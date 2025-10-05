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

This foundation makes adding accessibility features (Day 6) much easier.

---

## 💡 WHAT WE'RE ACHIEVING

You'll create the HTML structure users will interact with: input field, add button, and list container. You'll link empty CSS and JavaScript files. Then you'll use the professional git workflow to push everything live.

---

## 📋 THE PROCESS

1. **Create the file structure** (HTML, CSS, JS files)
2. **Write HTML5 boilerplate**
3. **Build the todo app structure** with semantic tags
4. **Link external files** properly
5. **Test file connections** with console.log
6. **Use professional git workflow** to deploy

---

## ✅ TASKS

### **Task 1: Create project files (5 min)**

In VS Code, create three new files in your `todo-app` folder:

1. Click "New File" icon or press `Cmd + N`
2. Save as `index.html`
3. Repeat for `styles.css`
4. Repeat for `script.js`

**Your folder structure:**
```
todo-app/
  ├── README.md
  ├── index.html
  ├── styles.css
  └── script.js
```

---

### **Task 2: Write HTML5 boilerplate (10 min)**

Open `index.html`. Every HTML page needs this foundation:

**Required elements:**
1. `<!DOCTYPE html>` declaration
2. `<html>` root element with language
3. `<head>` section with:
    - Character encoding meta tag
    - Viewport meta tag (for mobile responsiveness)
    - Title
    - Link to CSS file
4. `<body>` section
5. Script tag linking to JavaScript file

**Write this from scratch.** Think through what each piece does.

**Hints if stuck after 10 minutes:**
- The doctype is: `<!DOCTYPE html>`
- Language attribute: `lang="en"`
- Charset: `UTF-8`
- Viewport: `width=device-width, initial-scale=1.0`
- CSS link goes in `<head>`, script goes before `</body>`

---

### **Task 3: Plan the app structure (5 min)**

Before writing more HTML, visualize what users will see:

```
┌─────────────────────┐
│   My Todo List      │  ← Heading
├─────────────────────┤
│ [input] [Add Task]  │  ← Input area
├─────────────────────┤
│                     │
│  (empty list)       │  ← Where tasks appear
│                     │
└─────────────────────┘
```

**Three sections:**
1. **Header** - The title
2. **Input area** - Text input + button
3. **List area** - Empty unordered list (JavaScript fills it later)

---

### **Task 4: Build the structure with semantic tags (20 min)**

Inside `<body>`, create:

**1. Main container:**
- Use `<main>` tag (semantic: primary content)
- Everything else goes inside this

**2. Header section:**
- Use `<header>` tag (semantic: introductory content)
- Add `<h1>` heading with your app title

**3. Input section:**
- Use `<section>` tag (semantic: thematic grouping)
- Add `<input>` with type "text"
- Add `<button>` for submitting

**4. List section:**
- Use another `<section>` tag
- Add unordered list (keep it empty, no todos yet)

**Key semantic tags to use:**
- `<main>` - wraps all content (only one per page)
- `<header>` - for the title area
- `<section>` - for input area and list area (two sections total)
- `<button>` - for the add button (NOT a div)
- `<ul>` - for the task list

**Try writing this completely from scratch.** Use your knowledge of HTML structure.

**Stuck after 15 minutes?** Ask Claude: "I'm building a todo app structure with main, header, two sections (input and list). What HTML tags should I use and where?"

---

### **Task 5: Link external files (already done!)**

If you followed Task 2, your CSS and JavaScript are already linked:
- `<link rel="stylesheet" href="styles.css">` in `<head>`
- `<script src="script.js"></script>` before `</body>`

**Why JavaScript goes at the bottom:**
Browser reads HTML top-to-bottom. Script at bottom means HTML loads before JavaScript runs - critical for selecting elements that must exist first.

---

### **Task 6: Test JavaScript connection (10 min)**

Open `script.js` and add:

```javascript
console.log('JavaScript file connected!');
```

**Open index.html in browser:**

- Right-click `index.html` in VS Code
- Select "Open with Live Server"
- Browser opens automatically

**Check the console:**
- Press `Cmd + Option + J` (Chrome) or `Cmd + Option + C` (Safari)
- Should see: `JavaScript file connected!`

**What you should see on page:**
- Heading
- Unstyled input field
- Unstyled button
- Empty space where list will be

✅ **Success check:** Console shows your message.

---

### **Task 7: Professional git workflow (10 min)**

**This exact pattern is used by developers worldwide, every day.**

```bash
git status
```
See three untracked files.

```bash
git add .
```
Stage all changes. The `.` means "everything in current directory."

**Why we prefer `git add .`:**
- Faster with multiple files
- You know what changed (you just wrote it)
- Professional practice: commit related changes together
- Only use when you've reviewed your changes

```bash
git status
```
Files now "Changes to be committed" (green).

```bash
git commit -m "Add HTML structure with semantic elements"
```

**Good commit messages:**
- ✅ "Add HTML structure with semantic elements"
- ✅ "Create project file structure"
- ❌ "update" (too vague)
- ❌ "fixed stuff" (not descriptive)

```bash
git push
```

**The professional workflow:**
```
1. Make changes
2. git status (review)
3. git add . (stage)
4. git commit -m "what you did"
5. git push (upload & deploy)
```

**You'll use this pattern 50+ times in this project.**

**Verify deployment:**
- Wait 30-60 seconds
- Visit: `https://YOUR-USERNAME.github.io/todo-app/`
- Should see unstyled HTML

---

### **Task 8: Understanding check (5 min)**

Answer in notes:

1. Why `<button>` instead of `<div onclick="...">`?
2. Why does `<script>` go at bottom of `<body>`?
3. Name three semantic HTML tags you used and why each one.
4. What does `git add .` do?

---

## ✅ SUCCESS CHECKS

**You're done when:**
- [ ] HTML displays heading, input, and button in browser
- [ ] Console shows "JavaScript file connected!"
- [ ] GitHub shows all three new files
- [ ] GitHub Pages URL displays the HTML
- [ ] You wrote the HTML yourself (not copied)
- [ ] You used the git workflow: status → add . → commit → push

---

## ➜ UNDERSTANDING CHECK

Find three semantic tags in your HTML (`<main>`, `<header>`, `<section>`, etc.). For each, explain why you used that specific tag instead of `<div>`.

---

## 🎉 MILESTONE REACHED

Your HTML structure is live! You have:
- Semantic HTML written from scratch
- File linking working
- Tested JavaScript connection
- Professional git workflow mastered

**Remember:** `git status → git add . → git commit -m "message" → git push`

**Next up:** Hour 4 - Transform this raw HTML with CSS styling.