# DAY 1, HOUR 4: Basic Styling

**⏱️ Time: 60 minutes**

---

## 🎯 GOAL
Transform the raw HTML into a clean, centered interface with proper spacing, styled inputs, and a professional button. Deploy and see the visual transformation live.

---

## 📖 KEY CONCEPTS: The CSS Box Model & Modern Centering

**The Box Model:**
Every element is a box with four layers:
1. **Content** - the text/image itself
2. **Padding** - space inside the border
3. **Border** - the edge of the element
4. **Margin** - space outside the border

```
┌─────── margin ───────┐
│  ┌──── border ────┐  │
│  │  ┌─ padding ─┐ │  │
│  │  │  content  │ │  │
│  │  └───────────┘ │  │
│  └─────────────────┘  │
└──────────────────────┘
```

**Modern centering with Flexbox:**
Old way (2010s): complex margin calculations, positioning hacks
Modern way: Flexbox does it in 3 lines

This matters because Flexbox is how React/Vue developers build layouts.

---

## 💡 WHAT WE'RE ACHIEVING

You'll write CSS that centers content, adds breathing room with padding/margin, styles the input and button to look professional, and uses a simple color scheme. The app will look intentional instead of raw HTML.

---

## 📋 THE PROCESS

1. **Reset defaults** and set up the body
2. **Center the main container** with Flexbox
3. **Style the input field**
4. **Style the button** with hover effect
5. **Add spacing** throughout
6. **Deploy and compare** before/after

---

## ✅ TASKS

### **Task 1: Base styles (10 min)**

Open `styles.css` and add:

```css
/* Reset and base styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
  background-color: #f5f5f5;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}
```

**What this does:**
- `* { ... }` - Removes browser default spacing
- `box-sizing: border-box` - Makes width calculations predictable
- `display: flex` - Turns body into flex container
- `justify-content: center` - Centers horizontally
- `align-items: center` - Centers vertically
- `min-height: 100vh` - Full viewport height (vh = viewport height)

**Test it:** Save and check your browser. Content should be centered on page.

---

### **Task 2: Style main container (10 min)**

Add below your body styles:

```css
main {
  background-color: white;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 500px;
}

header {
  text-align: center;
  margin-bottom: 30px;
}

h1 {
  color: #333;
  font-size: 32px;
  font-weight: 600;
}
```

**Understanding these properties:**
- `border-radius` - Rounded corners (modern look)
- `box-shadow` - Subtle shadow for depth (rgba = red, green, blue, alpha/transparency)
- `max-width` - Won't exceed 500px even on large screens
- `width: 100%` - Takes full width up to max-width

**Test it:** White card should appear with rounded corners and shadow.

---

### **Task 3: Style input section (15 min)**

```css
.todo-input {
  display: flex;
  gap: 10px;
  margin-bottom: 30px;
}

#taskInput {
  flex: 1;
  padding: 12px 16px;
  font-size: 16px;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.3s;
}

#taskInput:focus {
  border-color: #4a90e2;
}

#taskInput::placeholder {
  color: #999;
}
```

**Key concepts:**
- `flex: 1` - Input takes all available space, button stays its natural width
- `gap: 10px` - Space between input and button (easier than margins)
- `outline: none` - Removes default browser outline (we'll style focus state instead)
- `:focus` - State when user clicks/tabs into input
- `transition` - Smooth color change (0.3 seconds)
- `::placeholder` - Styles the placeholder text

**Test it:** Click the input field - border should turn blue smoothly.

---

### **Task 4: Style button (15 min)**

```css
#addBtn {
  padding: 12px 24px;
  font-size: 16px;
  font-weight: 600;
  color: white;
  background-color: #4a90e2;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

#addBtn:hover {
  background-color: #357abd;
}

#addBtn:active {
  transform: translateY(1px);
}
```

**Understanding states:**
- `:hover` - When mouse is over button (darker blue)
- `:active` - When button is being clicked (moves down 1px)
- `cursor: pointer` - Hand cursor on hover
- `border: none` - Removes default button border

**Test it:** Hover and click the button. Notice the color change and subtle press effect.

---

### **Task 5: Style task list container (5 min)**

```css
.todo-list ul {
  list-style: none;
}

#taskList {
  min-height: 50px;
}
```

**Why:**
- `list-style: none` - Removes bullet points
- `min-height` - Prevents collapse when empty

**Test it:** The empty list area maintains space.

---

### **Task 6: Deploy with professional workflow (5 min)**

**The workflow you'll use hundreds of times:**

```bash
git status
```
See what changed (should show `styles.css` modified).

```bash
git add .
```
Stage all changes.

```bash
git commit -m "Add basic CSS styling and layout"
```
Create snapshot with descriptive message.

```bash
git push
```
Upload to GitHub and auto-deploy.

**Wait 30-60 seconds, then refresh your GitHub Pages URL.**

---

### **Task 7: Before/after comparison (3 min)**

Take a moment to appreciate the transformation:

**Before:** Raw HTML, left-aligned, default fonts, no spacing
**After:** Centered card, professional colors, proper spacing, interactive elements

This demonstrates how CSS transforms structure into experience.

---

### **Task 8: Understanding check (2 min)**

Answer quickly:

1. What does `display: flex` on the body do?
2. Why do we use `:hover` on the button?
3. What's the difference between `padding` and `margin`?

---

## ✅ SUCCESS CHECKS

**You're done with Hour 4 when:**
- [ ] White card is centered on page with shadow
- [ ] Input field border turns blue when focused
- [ ] Button changes color on hover and presses down when clicked
- [ ] Everything is deployed and live at your GitHub Pages URL
- [ ] You understand the git workflow: `status → add . → commit → push`

---

## ➜ UNDERSTANDING CHECK

**Without looking at code:**

Explain what Flexbox does and why it's better than old centering methods. If you can't, that's your signal to ask Claude: "Explain Flexbox centering in simple terms."

---

## 🎉 DAY 1 COMPLETE!

You've accomplished:
- ✅ Set up Git and GitHub
- ✅ Created and deployed a repository
- ✅ Built semantic HTML structure
- ✅ Styled a professional-looking interface
- ✅ Mastered the professional git workflow

**Your app is live online.** Tomorrow you'll make it interactive - adding, deleting, and completing tasks.

---

## 🎯 END OF DAY REFLECTION (5 minutes)

Before stopping, write brief answers:

1. What did I learn today that I didn't know this morning?
2. What's still confusing?
3. The git workflow in my own words: _______

This reflection matters for retention. Don't skip it.

**Next session:** Day 2, Hour 1 - Making the button actually do something when clicked.