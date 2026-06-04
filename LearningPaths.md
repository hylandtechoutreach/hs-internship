# Learning Paths
Regardless of your current experience level, you will be able to build the skills you need to contribute successfully to this project. This page contains some helpful resources you can use to build your own learning path.

Note that it is not necessary to have a full grasp of all of these concepts to start developing. In fact, even the architect of this project (aka the person writing this, aka Joseph) is nowhere near an expert on any of this! It's more about building a product and learning as you go.

#### Learning Checklist
Check off these items as you complete them, or if you already have sufficient knowledge:

<ul style="list-style-type: none">
  <input type="checkbox" id="html"> <a href="https://www.w3schools.com/html/">HTML Tutorial</a><br>
  <input type="checkbox" id="css"> <a href="https://www.w3schools.com/css/">CSS Tutorial</a><br>
  <input type="checkbox" id="js-1"> <a href="https://www.w3schools.com/js/">JavaScript Tutorial (Simpler)</a><br>
  <input type="checkbox" id="js"> <a href="https://javascript.info/">JavaScript Tutorial</a><br>
  <input type="checkbox" id="ts"> <a href="https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html">TypeScript Introduction</a><br>
  <input type="checkbox" id="ts-hb"> <a href="https://www.typescriptlang.org/docs/handbook/intro.html">TypeScript Handbook</a><br>
  <input type="checkbox" id="csa"> <a href="https://en.wikipedia.org/wiki/Client%E2%80%93server_model">Client-Server Architecture</a><br>
  <input type="checkbox" id="term"> <a href="http://www.mprat.org/Terminus/">Terminal</a><br>
  <input type="checkbox" id="exp"> <a href="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs">Express with Node.js</a><br>
  <input type="checkbox" id="mdb"> <a href="https://www.mongodb.com/docs/manual/introduction/">MongoDB</a><br>
  <input type="checkbox" id="mgs"> <a href="https://www.mongodb.com/developer/languages/javascript/getting-started-with-mongodb-and-mongoose/">Mongoose</a><br>
  <input type="checkbox" id="rqs"> <a href="https://react.dev/learn">React: Quick Start</a><br>
  <input type="checkbox" id="rttt"> <a href="https://react.dev/learn/tutorial-tic-tac-toe">React: Tic-Tac-Toe</a><br>
  <input type="checkbox" id="rfull"> <a href="https://react.dev/learn/describing-the-ui">React: Full Introduction</a><br>
  <input type="checkbox" id="lgb"> <a href="https://learngitbranching.js.org/">Learn Git Branching</a><br>
</ul>

<script>
  document.querySelectorAll("input").forEach(inputElement => {
    const elementId = `${inputElement.id}`;

    inputElement.checked = localStorage.getItem(elementId) === 'checked';
    inputElement.onchange = e => {
      if (e.target.checked) {
        localStorage.setItem(elementId, 'checked');
      } else {
          localStorage.setItem(elementId, 'not-checked');
      }
    };
  });
</script>

More information about these resources is available below.

## HTML, CSS, and JavaScript
To get started with HTML, CSS, and JavaScript, we recommend these tutorials. They are a little simpler than the more advanced ones, and should be a good starting point.

- [HTML](https://www.w3schools.com/html/)
- [CSS](https://www.w3schools.com/css/)
- [JavaScript](https://www.w3schools.com/js/)

## JavaScript & TypeScript
The most important building block for this entire project is JavaScript. The project is written in TypeScript, but most of it looks like JavaScript.

- Fill in any knowledge gaps with the [`javascript.info` JavaScript Tutorial](https://javascript.info/)
- Learn a bit about TypeScript with [this quick guide](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)
- Dig deeper into TypeScript with [this handbook](https://www.typescriptlang.org/docs/handbook/intro.html)

If you are comfortable with JavaScript, you should be good to go. You can use TypeScript to your advantage, but it is not necessary for all development; simply writing JavaScript code in **.ts** files should almost always be fine.

## Client-Server Architecture
It will be helpful to recognize the basic parts of a full-stack web application:

- **backend**: the server - what happens behind the scenes (Node.js for this project)
- **frontend**: the client - what the user sees (React for this project)
- **database**: the storage location for all information (MongoDB for this project)
- **communication layer**: how the client and server communicate (HTTP for this project)

[Click here for the Wikipedia article that covers this topic.](https://en.wikipedia.org/wiki/Client%E2%80%93server_model)

## Terminal / Command Line
Using the command line is a valuable skill for software development, and can greatly enhance the development process.

[Click here to practice using the terminal by playing this text-based game.](http://www.mprat.org/Terminus/)

## Backend Server: Node.js and Express
If you've only used JavaScript to run code in a browser, it might be a little weird to see it run in a terminal. [This MDN tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs) walks through the concepts behind the Express framework in great detail. Note that some prerequisite knowledge is required, linked here:

- [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Server-side website programming](https://developer.mozilla.org/en-US/docs/Learn/Server-side)
  - [First Steps](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps)
  - [Client-Server Overview](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview)

After ensuring you have the fundamental knowledge, you're ready to get into Express.

## Backend Database: MongoDB and Mongoose
The most crucial feature of the application's backend server is its ability to connect to the database. Specifically, interfacing with the MongoDB database using Mongoose. [Part of the Express tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/mongoose) covers this topic. Additionally, there are some good learning resources available from MongoDB:

- [Introduction to MongoDB](https://www.mongodb.com/docs/manual/introduction/)
- [Getting Started with MongoDB and Mongoose](https://www.mongodb.com/developer/languages/javascript/getting-started-with-mongodb-and-mongoose/)

## Frontend Component Framework: React
React is an incredibly powerful component-based framework for the web. Here are some helpful ways to learn React, with varying commitment levels:

- [Quick Start](https://react.dev/learn)
- [Tic-Tac-Toe Tu-To-Rial](https://react.dev/learn/tutorial-tic-tac-toe)
- [React Mindset](https://react.dev/learn/thinking-in-react)
- [Full Guide](https://react.dev/learn/describing-the-ui)
- [Refs in React](https://react.dev/learn/manipulating-the-dom-with-refs)
- [`forwardRef` in React](https://www.youtube.com/watch?v=-vw6uG1JSEA)

### React Redux
The application also uses React Redux to store state. It can be helpful to learn a bit about this topic as well.

- [Redux Overview](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)
- [Quick Start with React/TypeScript](https://react-redux.js.org/tutorials/typescript-quick-start)

## Version Control with Git
Though not directly related to coding, version control is a huge part of software development. Learn a bit about Git and GitHub before diving into using them. This project will use [trunk-based development](https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development), which means team members will create small feature branches when they develop, and then merge them into the **main** branch as often as possible.

- [Workshop Lesson](https://hylandtechclub.com/capstone/GitHubLesson/StudentDesc.html)
- [Learn Git Branching](https://learngitbranching.js.org/)
