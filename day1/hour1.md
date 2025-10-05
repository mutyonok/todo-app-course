# DAY 1, HOUR 1: Development Environment Setup

**⏱️ Time: 60 minutes**

---

## 🎯 GOAL
Configure Git on your Mac and create a GitHub account so you're ready to track code changes and deploy your project online.

---

## 📖 KEY CONCEPTS: Version Control & Git

**What is Git?**
Git is a system that saves snapshots of your code as you work. Think of it like "track changes" in Word, but far more powerful. Every time you make progress, you save a snapshot (called a "commit"). You can:
- See what changed between versions
- Revert mistakes
- Try experimental features without breaking working code
- Collaborate with others without overwriting each other's work

**Why professionals use it:**
- Every company uses Git for code
- It's your "undo" button for entire projects
- GitHub (where Git repositories live online) serves as your portfolio
- Interviewers will look at your GitHub profile

**Git vs GitHub:**
- **Git** = the tool on your computer that tracks changes
- **GitHub** = website where you store copies of your Git projects (like Dropbox for code)

This matters for React/Vue later: All modern development uses Git. Learning it now with a simple project means you'll be comfortable with it before tackling frameworks.

---

## 💡 WHAT WE'RE ACHIEVING

You'll install Git, configure it with your identity, and create a GitHub account. By the end, you'll understand what version control is and why every developer uses it. You won't write code yet - we're setting up the professional workflow first.

---

## 📋 THE PROCESS

1. **Install Git** - Get the tool on your Mac
2. **Configure Git** - Tell Git who you are
3. **Create GitHub account** - Set up your online code portfolio
4. **Verify everything works** - Test that Git is ready

---

## ✅ TASKS

### **Task 1: Check if Git is already installed (5 min)**

1. Open **Terminal** (press `Cmd + Space`, type "Terminal", press Enter)
2. Type this command and press Enter:
   ```bash
   git --version
   ```

**What happens:**
- **If you see something like** `git version 2.39.0`: ✅ Git is installed! Skip to Task 3.
- **If you see** `command not found`: Continue to Task 2.

---

### **Task 2: Install Git (15 min)**

Since Homebrew isn't an option, we'll use the official installer.

1. **Download Git:**
    - Go to: https://git-scm.com/download/mac
    - Click the "Binary installer" link
    - Download will start automatically

2. **Install Git:**
    - Open the downloaded `.dmg` file
    - Double-click the `.pkg` installer
    - Click "Continue" through the installation
    - Enter your Mac password when prompted
    - Click "Install"

3. **Verify installation:**
    - Close Terminal completely (Cmd + Q)
    - Open Terminal again (important - refreshes environment)
    - Type: `git --version`
    - You should see a version number

**🚨 Stuck?** If you don't see a version number after closing/reopening Terminal, ask Claude: "I installed Git but git --version gives command not found"

---

### **Task 3: Configure Git with your identity (10 min)**

Git needs to know who you are so each code snapshot is credited to you.

In Terminal, run these two commands (replace with YOUR information):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Example:**
```bash
git config --global user.name "Sarah Chen"
git config --global user.email "sarah.chen@gmail.com"
```

**Important:**
- Keep the quotation marks
- Use the email you'll use for GitHub (next task)
- This info will appear on your commits

**Verify it worked:**
```bash
git config --global --list
```

You should see your name and email in the output.

---

### **Task 4: Create GitHub account (15 min)**

1. **Sign up:**
    - Go to: https://github.com
    - Click "Sign up"
    - Use the SAME email you configured in Git
    - Choose a professional username (employers will see this)
        - ✅ Good: `sarahchen`, `sarah-codes`, `schen-dev`
        - ❌ Avoid: `cutiegirl123`, `xXcoderXx`

2. **Complete verification:**
    - Verify your email address (check inbox)
    - Skip any "personalization" questions (you can always update later)

3. **Explore briefly (5 min):**
    - Look at GitHub's homepage when logged in
    - Click on your profile picture (top right)
    - Notice you have 0 repositories - you'll create your first one tomorrow

---

### **Task 5: Understanding check (5 min)**

Open a note on your Mac (Notes app or anywhere) and answer these questions in your own words:

1. What's the difference between Git and GitHub?
2. Why do developers use version control instead of just saving files?
3. What did the `git config` commands do?

Don't look back at the instructions - test what you remember. This matters for retention.

---

## ✅ SUCCESS CHECKS

**You're done with Hour 1 when:**
- [ ] `git --version` shows a version number in Terminal
- [ ] `git config --global --list` shows your name and email
- [ ] You can log into GitHub in your browser
- [ ] You've answered the 3 understanding check questions

---

## ➜ UNDERSTANDING CHECK

**Before moving to Hour 2, answer this:**

"Tomorrow you'll type `git commit -m "Added HTML structure"`. Based on what you learned today, what do you think this command does?"

If you're not sure, that's okay - you'll learn it tomorrow. But try to guess based on the "snapshot" analogy.

---

## 🎉 MILESTONE REACHED

You now have the same tools professional developers use! Git is installed, configured, and connected to GitHub. Tomorrow you'll use these tools to track your project and deploy it online.

**Next up:** Hour 2 - Creating your first Git repository and deploying to GitHub Pages.