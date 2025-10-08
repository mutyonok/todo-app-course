**TODO LIST PROJECT - 7 DAY INTENSIVE**
*(4 hours/day, ~28 hours total)*

---

**PRE-START CHECKLIST**

✓ Code editor installed? (VS Code recommended)
→ Ask Claude: "How to install VS Code on [your OS]"
✓ Understand HTML/CSS/JS roles?
→ If fuzzy, ask Claude: "Explain the role of HTML, CSS, and JavaScript"
✓ Can you open DevTools? (F12 or Cmd+Option+I on Mac)

---

## **DAY 1: Setup & Basic Structure**

🎯 **GOAL:** Get your development environment working and create the visual structure of your app. By end of day, you'll have a styled page deployed online.

📖 **KEY CONCEPT: The Development Workflow**

Professional developers don't just write code on their computer. They use tools to:
- **Version control (Git):** Save snapshots of your code so you can go back if something breaks
- **Remote backup (GitHub):** Store code online so it's safe and shareable
- **Deployment (GitHub Pages):** Make your project visible to the world

Think of it like writing a book: Git is saving drafts, GitHub is storing them in the cloud, GitHub Pages is publishing the book for others to read.

This might feel like a lot of setup, but you only do it once. Every project after this will be faster.

---

**Hour 1: Git & GitHub Setup**

💡 **WHAT WE'RE ACHIEVING:**
Setting up the tools that every professional web developer uses. Git tracks your changes, GitHub stores your code online.

**Tasks:**
- Install Git → Ask Claude: "Step-by-step guide to install Git on [your OS]"
- Create GitHub account at github.com
- Configure Git with your name and email (Claude will give you exact commands)
- **Success check:** Run `git --version` in terminal and see a version number

➜ **Understanding check:** "What's the difference between Git (on your computer) and GitHub (website)?"

---

**Hour 2: First Repository & Deployment**

💡 **WHAT WE'RE ACHIEVING:**
Creating your project folder and putting it online so others can see it. This is how you'll share your portfolio project.

**Tasks:**
- Create folder called `todo-app` on your computer
- Inside it, create three empty files: `index.html`, `styles.css`, `script.js`
- Ask Claude: "Complete beginner guide to creating a GitHub repository and pushing code"
- Follow the steps: `git init`, `git add .`, `git commit -m "initial commit"`, push to GitHub
- Ask Claude: "How to deploy a GitHub repository to GitHub Pages step-by-step"
- Wait 2-3 minutes after enabling GitHub Pages
- **Success check:** Visit yourusername.github.io/todo-app and see a blank page (this is correct!)

➜ **Understanding check:** "What does `git commit` do versus `git push`? Explain in your own words."

---

**Hour 3: HTML Structure**

💡 **WHAT WE'RE ACHIEVING:**
Building the skeleton of your app - the input field, button, and list that will hold tasks. HTML defines *what* elements exist, not how they look or behave yet.

**Tasks:**
- Open `index.html` in VS Code
- Ask Claude: "HTML5 boilerplate template" and paste it in
- Inside `<body>`, add:
    - `<h1>My Todo List</h1>`
    - `<input type="text" id="taskInput" placeholder="Enter a task...">`
    - `<button id="addBtn">Add Task</button>`
    - `<ul id="taskList"></ul>` (this is where tasks will appear)
- In the `<head>`, link your CSS: `<link rel="stylesheet" href="styles.css">`
- Before closing `</body>`, link your JS: `<script src="script.js"></script>`
- In `script.js`, write just one line: `console.log("JavaScript is connected!");`
- Open `index.html` in browser, press F12 to open DevTools, check Console tab
- **Success check:** See your HTML elements on the page and "JavaScript is connected!" in console

➜ **Understanding check:** "Why do we put the `<script>` tag at the bottom of `<body>` instead of in `<head>`?"

---

**Hour 4: Basic Styling**

💡 **WHAT WE'RE ACHIEVING:**
Making your app look clean and professional. Right now it probably looks like a website from 1995. CSS transforms that into something modern.

