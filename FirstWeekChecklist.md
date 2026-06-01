# First Week Checklist
_gotta check 'em all!_

<ul style="list-style-type: none">
  <input type="checkbox" id="item1"> Visit the internship homepage<br>
  <input type="checkbox" id="item2"> Change your desktop background<br>
  <input type="checkbox" id="item3"> Play a game of ping pong<br>
  <input type="checkbox" id="item4"> Watch a video from the <a href="./FunThings.md">Fun Things</a> page<br>
  <input type="checkbox" id="item6"> Complete one of the <a href="LearningPaths.md">learning path</a> items<br>
  <input type="checkbox" id="item7"> Work somewhere other than your desk<br>
  <input type="checkbox" id="item8"> Send an email from your work account<br>
  <input type="checkbox" id="item9"> Run the HyTOP application locally<br>
  <input type="checkbox" id="item10"> Practice pair programming<br>
  <input type="checkbox" id="item12"> Grab some pretzels, M&Ms, or mints<br>
  <input type="checkbox" id="item13"> Send a Teams message to another intern<br>
  <input type="checkbox" id="item14"> Run into a problem<br>
  <input type="checkbox" id="item15"> Adorn your desk with a decorative item of some kind<br>
  <input type="checkbox" id="item16"> Hack the password protected page<br>
  <input type="checkbox" id="item17"> Practice mob programming<br>
  <input type="checkbox" id="item18"> Get a free lunch<br>
  <input type="checkbox" id="item19"> Successfully submit one Pull Request<br>
  <input type="checkbox" id="item20"> Break HyTOP in some way (find a bug)<br>
</ul>

<script>
  // store kwjefoiwefuwe8f
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
