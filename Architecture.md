# Architecture
This guide contains an overview of the architecture for the application.

## Overview
HyTOP is a fairly standard full-stack web application. It's split up into two main parts: the **frontend** and the **backend**. This is kind of like at a restaurant, with the front of house and back of house.

The **frontend** is everything the people see. The **backend** is everything that happens behind the scenes. The frontend has the user interface, and the backend has the database. They communicate through HTTP.

## Shared
Some pieces of the application are shared by both the frontend and the backend. This is especially important when the frontend and backend need to use the same types variables and objects.

### Types
The **shared/types.ts** file contains the types for the data within the application. Actually, it only has [`interface`](https://www.typescriptlang.org/docs/handbook/2/objects.html) declarations, but these are used to ensure the data is in the proper form everywhere.

These pieces of code define the shape of the data for the application. Each project that is created has all of the things in each of the interfaces.

## Frontend
The frontend of the application is built using [React](https://react.dev/) and [React Redux](https://react-redux.js.org/).

### Starting Point
The actual starting point is the **frontend/index.html** file - however, that file does not do much beyond including the **frontend/src/main.tsx** file:

```html
<script type="module" src="/src/main.tsx"></script>
```

The **main.tsx** file is the main entry point into the actual React application. This file does not do anything too interesting - it mainly contains the router for different pages in the app. The main thing it does is point the root (`"/"`) to the **App.tsx** file. The most important thing is the `ReactDOM.createRoot` - that renders the React application into the HTML.

So, from there, there is one big thing: the `<App>` component (from the **App.tsx** file).

### App
In the **App.tsx** file lives the `<App>` component. This is really the main HTML container for everything else in the app.

### Components
In React, a [component](https://react.dev/learn/describing-the-ui#your-first-component) is an isolated piece of UI. Components are a lot like HTML Elements - in fact, they are represented in the same manner, using angle brackets like `<ThisComponent></ThisComponent>`. There are some components in the **frontend/src/components/** folder - all of which are meant to represent one small part of the larger app.

For example, the `<FileSelectorComponent>` component is a little piece of UI to represent the left side of the screen where files are chosen. It lists out each file in the list, and calls a function when a new file is chosen. A component is just a function that returns some JSX (basically HTML with JS or TS inside).

Several components use the [`useEffect` hook](https://react.dev/reference/react/useEffect) - this allows the application to sync a component with an external system.

#### Folder Structure
There are several components and components _within_ components, so the folder structure is a little deep. Here is the full rundown of the **components** folder (as of June 1st, 2026):

- **📁 Interface**: _general standalone UI components_
  - **📄 Button.tsx** - a button element used across the application
  - **📄 Loader.tsx** - a loader element used across the application
  - **📄 Logo.tsx** - a logo element used across the application
- **📁 Main**: _top level screens / components_
  - **📄 AboutScreen.tsx** - [about page](https://hytop.onrender.com/about)
  - **📄 CopyProjectScreen.tsx** - fork link (e.g., [https://hytop.onrender.com/c/www](https://hytop.onrender.com/c/www) copes **www**)
  - **📄 CreateProjectScreen.tsx** - [create project page](https://hytop.onrender.com/create-project)
  - **📄 Header.tsx** - top bar on top of every page
  - **📄 HomeScreen.tsx** - [homepage](https://hytop.onrender.com/)
  - **📄 LatestUpdatesScreen.tsx** - [latest updates page](https://hytop.onrender.com/latest-updates)
  - **📄 PrivateRoute.tsx** - wrapper used to lock down some pages
- **📁 Project View**: _components for the [project viewer / editor](https://hytop.onrender.com/e/www)_
  - **📁 File Editor**: _components for the code editor itself_
    - **📄 FileEditorComponent.tsx** - a wrapper around a [`<MonacoEditor />` component](https://microsoft.github.io/monaco-editor/)
    - **📄 TabBar.tsx** - a component to display open tabs at the top of the editor
  - **📁 Interface**: _general UI for the project view_
    - **📄 ProjectViewContainer.tsx** - a wrapper around the whole project view
  - **📁 Preview**: _components for the preview pane on the right_
  -   **📄 PreviewComponent.tsx** - a single component for the preview pane
  - **📁 SideBar**: _components for the sidebar pane on the left_
    - **📁 FileSelector**: _components for the file list / explorer selector_
      - **📄 FileName.tsx** - a component for one single File listed in the selector
      - **📄 FileSelectorComponent.tsx** - the actual component for the whole file selector
      - **📄 FilesHeader.tsx** - a component for the top of the file selector
    - **📁 Interface**: _general UI for the sidebar_
      - **📄 SideBarButton.tsx** - a generalized button with a tooltip for choosing from the sidebar
      - **📄 SideBarMenu.tsx** - the combination of sidebar buttons to open their proper views
      - **📄 SideBarPane.tsx** - the display for whichever view is currently shown in the sidebar
    - **📁 ProjectSettings**: _components for the settings view (project name + description)_
      - **📄 ProjectSettingsComponent.tsx** - a single component for the project settings view of the sidebar
    - **📄 SideBarComponent.tsx** - the component that contains all the sidebar stuff
  - **📄 constants.tsx** - values set to be referenced elsewhere
  - **📄 ProjectViewScreen.tsx** - the primary component for the whole Project View
  - **📄 util.ts** - helper functions for the project viewer
- **📁 User**: _components related to users / accounts / authentication_
  - **📁 Preferences**: _components for the preferences view (font size, etc)_
    - **📄 DarkModeToggle.tsx** - a little component for turning on/off dark mode
    - **📄 PreferencesPane.tsx** - a view for setting user preferences (currently shown in SideBar)
  - **📄 AdminPanel.tsx** - special view for admins to do admin things
  - **📄 LoginScreen.tsx** - [sign in page](https://hytop.onrender.com/login)
  - **📄 ProfileScreen.tsx** - [where users view their profile](https://hytop.onrender.com/profile)
  - **📄 ProjectList.tsx** - helper component for viewing a list of projects
  - **📄 RegisterScreen.tsx** - [register page](https://hytop.onrender.com/register)

### Slices
Slices are really weird. For the purposes of this application, they are mainly used for:

- Frontend requests to the backend
- Frontend storage for data to be accessible across multiple components

For requests to the backend, an example would be: if someone using the app wants to pull up a certain project, the frontend has to call up the backend and say "this person wants to see this project." The backend will check the database and send back the proper information.

```ts
/* query defined as an endpoint in a slice */
getProject: builder.query({
  query: (projectName) => {
    return {
      url: `${PROJECTS_URL}/get/${projectName}`,
      method: "GET",
    };
  },
  providesTags: ["Project"]
}),
```

```ts
/* use within a component */
const projectData = useGetProjectQuery(projectName);
```

For storage, an example would be: the `<FileSelectorComponent />` component needs to know which tab is currently active, so it does this:

```ts
const { activeTab } = useSelector((state: RootState) => state.editor);
```

## Backend
The primary purpose of the backend is to work with the data from the MongoDB database. The **server.ts** file create the backend web server, and puts everything all together.

### config/db.ts
This file connects to the MongoDB database.

### controllers/*
This folder contains files that control each type of data. There are functions defined for each type of request the frontend might make. For example, the `findProject` function will check the database to see if a project exists, and return the content.

### middleware/*
This folder contains stuff that goes in between the frontend request and the backend logic.

### models/*
This folder contains each type of data object. It tells the database how to store these different types of objects. For example, each project has a name - this is in the **projectModel.ts** file, with the `projectSchema` object, and the `projectName` property.

### routes/*
This folder contains mappings for requests. Basically, it tells the backend where to route messages from the frontend. For example, if the frontend says "I want to `create/` a project," the **projectRoutes.ts** file ensures that the `createProject` function will be called.

### starters/*
This folder contains some actual starter projects, using HTML, CSS, and JavaScript. The application is able to access this code, and send it for certain projects.
