# DAY 1, HOUR 2: Create Repository & Deploy to GitHub Pages

**⏱️ Time: 60 minutes**

---

## 🎯 GOAL
Create your project folder, initialize Git tracking, connect it to GitHub, and enable GitHub Pages so your project has a live URL by end of this hour.

---

## 📖 KEY CONCEPTS: Local vs Remote & The Deployment Pipeline

**Three places your code lives:**

1. **Local (your Mac)** - Where you edit code
2. **Remote (GitHub)** - Cloud backup and sharing
3. **Deployed (GitHub Pages)** - Live website anyone can visit

**The workflow:**
```
Edit code → Save changes (commit) → Upload to GitHub (push) → Automatic deployment
```

**Why this matters:**
- **Portfolio:** Live URL to share with employers
- **Backup:** Code is safe even if your laptop breaks
- **Collaboration:** Later you can work with others
- **Real workflow:** This is how professionals deploy React apps, just with fancier tools

Understanding this flow now makes deploying frameworks later feel natural.

---

## 💡 WHAT WE'RE ACHIEVING

You'll create a project folder, tell Git to track it, create a matching repository on GitHub, connect them, and turn on GitHub Pages. The folder will be empty initially - we're establishing the pipeline before putting anything through it.

---

## 📋 THE PROCESS

1. **Create project folder** with proper structure
2. **Initialize Git** to start tracking
3. **Create GitHub repository** (the remote copy)
4. **Connect local to remote**
5. **Enable GitHub Pages** for deployment
6. **Test the pipeline** with a simple file

---

## ✅ TASKS

### **Task 1: Create project folder (5 min)**

1. **Choose a location for your projects:**
    - Open Finder
    - Go to your home folder (the house icon in sidebar)
    - Create a new folder called `coding-projects` (if you don't have one)

2. **Create the project folder:**
    - Inside `coding-projects`, create a new folder: `todo-app`

3. **Open in VS Code:**
    - Launch VS Code
    - File → Open Folder
    - Select your `todo-app` folder
    - Click "Open"

4. **Open integrated terminal:**
    - In VS Code, go to Terminal → New Terminal (or press `Ctrl + \``)
    - You should see a terminal at the bottom showing something like:
      ```
      yourname@YourMac todo-app %
      ```

**Why we're doing this:** VS Code's integrated terminal starts in your project folder automatically, making commands easier.

---

### **Task 2: Initialize Git repository (10 min)**

In the VS Code terminal, type:

```bash
git init
```

**What this does:** Creates a hidden `.git` folder that tracks all changes. Your folder is now a "repository" (repo).

**Verify it worked:**
```bash
ls -la
```

You should see `.git` in the list (the `a` flag shows hidden files).

**Create a README:**

In VS Code, create a new file (File → New File or `Cmd + N`):
- Save it as `README.md`
- Add this content:
  ```markdown
  # Todo List Application
  
  A simple todo app built with HTML, CSS, and JavaScript.
  ```
- Save the file (`Cmd + S`)

**Tell Git to track this file:**

```bash
git add README.md
git commit -m "Initial commit"
```

**What just happened:**
- `git add` = "Include this file in the next snapshot"
- `git commit` = "Save the snapshot with a description"
- The `-m` flag lets you add a message describing what changed

**Check your work:**
```bash
git log
```

You should see your commit with your name, date, and message.

---

### **Task 3: Create GitHub repository (10 min)**

1. **Go to GitHub:**
    - Log into https://github.com
    - Click the **+** icon (top right)
    - Select "New repository"

2. **Configure the repository:**
    - **Repository name:** `todo-app` (must match your folder name)
    - **Description:** "A todo list app built with vanilla JavaScript"
    - **Public** (not Private - employers need to see it)
    - **DO NOT** check "Add a README" - you already have one
    - **DO NOT** add .gitignore or license yet
    - Click "Create repository"

3. **You'll see a page with setup instructions - keep this page open for the next task**

---

### **Task 4: Connect local repository to GitHub (10 min)**

On the GitHub page you just saw, find the section: **"…or push an existing repository from the command line"**

Copy the commands shown (they'll include your username). They look like:

```bash
git remote add origin https://github.com/YOUR-USERNAME/todo-app.git
git branch -M main
git push -u origin main
```

**Paste these into your VS Code terminal and run them.**

**What each command does:**
- `git remote add origin [URL]` = "Connect this local repo to that GitHub repo"
- `git branch -M main` = "Name the main branch 'main'" (Git's default)
- `git push -u origin main` = "Upload everything to GitHub"

**Verify it worked:**
- Refresh your GitHub repository page in the browser
- You should now see your README.md file displayed

**🚨 Common issue:** If asked for username/password, GitHub requires a Personal Access Token instead of password:
- Ask Claude: "GitHub is asking for credentials when I push, how do I create a personal access token?"

---

### **Task 5: Enable GitHub Pages (10 min)**

1. **In your GitHub repository page:**
    - Click "Settings" tab (top right of the repo)
    - Scroll down the left sidebar
    - Click "Pages"

2. **Configure GitHub Pages:**
    - Under "Source", select: **Deploy from a branch**
    - Under "Branch", select: **main** and **/root**
    - Click "Save"

3. **Wait for deployment (1-2 minutes):**
    - Refresh the page
    - You should see: "Your site is live at `https://YOUR-USERNAME.github.io/todo-app/`"
    - Click the "Visit site" button

4. **What you'll see:**
    - Just your README content displayed as plain text
    - That's expected - we haven't added HTML yet
    - **Copy this URL** - this is your project's permanent address

---

### **Task 6: Test the pipeline (10 min)**

Let's verify the full workflow by making a change.

**Update your README:**

In VS Code, add a new line to `README.md`:
```markdown
# Todo List Application

A simple todo app built with HTML, CSS, and JavaScript.

Live demo: [View here](https://YOUR-USERNAME.github.io/todo-app/)
```

**Push the change:**

```bash
git add README.md
git commit -m "Add live demo link"
git push
```

**Verify deployment:**
- Wait 30-60 seconds
- Refresh your GitHub Pages URL
- You should see the updated README with the link

**🎉 The pipeline works!** Edit → Commit → Push → Auto-deploy

---

### **Task 7: Understanding check (5 min)**

Answer these in your notes:

1. What's the difference between `git commit` and `git push`?
2. Draw or describe the flow: Where does your code go from VS Code to appearing on the web?
3. What does `git remote add origin` do?

---

## ✅ SUCCESS CHECKS

**You're done with Hour 2 when:**
- [ ] `git log` shows your commits in VS Code terminal
- [ ] Your GitHub repository shows your README.md
- [ ] Your GitHub Pages URL displays your README
- [ ] You can make a change, commit, push, and see it live within 1 minute

---

## ➜ UNDERSTANDING CHECK

**Answer without looking back:**

"You just typed `git push`. Explain in your own words what happens between pressing Enter and your changes appearing on GitHub."

If stuck, that's okay - the goal is to think through it, not memorize.

---

## 🎉 MILESTONE REACHED

Your deployment pipeline is live! You now have:
- Local Git repository tracking changes
- Remote GitHub repository (your backup/portfolio)
- Live GitHub Pages URL (your deployment)

Everything you build from now on will automatically appear at your URL within seconds of pushing.

**Next up:** Hour 3 - Building the HTML structure that users will interact with.