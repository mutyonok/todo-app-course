# DAY 1, HOUR 3: Build HTML Structure

**⏱️ Time: 60 minutes**

---

## 🎯 GOAL
Create the HTML skeleton of your todo app with semantic markup, link CSS and JavaScript files, and push to see it live.

---

## 📖 KEY CONCEPTS: Semantic HTML & Document Structure

**Semantic HTML = Tags that describe meaning, not just appearance**

Compare:
```html
<!-- Non-semantic (bad) -->
<div class="header">
  <div class="title">My Todos</div>
</div>

<!-- Semantic (good) -->
<header>
  <h1>My Todos</h1>
</header>
```

**Why semantic HTML matters:**

1. **Accessibility:** Screen readers understand `<nav>`, `<main>`, `<button>` - not generic `<div>`s
2. **SEO:** Search engines prioritize semantic content structure
3. **Maintainability:** Other developers (and future you) understand the code faster
4. **Modern standards:** Frameworks like React still use semantic HTML underneath

**Key semantic tags we'll use:**
- `<header>` - Top section of page/section
- `<main>` - Primary content (only one per page)
- `<section>` - Thematic grouping of content
- `<ul>` - Unordered list (perfect for todos)
- `<button>` - Interactive element (NOT `<div onclick>`)

This foundation makes adding accessibility features (Day 6) much easier.

---

## 💡 WHAT WE'RE ACHIEVING

You'll create the HTML structure users will interact with: input field, add button, and list container. You'll link empty CSS and JavaScript files (creating them in the process). Then you'll use the professional git workflow to push everything live.

---

## 📋 THE PROCESS

1. **Create the file structure** (HTML, CSS, JS files)
2. **Write semantic HTML** boilerplate and todo structure
3. **Link external files** properly
4. **Test file connections** with console.log
5. **Use professional git workflow** to deploy

---

## ✅ TASKS

### **Task 1: Create project files (5 min)**

In VS Code, create three new files in your `todo-app` folder:

1. Click "New File" icon or press `Cmd + N`
2. Save as `index.html`
3. Repeat for `styles.css`
4. Repeat for `script.js`

**Your folder structure should be:**
```
todo-app/
  ├── README.md
  ├── index.html
  ├── styles.css
  └── script.js
```

---

### **Task 2: Write HTML structure (20 min)**

Open `index.html` and type this HTML5 boilerplate with semantic structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Todo List App</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <main>
    <header>
      <h1>My Todo List</h1>
    </header>

    <section class="todo-input">
      <input 
        type="text" 
        id="taskInput" 
        placeholder="What needs to be done?">
      <button id="addBtn">Add Task</button>
    </section>

    <section class="todo-list">
      <ul id="taskList"></ul>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>