**Tasks:**
- In `styles.css`, ask Claude: "CSS to center a div and style a todo app form nicely"
- Apply the styles (you'll get: centered container, styled input/button, better spacing)
- Choose a color scheme (or ask Claude: "suggest a modern color scheme for todo app")
- Add: padding to elements, border-radius for rounded corners, nice font (like `font-family: 'Segoe UI', sans-serif;`)
- In terminal: `git add .`, `git commit -m "Add HTML and CSS"`, `git push`
- Wait a minute, refresh your GitHub Pages URL
- **Success check:** Your page looks clean and centered, visible online

🎯 **What you're learning:** Development workflow, version control, HTML structure, CSS styling

🎉 **MILESTONE - End of Day 1:**
You now have a deployed web page that you can share with anyone in the world! You know how to use Git, GitHub, and GitHub Pages - tools you'll use in every future project.

---

## **DAY 2: Making It Interactive**

🎯 **GOAL:** Transform your static page into an interactive app. By end of day, users can add tasks, delete them, and mark them complete.

📖 **KEY CONCEPT: The DOM (Document Object Model)**

Your HTML creates elements (button, input, etc.), but they just sit there doing nothing. JavaScript brings them to life.

The DOM is how JavaScript "sees" your HTML. Think of your HTML as a real-world object:
- `document.getElementById('addBtn')` = "Find me the button with id='addBtn'"
- `addEventListener('click', ...)` = "When someone clicks this button, do something"
- `createElement('li')` = "Create a new list item"

You're essentially giving JavaScript a remote control for your webpage.

**The pattern you'll use constantly:**
1. Select an element (getElementById)
2. Listen for an event (addEventListener)
3. Do something when event happens (run a function)

This is the foundation of ALL web interactivity.

---

**Hour 1: Selecting Elements & First Event**

💡 **WHAT WE'RE ACHIEVING:**
Teaching JavaScript how to find and interact with your HTML elements. You'll make the button respond when clicked.

**Tasks:**
- In `script.js`, remove the console.log from yesterday
- Select your elements and store them in variables:
  ```javascript
  const addBtn = document.getElementById('addBtn');
  const taskInput = document.getElementById('taskInput');
  const taskList = document.getElementById('taskList');
  ```
- Add: `console.log(addBtn, taskInput, taskList);` to verify they're found
- Add an event listener to the button:
  ```javascript
  addBtn.addEventListener('click', function() {
      console.log('Button was clicked!');
  });
  ```
- Test in browser: click button, check console
- Now log the input value: `console.log(taskInput.value);`
- **Success check:** When you type something and click the button, console shows what you typed

➜ **Understanding check:** "What does `getElementById()` return if the ID doesn't exist? Try it: `document.getElementById('fakeID')` in console."

🎯 **What you're learning:** DOM selection, event listeners, getting user input

---

**Hour 2: Creating Elements Dynamically**

💡 **WHAT WE'RE ACHIEVING:**
When users type a task and click "Add", we need to create a new `<li>` element and add it to the list. This is "dynamic" because we're creating HTML with JavaScript, not writing it by hand.

THE PROCESS:
1. Get what the user typed
2. Create a new `<li>` element
3. Put the text inside the `<li>`
4. Add the `<li>` to the `<ul>` on the page
5. Clear the input so they can type another task

**Tasks:**
- Inside your click event listener, get the input value: `const taskText = taskInput.value;`
- Add a check: only proceed if `taskText.trim() !== ''` (trim removes spaces)
- Create a new list item: `const li = document.createElement('li');`
- Set its text: `li.textContent = taskText;`
- Add it to the list: `taskList.appendChild(li);`
- Clear the input: `taskInput.value = '';`
- **Success check:** Type a task, click Add, see it appear in the list!

If stuck, ask Claude: "How to create an li element and append it to a ul in JavaScript"

➜ **Understanding check:** "What's the difference between `textContent` and `innerHTML`? Which is safer and why?"

🎯 **What you're learning:** Creating elements, DOM manipulation, input validation

---

**Hour 3: Delete Functionality**

💡 **WHAT WE'RE ACHIEVING:**
Each task needs a delete button. When clicked, that specific task should disappear.

THE CHALLENGE: You're creating tasks dynamically, so you can't just add an event listener to a specific delete button in advance. You need to create the delete button when you create the task.

**Tasks:**
- When creating the `<li>`, also create a delete button:
  ```javascript
  const deleteBtn = document.createElement('button');
  deleteBtn.textContent = '×'; // or 'Delete'
  deleteBtn.className = 'delete-btn';
  ```
- Append the delete button to the `<li>`: `li.appendChild(deleteBtn);`
- Add an event listener to the delete button:
  ```javascript
  deleteBtn.addEventListener('click', function() {
      li.remove(); // removes the entire li from the page
  });
  ```
- In `styles.css`, style `.delete-btn` (make it red, float it to the right, etc.)
- **Success check:** Each task has a delete button that removes only that task

If stuck, ask Claude: "How to remove a parent element when a button inside it is clicked"

➜ **Understanding check:** "Why do we add the event listener to `deleteBtn` instead of to a button with an ID?"

🎯 **What you're learning:** Event listeners on dynamic elements, removing elements from DOM

---

**Hour 4: Mark Complete**

💡 **WHAT WE'RE ACHIEVING:**
When users click a task, it should toggle between complete (crossed out) and incomplete. We do this by adding/removing a CSS class.

THE APPROACH:
- Add a click event to the `<li>` itself
- When clicked, toggle a CSS class called `completed`
- CSS will handle the visual change (line-through text)

**Tasks:**
- When creating the `<li>`, add an event listener to it:
  ```javascript
  li.addEventListener('click', function() {
      li.classList.toggle('completed');
  });
  ```
- In `styles.css`, add:
  ```css
  .completed {
      text-decoration: line-through;
      opacity: 0.6;
      color: #888;
  }
  ```
- **Success check:** Clicking a task crosses it out, clicking again uncrosses it

If stuck, ask Claude: "How to toggle a CSS class on click in JavaScript"

➜ **Understanding check:** "What does `classList.toggle()` do? What if you click the same element twice?"

🎯 **What you're learning:** CSS classes manipulation, toggle functionality, visual feedback

🎉 **MILESTONE - End of Day 2:**
You have a fully functional todo app! Users can add, delete, and complete tasks. This is real web development - you're manipulating the DOM based on user actions. The problem? If you refresh the page, everything disappears. That's what we fix tomorrow.

---

## **DAY 3: Data Persistence**

🎯 **GOAL:** Make your tasks survive page reloads. Learn how web apps remember information using localStorage.

📖 **KEY CONCEPT: localStorage - Your App's Memory**

Right now, your tasks only exist in the DOM (the visible webpage). When you refresh, the DOM is rebuilt from scratch, and your tasks are gone.

**The solution:** Store your tasks in the browser's localStorage - a simple database built into every browser.

Think of it like this:
- **Without localStorage:** Writing on a whiteboard. When you leave the room (refresh), someone erases it.
- **With localStorage:** Writing in a notebook that stays on the desk. When you come back, you read from the notebook and rewrite it on the whiteboard.

**Important concept:** localStorage can only store text (strings), not JavaScript objects or arrays directly. So we convert:
- JavaScript array → JSON string (using `JSON.stringify`) → Save to localStorage
- localStorage → JSON string → JavaScript array (using `JSON.parse`)

**The new workflow:**
1. Keep tasks in an array (the "source of truth")
2. When anything changes, save the array to localStorage
3. When the page loads, read from localStorage and display the tasks

This is the foundation of how real apps work. React, Vue, Angular - they all follow this pattern of "keep data separate from display."

---

**Hour 1: Understanding localStorage**

💡 **WHAT WE'RE ACHIEVING:**
Before diving into code, you need to understand how localStorage works. It's actually very simple - just key-value pairs, like a dictionary.

**Tasks:**
- Ask Claude: "Explain localStorage with simple examples"
- Open your app in browser, open Console (F12)
- Experiment directly in console:
  ```javascript
  localStorage.setItem('name', 'Alex');
  localStorage.getItem('name'); // returns 'Alex'
  localStorage.removeItem('name');
  ```
- Try storing an array (it won't work correctly):
  ```javascript
  localStorage.setItem('numbers', [1,2,3]);
  localStorage.getItem('numbers'); // returns "1,2,3" as string - broken!
  ```
- Now with JSON:
  ```javascript
  localStorage.setItem('numbers', JSON.stringify([1,2,3]));
  JSON.parse(localStorage.getItem('numbers')); // returns [1,2,3] - works!
  ```
- In DevTools, go to Application tab → Local Storage → see your saved data
- **Success check:** You understand localStorage basics and why we need JSON

➜ **Understanding check:** "Why can't we store arrays directly in localStorage? What does JSON.stringify do?"

---

**Hour 2: Restructure - Store Tasks in Array**

💡 **WHAT WE'RE ACHIEVING:**
Right now your tasks only exist as `<li>` elements in the DOM. We need to keep them in a JavaScript array instead. This array will be our "source of truth" - the place where we really know what tasks exist.

**The mindset shift:**
- OLD WAY: Create `<li>` directly when button clicked
- NEW WAY: Add task to array → save array → display all tasks from array

**Tasks:**
- At the top of your script, create an empty array: `let tasks = [];`
- Rewrite your add button logic:
  ```javascript
  addBtn.addEventListener('click', function() {
      const taskText = taskInput.value.trim();
      if (taskText === '') return;
      
      // Create task object
      const task = {
          id: Date.now(), // unique ID (timestamp)
          text: taskText,
          completed: false
      };
      
      // Add to array
      tasks.push(task);
      
      // Log to verify
      console.log(tasks);
      
      // Clear input
      taskInput.value = '';
  });
  ```
- **Success check:** Click add a few times, check console - see your tasks array growing

➜ **Understanding check:** "Why do we use `Date.now()` for the ID? What does it return?"

🎯 **What you're learning:** Data models, separating data from display

---

**Hour 3: Save to localStorage & Render Function**

💡 **WHAT WE'RE ACHIEVING:**
Now we save the tasks array to localStorage whenever it changes, and create a function that displays tasks from the array (instead of creating `<li>` elements directly).

**THE SEPARATION OF CONCERNS:**
- `tasks` array = DATA (what tasks exist)
- `renderTasks()` function = VIEW (displaying the data)
- Rule: Always update data first, then call renderTasks()

This pattern is fundamental to all modern frameworks (React, Vue, etc.).

**Tasks:**
- Create a save function:
  ```javascript
  function saveTasks() {
      localStorage.setItem('tasks', JSON.stringify(tasks));
  }
  ```
- Create a render function (this replaces your direct DOM manipulation):
  ```javascript
  function renderTasks() {
      // Clear the list
      taskList.innerHTML = '';
      
      // Loop through tasks array and create li for each
      tasks.forEach(task => {
          const li = document.createElement('li');
          li.textContent = task.text;
          
          // Add completed class if task is completed
          if (task.completed) {
              li.classList.add('completed');
          }
          
          // Create delete button
          const deleteBtn = document.createElement('button');
          deleteBtn.textContent = '×';
          deleteBtn.className = 'delete-btn';
          li.appendChild(deleteBtn);
          
          // Delete functionality (we'll update this next)
          deleteBtn.addEventListener('click', function() {
              // Remove from array by filtering out this task
              tasks = tasks.filter(t => t.id !== task.id);
              saveTasks();
              renderTasks();
          });
          
          // Toggle complete (we'll update this next)
          li.addEventListener('click', function(e) {
              // Don't toggle if clicking delete button
              if (e.target === deleteBtn) return;
              
              task.completed = !task.completed;
              saveTasks();
              renderTasks();
          });
          
          taskList.appendChild(li);
      });
  }
  ```
- Update your add button to use the new pattern:
  ```javascript
  addBtn.addEventListener('click', function() {
      const taskText = taskInput.value.trim();
      if (taskText === '') return;
      
      const task = {
          id: Date.now(),
          text: taskText,
          completed: false
      };
      
      tasks.push(task);
      saveTasks(); // Save to localStorage
      renderTasks(); // Display updated list
      taskInput.value = '';
  });
  ```
- **Success check:** Add tasks - they appear. Delete - they disappear. Toggle complete - they cross out. Check Application → localStorage - see your data!

If stuck, ask Claude: "Explain the renderTasks pattern in a todo app"

➜ **Understanding check:** "Why do we call `renderTasks()` after every change? Why not just update the one `<li>` that changed?"

🎯 **What you're learning:** Separation of data and view, the render pattern, array methods (forEach, filter)

---

**Hour 4: Load Tasks on Page Load**

💡 **WHAT WE'RE ACHIEVING:**
The final piece: when the page loads, check if there are saved tasks in localStorage. If yes, load them into the tasks array and display them.

**Tasks:**
- At the top of your script (after declaring `let tasks = [];`), add:
  ```javascript
  function loadTasks() {
      const savedTasks = localStorage.getItem('tasks');
      if (savedTasks) {
          tasks = JSON.parse(savedTasks);
          renderTasks();
      }
  }
  
  // Load tasks when page loads
  loadTasks();
  ```
- **Success check:** Add tasks, refresh page - they're still there! 🎉

➜ **Understanding check:** "What happens if `localStorage.getItem('tasks')` returns null (no saved data)? Why don't we call `JSON.parse(null)`?"

🎯 **What you're learning:** Page lifecycle, loading data, handling null values

🎉 **MILESTONE - End of Day 3:**
Your app now has persistent data! This is a huge leap - you understand how web apps actually store and retrieve information. The pattern you learned today (data array → save → render) is used in every modern web application.

**TROUBLESHOOTING (if stuck Day 3):**
- Tasks don't persist? Check: Did you call `saveTasks()` after adding/deleting/toggling?
- Tasks duplicate on reload? Check: Is `renderTasks()` clearing the list first with `taskList.innerHTML = ''`?
- "Cannot read property"? Check: Is localStorage returning null? Use `if (savedTasks)` before parsing
- Confused? Ask Claude: "Explain the flow: user clicks add → what happens step by step in my code?"

---

## **DAY 4: Code Quality & Review**

🎯 **GOAL:** Understand what you've built, clean up your code, and make it professional. Today is about solidifying your knowledge, not adding features.

📖 **KEY CONCEPT: Clean Code & Software Engineering Principles**

You have a working app, but right now your code might be a bit messy. Professional developers don't just make things work - they make code readable, maintainable, and organized.

**Why this matters:**
- In 2 weeks, you'll forget why you wrote something a certain way
- Other developers (or employers) need to read your code
- Messy code breeds bugs

**The principles you'll apply:**
1. **Separation of Concerns:** Data logic separate from display logic
2. **DRY (Don't Repeat Yourself):** Use functions to avoid copying code
3. **Clear naming:** Variable/function names that explain what they do
4. **Comments:** Explain WHY, not WHAT (code shows what, comments show why)

This is what separates someone who can code from a software engineer.

---

**Hour 1: Code Review & Refactoring**

💡 **WHAT WE'RE ACHIEVING:**
Reading through all your code with fresh eyes, understanding every line, and reorganizing for clarity.

**Tasks:**
- Close your project completely
- Open it fresh and read through all your JavaScript
- For each function, ask yourself: "What does this do? Why?"
- Check if you have any repeated code - can it become a function?
- Ensure you have these clean, separate functions:
    - `loadTasks()` - loads from localStorage on page start
    - `saveTasks()` - saves tasks array to localStorage
    - `renderTasks()` - displays all tasks from array
    - `addTask()` - adds new task to array (optional: make this a separate function)
- Look at your event listeners - are they inside renderTasks (bad) or set up once (good)?
- **Success check:** Code is organized into clear functions, each does one thing

Ask Claude: "Review my todo app code structure - any improvements?" (paste your code)

➜ **Understanding check:** "Explain in your own words why we separate `saveTasks()` and `renderTasks()` instead of doing everything in one function."

🎯 **What you're learning:** Code organization, refactoring, software design patterns

---

**Hour 2: Active Learning - Rebuild From Memory**

💡 **WHAT WE'RE ACHIEVING:**
Testing if you truly understand what you built. This is where real learning happens.

**Tasks:**
- Close all your code files
- Open a blank piece of paper (or empty text file)
- Without looking at your code, write in plain English:
    1. What happens when the page loads?
    2. What happens when user clicks "Add"?
    3. What happens when user clicks "Delete"?
    4. What happens when user clicks a task to complete it?
    5. Draw the flow: User action → Array changes → localStorage → Display updates
- Now try to write the key parts from memory:
    - How do you save to localStorage?
    - How do you load from localStorage?
    - How do you remove an item from an array?
- Open your code and compare - what did you forget? That's what you need to review
- **Success check:** You can explain the entire flow without looking at code

**No Claude here - this is self-assessment**

➜ **Understanding check:** "Which part was hardest to remember? That's your weak point - review it."

🎯 **What you're learning:** Metacognition, identifying knowledge gaps

---

**Hour 3: Add Comments & Documentation**

💡 **WHAT WE'RE ACHIEVING:**
Making your code readable for others (and future you). Good comments explain WHY you made decisions, not what the code does.

**BAD COMMENT:**
```javascript
// Loop through tasks
tasks.forEach(task => {
```

**GOOD COMMENT:**
```javascript
// Rebuild the entire task list from our tasks array (source of truth)
tasks.forEach(task => {
```

**Tasks:**
- Add a comment block at the top of your JS file:
  ```javascript
  /*
   * Todo App
   * Allows users to add, complete, and delete tasks
   * Data persists in browser localStorage
   */
  ```
- Add comments explaining:
    - Why you use `Date.now()` for IDs
    - Why you call `renderTasks()` instead of updating individual elements
    - Any tricky parts (like `e.target === deleteBtn` check)
- Don't comment obvious things like `// Get the button`
- In HTML, add comments explaining sections:
  ```html
  <!-- Task input form -->
  <!-- Task list will be rendered here by JavaScript -->
  ```
- **Success check:** Someone with basic JS knowledge could read your code and understand it

Ask Claude: "Are my code comments helpful? Should I add/remove any?" (paste code)

➜ **Understanding check:** "What's the difference between commenting WHAT code does versus WHY you wrote it that way?"

🎯 **What you're learning:** Documentation, code readability

---

**Hour 4: Testing & Bug Fixing**

💡 **WHAT WE'RE ACHIEVING:**
Systematically testing your app like a user would, finding edge cases and bugs, fixing them.

**Tasks:**
- Test these scenarios:
    - Add a task with just spaces - should not add (do you trim?)
    - Add a very long task (200 characters) - does it break your layout?
    - Add task with special characters: `<script>alert('hi')</script>` - are you vulnerable? (use `textContent` not `innerHTML`)
    - Rapidly click "Add" 20 times - any issues?
    - Delete all tasks - does it still work?
    - Reload page multiple times - any weird behavior?
    - Open DevTools Application → localStorage → manually edit the data → reload - does it crash?
- For each bug found, fix it
- Add validation:
    - Max task length (e.g., 200 characters)
    - Sanitize input (you're already doing this if using `textContent`)
- **Success check:** App handles all edge cases gracefully, no crashes

If you find security concerns, ask Claude: "How do I prevent XSS vulnerabilities in a todo app?"

➜ **Understanding check:** "Why is `textContent` safer than `innerHTML`? What's the risk?"

🎯 **What you're learning:** Testing, edge cases, input validation, basic security

🎉 **MILESTONE - End of Day 4:**
Your code is now professional quality. You understand not just HOW it works, but WHY you built it this way. You've tested it thoroughly. This is the difference between a hobbyist and a professional developer.

**Review checkpoint:**
Open your DevTools console and explain out loud (or to someone else):
"When I click Add, first [X] happens, then [Y], then [Z]..."
If you can do this fluently, you're ready for Day 5.

---

## **DAY 5: Features & Enhancement**

🎯 **GOAL:** Add professional features that make your app more useful and impressive. These are the features that make employers say "this person can build real products."

📖 **KEY CONCEPT: State Management & Filtering**

Your app has been working with all tasks all the time. Now we add complexity: showing different "views" of the same data.

**The concept:**
- Your tasks array doesn't change (the data is the data)
- But what you DISPLAY changes based on filters
- This is called "state management" - showing different views of the same underlying data

**In React/Vue, this is core:**
- Same data, different views
- User switches between views with buttons
- App needs to "remember" which view is active (this is called "state")

You'll implement a simple version: All tasks / Active tasks / Completed tasks.

---

**Hour 1: Task Counter**

💡 **WHAT WE'RE ACHIEVING:**
Showing users helpful information: "You have 5 tasks, 3 remaining"

This teaches you to derive information from your data (counting/filtering).

**Tasks:**
- In your HTML, add after the input:
  ```html
  <p id="taskCounter"></p>
  ```
- Create a function:
  ```javascript
  function updateCounter() {
      const total = tasks.length;
      const remaining = tasks.filter(task => !task.completed).length;
      const counter = document.getElementById('taskCounter');
      counter.textContent = `${remaining} of ${total} tasks remaining`;
  }
  ```
- Call `updateCounter()` at the end of `renderTasks()`
- **Success check:** Counter shows accurate count, updates when you add/delete/complete tasks

➜ **Understanding check:** "What does `tasks.filter(task => !task.completed)` return? Try logging it."

🎯 **What you're learning:** Array filter method, derived state, template literals

---

**Hour 2: Filter Buttons (All / Active / Completed)**

💡 **WHAT WE'RE ACHIEVING:**
Letting users view only active tasks, only completed tasks, or all tasks. This is a common pattern in todo apps (see Todoist, Microsoft To Do, etc.).

**THE APPROACH:**
- Add three buttons: All, Active, Completed
- Track which filter is currently active (a global variable)
- In `renderTasks()`, only show tasks that match the current filter
- When user clicks a filter button, update the filter and re-render

**Tasks:**
- In HTML, add after your counter:
  ```html
  <div id="filters">
      <button class="filter-btn active" data-filter="all">All</button>
      <button class="filter-btn" data-filter="active">Active</button>
      <button class="filter-btn" data-filter="completed">Completed</button>
  </div>
  ```
- At top of JS, add: `let currentFilter = 'all';`
- Update `renderTasks()` to filter tasks:
  ```javascript
  function renderTasks() {
      taskList.innerHTML = '';
      
      // Filter tasks based on currentFilter
      let filteredTasks = tasks;
      if (currentFilter === 'active') {
          filteredTasks = tasks.filter(task => !task.completed);
      } else if (currentFilter === 'completed') {
          filteredTasks = tasks.filter(task => task.completed);
      }
      // If 'all', show everything (no filter needed)
      
      filteredTasks.forEach(task => {
          // ... rest of your render code
      });
      
      updateCounter();
  }
  ```
- Add event listeners to filter buttons:
  ```javascript
  document.querySelectorAll('.filter-btn').forEach(btn => {
      btn.addEventListener('click', function() {
          // Remove 'active' class from all buttons
          document.querySelectorAll('.filter-btn').forEach(b => 
              b.classList.remove('active')
          );
          // Add 'active' class to clicked button
          this.classList.add('active');
          
          // Update filter and re-render
          currentFilter = this.dataset.filter;
          renderTasks();
      });
  });
  ```
- In CSS, style the active filter button differently:
  ```css
  .filter-btn.active {
      background: #007bff;
      color: white;
  }
  ```
- **Success check:** Clicking filters shows correct tasks, active button is highlighted

If stuck, ask Claude: "How to implement filter buttons in a todo app"

➜ **Understanding check:** "Why don't we filter the tasks array itself? Why create a new filteredTasks variable?"

🎯 **What you're learning:** Filtering data, maintaining UI state, querySelectorAll, data attributes

---

**Hour 3: Clear Completed Button**

💡 **WHAT WE'RE ACHIEVING:**
One-click way to delete all completed tasks. This teaches bulk operations on data.

**Tasks:**
- Add button in HTML:
  ```html
  <button id="clearCompleted">Clear Completed</button>
  ```
- Add event listener:
  ```javascript
  document.getElementById('clearCompleted').addEventListener('click', function() {
      // Keep only tasks that are NOT completed
      tasks = tasks.filter(task => !task.completed);
      saveTasks();
      renderTasks();
  });
  ```
- Optional: Only show this button if there are completed tasks
- **Success check:** Clicking button removes all completed tasks

➜ **Understanding check:** "Explain what `tasks.filter(task => !task.completed)` does step by step."

🎯 **What you're learning:** Bulk operations, array filter, conditional UI

---

**Hour 4: Additional Feature (Choose One)**

💡 **WHAT WE'RE ACHIEVING:**
Pick ONE feature that interests you. This is your chance to explore and problem-solve independently.

**OPTION A: Edit Tasks (Recommended)**
- Double-click a task to edit it
- Input field appears with current text
- Press Enter to save, Escape to cancel
- Ask Claude: "How to implement edit functionality in todo app"

**OPTION B: Keyboard Shortcuts**
- Press Enter in input field to add task (not just clicking button)
- Press Escape to clear input
- Ask Claude: "How to detect Enter key press in JavaScript"

**OPTION C: Task Priority**
- Add priority levels (High/Medium/Low)
- Color-code tasks by priority
- Sort tasks by priority
- Ask Claude: "How to add priority system to todo app"

**OPTION D: Due Dates**
- Add date input when creating task
- Show due date next to task
- Highlight overdue tasks in red
- Ask Claude: "How to add due dates to todo app"

**Tasks:**
- Pick ONE feature from above
- Spend 30 minutes trying to implement it yourself
- If stuck after 30 minutes, ask Claude for guidance
- Implement the feature
- **Success check:** Your chosen feature works

➜ **Understanding check:** "What was the hardest part of implementing this feature? Why?"

🎯 **What you're learning:** Problem-solving, feature implementation, independent learning

🎉 **MILESTONE - End of Day 5:**
Your app now has professional features that make it actually useful. You've learned to filter data, manage UI state, and implement features independently. Employers look for this - not just following tutorials, but extending functionality on your own.

**TROUBLESHOOTING (if stuck Day 5):**
- Filters not working? Check: Is `currentFilter` variable being updated? Add `console.log(currentFilter)` before filtering
- Counter wrong? Check: Are you calling `updateCounter()` after every change?
- Can't figure out feature? Ask Claude with specific details: "I'm trying to [goal], here's my code [paste], I'm stuck because [specific problem]"

---

## **DAY 6: Design & Polish**

🎯 **GOAL:** Transform your functional app into a beautiful, professional portfolio piece. Make it look like a product people would want to use.

📖 **KEY CONCEPT: UI/UX Design Principles**

You've been focused on functionality. Now we focus on presentation. Good design isn't just about "looking pretty" - it's about:

**Usability:** Can users figure out how to use it instantly?
**Accessibility:** Can everyone use it, including people with disabilities?
**Responsiveness:** Does it work on all screen sizes?
**Polish:** Do interactions feel smooth and intentional?

**The principles you'll apply:**
1. **Visual hierarchy:** Important things stand out (size, color, position)
2. **Consistency:** Similar elements look similar
3. **Feedback:** Actions have visible responses (hover effects, transitions)
4. **Whitespace:** Empty space makes content breathable
5. **Color theory:** Colors create mood and guide attention

Think of the difference between a rough wooden chair (works, but uncomfortable) and a well-designed chair (works AND feels good). That's what we're doing today.

---

**Hour 1: Visual Design & Color Scheme**

💡 **WHAT WE'RE ACHIEVING:**
Making your app look modern and professional with better colors, typography, and spacing.

**Tasks:**
- Choose a color scheme. Options:
    - Ask Claude: "Suggest a modern color palette for a todo app with hex codes"
    - Use a tool: coolors.co or go to dribbble.com and search "todo app" for inspiration
- Apply your color scheme:
    - Background color (light, not pure white)
    - Primary color (for buttons, accents)
    - Text colors (dark gray, not pure black)
    - Success/danger colors (green for complete, red for delete)
- Improve typography:
  ```css
  body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      font-size: 16px;
      line-height: 1.6;
  }
  ```
- Add better spacing:
    - Increase padding in input/buttons
    - Add margin between elements
    - Make container width comfortable (600-800px)
- Add subtle shadows for depth:
  ```css
  .container {
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }
  ```
- Round corners on elements (border-radius: 8px)
- **Success check:** App looks modern, colors are cohesive, spacing feels comfortable

Ask Claude: "Review my CSS design choices" (paste your CSS)

➜ **Understanding check:** "Why use `rgba(0,0,0,0.1)` for shadows instead of a solid color?"

🎯 **What you're learning:** Color theory, typography, visual design, CSS box model

---

**Hour 2: Responsive Design (Mobile-First)**

💡 **WHAT WE'RE ACHIEVING:**
Making your app work beautifully on phones, tablets, and desktops. Over 60% of web traffic is mobile - this is essential.

**THE APPROACH:**
- Use flexible units (%, rem) instead of fixed pixels
- Test at different screen sizes
- Adjust layout for small screens

**Tasks:**
- In DevTools, click the device toolbar icon (or Ctrl+Shift+M)
- Test your app at: iPhone SE (375px), iPad (768px), Desktop (1200px)
- Make it responsive:
  ```css
  /* Base styles (mobile first) */
  .container {
      width: 90%;
      max-width: 600px;
      margin: 0 auto;
      padding: 20px;
  }
  
  input, button {
      font-size: 16px; /* Prevents zoom on mobile */
      padding: 12px;
  }
  
  /* Larger screens */
  @media (min-width: 768px) {
      .container {
          padding: 40px;
      }
  }
  ```
- Make buttons stack on small screens if needed
- Ensure touch targets are at least 44x44px (Apple guideline)
- Test tap interactions on mobile view
- **Success check:** App works smoothly on phone-sized screen (375px) and desktop

Ask Claude: "How to make my todo app responsive for mobile"

➜ **Understanding check:** "What does 'mobile-first' mean? Why start with mobile styles?"

🎯 **What you're learning:** Responsive design, media queries, mobile UX

---

**Hour 3: Animations & Micro-interactions**

💡 **WHAT WE'RE ACHIEVING:**
Adding subtle animations that make the app feel polished and alive. Micro-interactions provide feedback that makes the UI feel responsive.

**THE PRINCIPLE:**
Animations should be quick (200-300ms) and purposeful, not distracting. They guide attention and confirm actions.

**Tasks:**
- Add fade-in for new tasks:
  ```css
  li {
      animation: fadeIn 0.3s ease-in;
  }
  
  @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-10px); }
      to { opacity: 1; transform: translateY(0); }
  }
  ```
- Add hover effects:
  ```css
  button:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
      transition: all 0.2s ease;
  }
  
  li:hover {
      background: #f8f9fa;
      transition: background 0.2s ease;
  }
  ```
- Add active/click feedback:
  ```css
  button:active {
      transform: translateY(0);
  }
  ```
- Smooth transitions for completing tasks:
  ```css
  li {
      transition: all 0.3s ease;
  }
  
  li.completed {
      text-decoration: line-through;
      opacity: 0.6;
  }
  ```
- Optional: Add checkmark animation when completing
- **Success check:** Interactions feel smooth, nothing is jarring

Ask Claude: "Simple CSS animations for todo app that aren't distracting"

➜ **Understanding check:** "Why do we use `transition` for hover effects but `animation` for fade-in? What's the difference?"

🎯 **What you're learning:** CSS animations, transitions, micro-interactions, UX feedback

---

**Hour 4: Accessibility (A11y)**

💡 **WHAT WE'RE ACHIEVING:**
Making your app usable by everyone, including people using screen readers, keyboard navigation, or who have visual impairments.

**WHY THIS MATTERS:**
- 15% of the world has some form of disability
- Accessible apps are easier for everyone to use
- Shows professional attention to detail

**Tasks:**
- Add semantic HTML (you probably already have this, but verify):
    - `<main>` wrapper for content
    - `<h1>` for title
    - `<button>` for buttons (not styled divs)
- Add ARIA labels for screen readers:
  ```html
  <input 
      type="text" 
      id="taskInput"
      placeholder="Enter a task..."
      aria-label="New task input"
  >
  <button id="addBtn" aria-label="Add new task">Add Task</button>
  <ul id="taskList" role="list" aria-label="Task list"></ul>
  ```
- Make it keyboard navigable:
    - Press Tab - should highlight each interactive element
    - Press Enter in input field - should add task
  ```javascript
  taskInput.addEventListener('keypress', function(e) {
      if (e.key === 'Enter') {
          addBtn.click();
      }
  });
  ```
- Ensure color contrast is sufficient:
    - Use a contrast checker: webaim.org/resources/contrastchecker
    - Text should be at least 4.5:1 contrast ratio
- Add focus indicators (visible outline when tabbing):
  ```css
  button:focus, input:focus {
      outline: 2px solid #007bff;
      outline-offset: 2px;
  }
  ```
- Test: Navigate your entire app using ONLY keyboard (Tab, Enter, Space)
- **Success check:** Can complete all actions (add, delete, complete, filter) using only keyboard

Ask Claude: "Basic accessibility checklist for todo app"

➜ **Understanding check:** "What is a screen reader? Why do we need ARIA labels if we have placeholders?"

🎯 **What you're learning:** Web accessibility, ARIA, keyboard navigation, inclusive design

🎉 **MILESTONE - End of Day 6:**
Your app now looks and feels professional. It works on all devices, has smooth interactions, and is accessible to everyone. This is what separates a coding exercise from a portfolio-worthy project. When employers see attention to design and accessibility, they know you care about the full user experience, not just making things work.

**Visual comparison to appreciate:**
- Look at your app from Day 2 (screenshot if you have it)
- Look at it now
- The functionality is similar, but the experience is completely different

---

## **DAY 7: Portfolio Preparation & Documentation**

🎯 **GOAL:** Package your project professionally so it's ready to show employers, share on LinkedIn, and add to your portfolio. Today is about presentation, not coding.

📖 **KEY CONCEPT: Documentation as Part of the Product**

Code without documentation is like a product without instructions. Employers evaluate:
1. Does the code work? (you've done this)
2. Can I understand it? (documentation)
3. Can I see their thought process? (README, commits)

**What makes a portfolio project stand out:**
- Clear README that explains what it does
- Screenshots/GIF showing it in action
- Deployed live link (you already have this!)
- Clean git history showing progression
- Thoughtful description of what you learned

You're not just showing "I can code," you're showing "I can communicate about my code."

---

**Hour 1: Write Comprehensive README**

💡 **WHAT WE'RE ACHIEVING:**
Creating a README.md file that acts as your project's front page on GitHub. This is often the first thing employers look at.

**Tasks:**
- In your project folder, create `README.md`
- Ask Claude: "Template for a professional portfolio project README"
- Include these sections:

  **1. Project Title & Description**
  ```markdown
  # Todo App
  
  A clean, responsive todo application built with vanilla JavaScript. 
  Features local storage persistence, task filtering, and a modern UI.
  
  🔗 [Live Demo](https://yourusername.github.io/todo-app)
  ```

  **2. Features**
    - Bullet list of what it does
    - Be specific: "✅ Local storage persistence" not just "saves tasks"

  **3. Technologies Used**
    - HTML5
    - CSS3 (Flexbox, Grid, Animations, Media Queries)
    - Vanilla JavaScript (ES6+)
    - LocalStorage API

  **4. What I Learned**
  This is CRITICAL - shows growth:
  ```markdown
  ## Key Learnings
  
  - **DOM Manipulation**: Understanding how to create, modify, and remove 
    elements dynamically
  - **Data Persistence**: Implementing localStorage with JSON serialization
  - **Separation of Concerns**: Maintaining a data model separate from the 
    view layer (render pattern)
  - **Array Methods**: Using filter, forEach, and map for data transformations
  - **Responsive Design**: Mobile-first approach with media queries
  - **Accessibility**: ARIA labels and keyboard navigation
  ```

  **5. Future Improvements** (shows you think ahead):
    - Drag-and-drop reordering
    - Categories/tags for tasks
    - Backend integration for multi-device sync

  **6. Setup/Installation** (if someone wants to run it locally)

- Use proper markdown formatting (headers, lists, code blocks)
- Add your live link prominently at the top
- **Success check:** README is clear, informative, sells your project well

➜ **Understanding check:** "Why is 'What I Learned' more valuable to employers than just listing features?"

🎯 **What you're learning:** Technical writing, markdown, project documentation

---

**Hour 2: Screenshots & Visual Documentation**

💡 **WHAT WE'RE ACHIEVING:**
Adding visual proof that your app works and looks good. A picture is worth a thousand words.

**Tasks:**
- Take high-quality screenshots:
    - Desktop view (full features visible)
    - Mobile view (showing responsiveness)
    - Both light/clean backgrounds
    - Use browser's device toolbar for consistent sizing
- Optional but impressive: Create an animated GIF showing:
    - Adding a task
    - Completing it
    - Filtering
    - Deleting
    - Use tool: LICEcap (Windows/Mac) or ScreenToGif (Windows)
- Add images to README:
  ```markdown
  ## Screenshots
  
  ### Desktop View
  ![Desktop Screenshot](./screenshots/desktop.png)
  
  ### Mobile View
  ![Mobile Screenshot](./screenshots/mobile.png)
  ```
- Create a `screenshots` folder in your project, add images there
- Commit and push to GitHub
- **Success check:** README shows what your app looks like without needing to click the live link

Ask Claude: "Best practices for taking portfolio project screenshots"

🎯 **What you're learning:** Visual documentation, presentation

---

**Hour 3: Code Cleanup & Git History**

💡 **WHAT WE'RE ACHIEVING:**
Final code polish and ensuring your git history tells a good story.

**Tasks:**
- **Clean up code:**
    - Remove all console.logs (or only keep intentional ones)
    - Check indentation is consistent (use Prettier or VS Code's format document)
    - Ensure all comments are still accurate and helpful
    - Remove any commented-out old code
    - Check for typos in comments/variable names

- **Review git commits:**
    - Look at your commit history: `git log --oneline`
    - Good commits tell a story: "Add task deletion", "Implement localStorage", "Add responsive design"
    - If your commits are messy (lots of "fix", "update", "asdf"), that's okay for learning projects, but note it for next time

- **Add final touches:**
    - Add a favicon (small icon in browser tab):
        - Create or find a simple icon (16x16 or 32x32 PNG)
        - Add to HTML: `<link rel="icon" type="image/png" href="favicon.png">`
    - Update page title: `<title>Todo App | [Your Name]</title>`
    - Add meta description:
      ```html
      <meta name="description" content="A clean, responsive todo app with local storage">
      ```

- **Final testing:**
    - Test in different browsers (Chrome, Firefox, Safari if available)
    - Test on actual phone if possible (not just DevTools)
    - Ask a friend to try it - watch where they get confused
    - Fix any bugs discovered

- **Success check:** Code is clean, professional, ready for others to read

➜ **Understanding check:** "Look at your first commit versus your last commit. What's improved in your code quality?"

🎯 **What you're learning:** Code quality, version control hygiene, final polish

---

**Hour 4: Portfolio Integration & Sharing**

💡 **WHAT WE'RE ACHIEVING:**
Preparing to share your project with the world - on your portfolio site, LinkedIn, and job applications.

**Tasks:**
- **Write a project description for your portfolio** (2-3 sentences):
  ```
  A responsive todo application demonstrating modern JavaScript practices 
  including DOM manipulation, local storage persistence, and clean separation 
  of concerns. Features include task filtering, completion tracking, and a 
  polished, accessible UI.
  ```

- **Write a LinkedIn post** (optional but recommended):
  ```
  Excited to share my latest project: a todo app built with vanilla JavaScript! 🎉
  
  Key features:
  ✅ Local storage for data persistence
  ✅ Filter by all/active/completed
  ✅ Fully responsive design
  ✅ Accessible (keyboard navigation & ARIA)
  
  This project taught me about [mention 1-2 key learnings].
  
  Live demo: [link]
  Code: [GitHub link]
  
  #WebDevelopment #JavaScript #LearningToCode
  ```

- **Prepare for job applications:**
    - Can you explain any part of this code in an interview?
    - Practice: "Walk me through how you implemented data persistence"
    - Practice: "Why did you separate renderTasks from saveTasks?"

- **Add to your portfolio site** (if you have one):
    - Project tile with screenshot
    - Link to live demo and GitHub
    - Your prepared description

- **Pin repository on GitHub:**
    - Go to your GitHub profile
    - Click "Customize your pins"
    - Pin this repository so it shows first

- **Update GitHub About section:**
    - Add your live demo link in the repository's About section (top right)
    - Add topics/tags: javascript, todo-app, vanilla-js, local-storage, portfolio

- **Success check:** Project is ready to share, you have links ready to send, you can explain it confidently

Ask Claude: "Help me write a compelling project description for my portfolio"

➜ **Understanding check:** "If an employer asks 'Why did you build a todo app?', what would you say?"

🎯 **What you're learning:** Professional presentation, self-marketing, interview prep

🎉 **MILESTONE - End of Day 7:**
**You have a complete, portfolio-ready project!**

You can now:
- Share a live link that works on any device
- Show clean, documented code on GitHub
- Explain what you built and what you learned
- Add it to job applications with confidence

This project demonstrates you understand:
✅ JavaScript fundamentals (DOM, events, arrays, objects)
✅ Data persistence (localStorage, JSON)
✅ Software engineering (separation of concerns, clean code)
✅ Modern web practices (responsive design, accessibility)
✅ Professional development (git, documentation, deployment)

---

## **GENERAL TROUBLESHOOTING GUIDE**

Use this whenever you're stuck on any day:

### **"Nothing appears on my page"**
1. Open DevTools Console (F12) - are there errors in red?
2. Check: Is your CSS file linked correctly in HTML `<head>`?
3. Check: Is your JS file linked before `</body>`?
4. Check: Do your element IDs in HTML match what you're selecting in JS?
5. Add `console.log("Script loaded")` at top of JS file - does it appear?

### **"My button doesn't work"**
1. Add `console.log("Button clicked")` inside the click handler - does it appear?
2. If yes: Problem is in your logic. Check what each line does with more console.logs
3. If no: Event listener isn't attached. Check for typos in element ID
4. Check: Is your script running before the HTML loads? (Put script at bottom of body)

### **"Tasks don't persist after reload"**
1. Open DevTools → Application tab → Local Storage
2. Do you see your tasks data there? If no: You're not calling `saveTasks()`
3. If yes but they don't load: Check your `loadTasks()` function
4. Add console.logs: `console.log("Loading:", savedTasks)` to debug
5. Check: Are you calling `loadTasks()` when page loads?

### **"I get 'Cannot read property of null'"**
- This means: You're trying to use an element that doesn't exist
- Check: Does the element ID match exactly? (case-sensitive!)
- Check: Is your script running before HTML loads?
- Add: `console.log(elementName)` before using it - is it null?

### **"My CSS isn't applying"**
1. Check: Is the CSS file linked in HTML `<head>`?
2. Check: Are you using the right selector? (class needs `.`, ID needs `#`)
3. Check: Is there a typo in your class/ID name?
4. In DevTools, inspect the element - do you see your CSS rules?
5. If you see them crossed out: There's a more specific rule overriding them

### **"I'm completely lost"**
1. Take a 10-minute break - seriously, step away
2. Come back and read the error message carefully
3. Add `console.log` statements to see what values you're working with
4. Google the specific error message
5. Ask Claude with this template:

```
📝 **How to Ask Claude for Help:**

"I'm working on Day [X], Hour [Y], trying to [specific task].

Here's my code:
[paste the relevant section - not all your code]

I expected [X] to happen, but [Y] happens instead.

The console shows: [error message, or "no errors"]

I've tried: [what you've already attempted]

Can you help me understand what's wrong?"
```

### **When to ask for help:**
- ✅ After trying for 20-30 minutes
- ✅ After reading error messages and googling
- ✅ After adding console.logs to debug
- ❌ Immediately when something doesn't work
- ❌ Without reading the error message
- ❌ To write the code for you (ask for explanation, then write it yourself)

---

## **SUCCESS METRICS**

By the end of 7 days, you should have:

**Technical Skills:**
- ✅ Understand DOM manipulation (create, modify, remove elements)
- ✅ Handle events (click, keypress)
- ✅ Work with arrays (push, filter, forEach, map)
- ✅ Use localStorage (save, load, parse JSON)
- ✅ Separate data from display (render pattern)
- ✅ Write clean, commented code
- ✅ Use Git & GitHub
- ✅ Deploy to GitHub Pages

**Portfolio:**
- ✅ Live, working application
- ✅ Works on mobile and desktop
- ✅ Professional README with screenshots
- ✅ Clean code on GitHub
- ✅ Can explain any part of your code

**Confidence:**
- ✅ Can start a new project from scratch
- ✅ Can debug your own code
- ✅ Know when and how to ask for help
- ✅ Understand the difference between following a tutorial and actually learning

**Next Steps After Completion:**
1. Build project #2 - apply what you learned to something different
2. Add backend: Learn Node.js/Express to make tasks sync across devices
3. Learn React: The patterns you learned (render, state, data flow) are exactly how React works
4. Start applying for junior developer positions - you have a real portfolio piece now

---

**FINAL NOTES:**

- **Don't rush:** If a day takes longer, that's okay. Understanding > speed.
- **Don't skip testing:** Catching bugs early saves hours later.
- **Don't copy-paste from Claude:** Type it yourself, even if it's slower.
- **Do commit often:** Every time something works, commit it.
- **Do ask questions:** Better to ask and learn than stay stuck and frustrated.
- **Do celebrate:** You're building real things. That's incredible.

**Remember:** Every professional developer was once exactly where you are now. The difference between a beginner and a professional isn't talent - it's persistence and practice. You're doing great. Keep going.

Good luck! 🚀