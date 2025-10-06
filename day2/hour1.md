# DAY 2, HOUR 1: DOM Selection & First Event

## 🎯 Hour Goal
Connect JavaScript to your HTML elements and make the "Add Task" button respond to clicks. By the end, you'll see user input appear in the console when clicking the button.

---

## 📖 KEY CONCEPT: The Bridge Between HTML and JavaScript

**What is the DOM?**
The DOM (Document Object Model) is how JavaScript "sees" your HTML. When the browser loads your page, it creates a tree-like structure in memory representing every element. JavaScript can read and manipulate this structure.

**Why This Matters:**
- This is how ALL web interactivity works - Facebook likes, YouTube play buttons, todo apps
- Understanding DOM manipulation is essential before learning React/Vue (which abstract this away)
- Event-driven programming (responding to clicks, types, scrolls) is fundamental to web development

**The Pattern You're Learning:**
1. Select elements (get references to HTML)
2. Listen for events (clicks, key presses)
3. Respond to events (run code when they happen)

This pattern appears in every interactive web application.

---

## ⏮️ 5-MINUTE REVIEW: Yesterday's Foundation

Before writing code, answer these questions (don't look at files):

1. What are the three files in your project and what does each one do?
2. What command pushes your local commits to GitHub?
3. What CSS property did you use to center the container?

*(Answers check your foundation before building on it)*

---

## THE APPROACH

Think of JavaScript as a puppet master and HTML as the puppet. Right now they're disconnected. This hour, you're creating the strings between them:

1. **Find the puppets** - Get JavaScript references to HTML elements
2. **Attach the strings** - Set up event listeners
3. **Make them dance** - Run code when events happen

You're not changing the page yet - just establishing communication.

---

## TASK 1: Store DOM Element References

### 📘 Concept: DOM References and Variables

When you write `document.getElementById('addBtn')`, JavaScript searches through the entire DOM tree and returns a **reference** to that element. Think of it like getting someone's phone number - you can now "call" that element whenever you need it.

**Why store in variables?**
- Searching the DOM is relatively slow
- You'll use these elements multiple times
- Variables make code readable and maintainable

**Critical: Variable Naming**
Variable names should describe **what the element IS**, not what you'll do with it:

❌ Bad: `btn`, `box`, `thing`, `input1`  
✅ Good: `addButton`, `taskInput`, `taskList`

Professional code is self-documenting. Someone reading your code should understand it without comments.

### ✅ Your Tasks:

1. **Open `script.js`** (create it if needed - save in same folder as index.html)

2. **Select and store three elements:**
    - The input field (where users type)
    - The add button
    - The `<ul>` list (where tasks will appear)

   Remember: `document.getElementById('theIdFromHTML')`

3. **Log all three to console** to verify the references work

### Success Check:
- Open browser, press F12 for DevTools
- Click Console tab
- Refresh page
- You see three HTML element references logged (not `null` or `undefined`)

### ➜ Understanding Check:
*"What's the difference between `document.getElementById('addBtn')` and `'addBtn'` (just the string)?"*

---

## TASK 2: Add Event Listener to Button

### 📘 Concept: Event Listeners

**What are events?**
Events are things that happen in the browser: clicks, key presses, mouse movements, page loads. JavaScript can "listen" for these events and run code when they occur.

**Two ways to write event listeners:**

```javascript
// Classic function syntax
element.addEventListener('click', function(event) {
    // code here
});

// Arrow function syntax (modern, shorter)
element.addEventListener('click', (event) => {
    // code here
});
```

Both work identically. Arrow functions are more common in modern code.

**The Event Parameter:**
The function automatically receives an `event` object (often shortened to `e` or `evt`). This object contains information about what happened - what was clicked, where, when, etc.

You don't have to use it, but it's always available if needed.

And if think you don't need it, you can omit it altogether:

```javascript
// Arrow function syntax without event parameter
element.addEventListener('click', () => {
    // code here
});
```
### ✅ Your Task:

1. **Add a click event listener to your add button**
    - Use either syntax (try arrow functions - you'll see them everywhere)
    - The function should receive the event parameter
    - Log the event object to console

### Success Check:
- Click the "Add Task" button
- Console shows an event object (has properties like `type: "click"`, `target`, etc.)
- Each click logs a new event

### ➜ Understanding Check:
*"Why do we pass a function to addEventListener instead of just calling code directly?"*

---

## TASK 3: Get Input Value on Click

### 📘 Concept: Input Element Values

HTML `<input>` elements store what users type in a special property called `.value`:

```javascript
const userTyped = myInputElement.value;  // Returns a string
```

**Important:**
- `.value` is always a string, even for number inputs
- `.value` gets the CURRENT content at the moment you access it
- You need to access `.value` each time you want the latest content

### ✅ Your Task:

1. **Modify your event listener:**
    - Remove the console.log of the event object
    - Instead, get the value from your input element
    - Log that value to console

2. **Test it thoroughly:**
    - Type "Buy milk" → Click button → Should log "Buy milk"
    - Type something else → Click button → Should log new text
    - Leave input empty → Click button → Should log empty string ""

### Success Check:
- Whatever you type appears in console when you click the button
- Different text appears each time

### ➜ Understanding Check:
*"What happens if you store the input's value in a variable OUTSIDE the event listener? Will it update each time you type?"*

---

## ✅ SUCCESS CHECKS - ALL MUST PASS
✅ Console is open and you can see logs
✅ Three variables created: addBtn, taskInput, taskList
✅ All three elements log correctly to console
✅ Click listener attached to button
✅ Clicking button logs the input's value
✅ Different inputs show different values in console

---

## ✋ HOUR 1 COMPLETE - Exit Ticket

Before moving on, answer these in your own words (no code, just concepts):

1. **What is a DOM reference?** Why store it in a variable?
2. **What does addEventListener do?** What are its two parameters?
3. **When you access `.value`** on an input element, what do you get?

**What's Still Unclear?** Write one thing you're not 100% confident about.

---

## 🎯 What You've Achieved

Your JavaScript can now:
- Find and store references to HTML elements
- Detect when users click the button
- Read what users typed in the input field

**Next hour:** You'll use this input value to create new task elements and add them to the page.

---

**⏸️ Take a 10-minute break before Hour 2.** Walk around, get water. Your brain needs processing time.