```

**Understanding the structure:**

- `<!DOCTYPE html>` - Tells browser this is HTML5
- `<html lang="en">` - Language for accessibility/SEO
- `<meta charset="UTF-8">` - Character encoding (supports emojis, accents, etc.)
- `<meta name="viewport"...>` - Makes responsive design work on mobile
- `<main>` - Primary content wrapper (semantic)
- `<header>` - Top section with title (semantic)
- `<section>` - Two sections: input area and list area (semantic)
- `<ul id="taskList"></ul>` - Empty list that JavaScript will fill
- `id` attributes - How JavaScript will find these elements

**Why these specific IDs:**
- `taskInput` - the input field
- `addBtn` - the add button
- `taskList` - the `<ul>` where tasks will appear

You'll use these IDs tomorrow with `getElementById()`.

---

### **Task 3: Link external files (5 min)**

**Notice the links in your HTML:**

```html
<link rel="stylesheet" href="styles.css">  <!-- In <head> -->
<script src="script.js"></script>          <!-- Before </body> -->
```

**Why JavaScript goes at the bottom:**
The browser reads HTML top-to-bottom. Script at the bottom means HTML loads before JavaScript runs - important for selecting elements that need to exist first.

**Leave CSS and JS files empty for now** - we'll add content in the next tasks.

---

### **Task 4: Test JavaScript connection (10 min)**

Open `script.js` and add:

```javascript
console.log('JavaScript file connected!');
```

**Open index.html in browser:**

**Method 1 - VS Code Live Server (recommended):**
- Right-click `index.html` in VS Code
- Select "Open with Live Server"
- Browser opens automatically

**Method 2 - Manual:**
- In Finder, navigate to your `todo-app` folder
- Double-click `index.html`
- Opens in default browser

**Check the console:**
- In browser, press `Cmd + Option + J` (Chrome) or `Cmd + Option + C` (Safari)
- You should see: `JavaScript file connected!`

**What you should see on the page:**
- Heading: "My Todo List"
- Input field with placeholder text
- "Add Task" button
- That's it - no styling yet

✅ **Success check:** Console shows your message.

---

### **Task 5: Professional git workflow (15 min)**

**This is the exact workflow you'll use hundreds of times as a professional developer. Memorize this pattern.**

**1. Check what changed:**

```bash
git status
```

You'll see three "untracked files": `index.html`, `styles.css`, `script.js`

**2. Stage files (two methods):**

**Method A - Add files individually:**
```bash
git add index.html
git add styles.css
git add script.js
```

**Method B - Add all at once (preferred):**
```bash
git add .
```

**Why we prefer `git add .`:**
- Faster when you have many changes
- You've already reviewed your changes (you wrote them)
- In real projects, you commit related changes together
- The `.` means "current directory and everything inside"

**Professional tip:** Only use `git add .` when you know what's changed. Run `git status` first.

**3. Check what's staged:**
```bash
git status
```

Files should now be "Changes to be committed" (green instead of red).

**4. Commit with descriptive message:**

```bash
git commit -m "Add HTML structure with semantic elements"
```

**Good commit messages:**
- ✅ "Add HTML structure with semantic elements"
- ✅ "Create project file structure"
- ❌ "update" (too vague)
- ❌ "fixed stuff" (not descriptive)

**5. Push to GitHub (and auto-deploy):**

```bash
git push
```

**This is the professional workflow:**
```
1. Make changes in VS Code
2. git status (see what changed)
3. git add . (stage all changes)
4. git commit -m "Description of what you did"
5. git push (upload to GitHub + deploy)
```

**You'll do this 50+ times during this project. This exact pattern is used at Google, Meta, Netflix - everywhere.**

**6. Verify deployment (2 min):**
- Wait 30-60 seconds
- Visit your GitHub Pages URL: `https://YOUR-USERNAME.github.io/todo-app/`
- You should see your unstyled HTML

---

### **Task 6: Understanding check (5 min)**

Answer in your notes:

1. Why do we use `<button>` instead of `<div onclick="...">`?
2. Why does the `<script>` tag go at the bottom of `<body>`?
3. What's the difference between `git add index.html` and `git add .`?
4. In the professional workflow, which command actually uploads your code to GitHub?

---

## ✅ SUCCESS CHECKS

**You're done with Hour 3 when:**
- [ ] `index.html` displays heading, input, and button in browser
- [ ] Browser console shows "JavaScript file connected!"
- [ ] GitHub repository shows all three new files
- [ ] Your GitHub Pages URL displays the HTML (unstyled is fine)
- [ ] You've used the complete git workflow: status → add → commit → push

---

## ➜ UNDERSTANDING CHECK

**Before moving on:**

Look at your `index.html` and find three semantic tags (like `<main>`, `<header>`, `<section>`). For each one, explain in your own words why we used that specific tag instead of a `<div>`.

Example: "We used `<main>` because..."

---

## 🎉 MILESTONE REACHED

Your HTML structure is live! You have:
- Semantic HTML that screen readers and search engines understand
- Proper file linking (CSS and JS)
- Tested JavaScript connection
- Practiced the professional git workflow you'll use daily

**Remember:** `git status → git add . → git commit -m "message" → git push`

This exact pattern is used by developers worldwide, every single day.

**Next up:** Hour 4 - Transform this raw HTML into something visually appealing with CSS.