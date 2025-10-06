# DAY 2 HOUR 4: MARK COMPLETE TOGGLE

## 5-MINUTE RETRIEVAL PRACTICE

1. How do you create a button element with JavaScript?
2. What property do you use to access an element's parent?
3. What's the difference between `textContent` and `innerHTML`?

---

## 🎯 GOAL
Make tasks toggle between complete (crossed out) and incomplete when clicked. Learn CSS class manipulation for visual state changes.

---

## 💡 WHAT WE'RE ACHIEVING

Users can add and delete tasks, but can't mark progress. You'll make clicking a task toggle it between complete/incomplete with visual feedback (strikethrough, changed color). This requires CSS class manipulation and understanding event targets.

---

## THE APPROACH: CLICK-TO-TOGGLE PATTERN

**User interaction:**
- Click task text → add strikethrough (mark complete)
- Click again → remove strikethrough (mark incomplete)
- Click delete button → remove task (should NOT toggle)

We say we change the **STATE** of the task.

---

## 📖 KEY CONCEPT: STATE MANAGEMENT WITH CSS CLASSES

**The pattern:** Use CSS classes to represent different states, then toggle (add or remove) them with JavaScript.

**Common UI states:**
- `completed` / `done` - Task finished
- `active` - Currently selected item
- `disabled` - Non-interactive element
- `hidden` - Invisible element
- `error` - Invalid input
- `loading` - Fetching data

**Why not inline styles?**
- `element.style.textDecoration = 'line-through'` works, but doesn't scale
- CSS classes keep styling in CSS files (separation of concerns)
- Easy to add multiple style changes at once (color, opacity, decoration, etc.)
- Professional codebases use class-based state management

**The classList API:**

To manipulate classes from Javascript, we should use DOM element's `.classList` property.

We can add, remove, toggle CSS classes on any element and check if element has a CSS class.

```javascript
element.classList.add('class-name');     // Add class
element.classList.remove('class-name');  // Remove class
element.classList.toggle('class-name');  // Add if absent, remove if present
element.classList.contains('class-name'); // Check if class exists
```

**Why this matters:** This is exactly how React, Vue, and all modern frameworks handle state-driven styling. You're learning the foundational pattern.

---

## TASK 1: Create CSS for Completed State (8 min)

**Goal:** Define how completed tasks should look.

In your CSS, create a `.completed` class (or `.done`, `.checked`, whatever name you prefer).

**Suggested styling:**
- Text decoration: line-through (crossed out text)
- Color: lighter gray (#888, #999) to show it's done
- Optional: Reduced opacity (0.6-0.7) for subtle fade effect

**Success check:** No visual change yet (you haven't applied the class), but CSS is written

**➜ Understanding check:** Why create a class instead of directly manipulating styles with JavaScript?

---

## TASK 2: Add Toggle to Task Click (15 min)

**Goal:** Clicking a task adds/removes the `completed` class.

**Your task:** Add a click listener to the `<li>` element that toggles the `completed` class.

**Try it yourself first.** After 12 minutes, if stuck, ask Claude: "How do I add a click listener to an li element that toggles a CSS class?"

**Success check:**
- Click a task → it gets crossed out
- Click again → strikethrough disappears
- Can toggle any task multiple times

**➜ Understanding check:** What happens if you click very quickly multiple times? Does it toggle each time?

---

## TASK 3: Understanding Event Propagation (20 min)

**The problem:** Right now, clicking the delete button toggles the task AND deletes it. We only want the delete.

**Technical challenge:** Both task and button are clickable, both inside the `<li>`. 

You need to ensure:
1. Clicking task text toggles complete state
2. Clicking delete button does NOT toggle (only deletes)

### Part A: Visualize the Problem (8 min)

**Concept: Event Bubbling**

When you click the delete button, the click "bubbles up":
1. Button receives click
2. Click bubbles to parent `<li>`
3. `<li>` receives click and toggles

**Your task - Make it visible:**

1. In your delete button's click handler, add at the very top:
   ```javascript
   console.log('Delete button clicked');
   ```

2. In your `<li>`'s click handler, add at the very top:
   ```javascript
   console.log('Li clicked');
   ```

3. Open DevTools console
4. Click the delete button
5. Observe: You see BOTH messages! "Delete button clicked" then "Li clicked"

**Try it:**
- Click delete button → see both logs
- Click task text (not button) → see only "Li clicked"

This proves the click is bubbling from button to parent.

**➜ Understanding check:** Why does clicking the button trigger both handlers?

---

### Part B: Stop the Bubbling (12 min)

**The solution: we can stop an event to propagate to parent elements**

The `event` object has method `.stopPropagation()`, when called - event stops "bubbling".

```javascript
button.addEventListener('click', function(event) {
  event.stopPropagation(); // Stop click from bubbling to parent
  console.log('Delete button clicked');
  // Delete logic here
});
```

**Your task:**

1. Add `event.stopPropagation();` as the FIRST line in your delete button's click handler (before the console.log)
2. Save and test
3. Click delete button → should only see "Delete button clicked" (not "Li clicked")
4. The task should delete WITHOUT toggling

**Success check:**
- Clicking delete button shows only one console log
- Task deletes WITHOUT toggling completion
- Clicking task text still toggles and shows "Li clicked"

**Clean up:** Remove or comment out both console.log statements once you understand.

**➜ Understanding check:** What would happen if you put `stopPropagation()` AFTER the delete logic instead of before?

---

## TASK 4: Improve Toggle Target (12 min)

**Current issue:** The entire `<li>` is clickable, including empty space around the button. This might confuse users.

**Better UX:** Only toggle when clicking task text, not the container - `<li>`.

We can only add event listeners to DOM elements. That means the task text must be inside its own element.  

**The approach:**
1. Wrap task text in a `<span>` element
2. Move toggle listener from `<li>` to `<span>`
3. Keep delete button separate

**Previous structure:**
```
<li>
  Task text here
  <button class="delete-btn">Delete</button>
</li>
```


**New structure:**
```
<li>
  <span class="task-text">Task text here</span>
  <button class="delete-btn">Delete</button>
</li>
```

**Your task:**
1. Instead of setting the text to `<li>` we need to create a new `<span>` element for task text
2. Move the click listener from li to the span element
3. Append span as child `<li>` (before the button)

**Success check:**
- Clicking task text toggles completion
- Clicking delete button only deletes
- Clicking empty space in `<li>` does nothing

**➜ Understanding check:** Why is wrapping text in a span better than keeping the listener on the `<li>`?

---

## TASK 5: Add Visual Feedback (10 min)

**Goal:** Make it obvious tasks are clickable.

**For task text span:**
- Cursor: pointer (shows hand cursor)
- Optional: Add hover effect (slight color change or underline)

**Success check:**
- Task text shows pointer cursor on hover
- Completion toggle has smooth animation
- Clear visual feedback that text is interactive

---

## SUCCESS CHECKS - ALL MUST PASS

✅ Clicking task text toggles completed state  
✅ Completed tasks show strikethrough  
✅ Clicking again removes strikethrough  
✅ Delete button does NOT toggle when clicked  
✅ Delete button removes task without affecting complete state  
✅ Task text shows pointer cursor  
✅ Can toggle and delete tasks in any combination  
✅ Visual feedback is clear and smooth

---

## EXIT TICKET

1. **In your own words:** What does `classList.toggle()` do?
2. **Explain:** Why do we need `event.stopPropagation()` in the delete handler?
3. **Predict:** If you toggle a task complete, then refresh the page, will it still be marked complete? Why or why not?

---

## 🎯 WHAT YOU ACCOMPLISHED

You've implemented state management with CSS classes and handled complex event interactions. The app is now fully functional - users can add, complete, and delete tasks. This is a complete todo app! The only limitation: tasks disappear on refresh (you'll fix that tomorrow with localStorage).

**Tomorrow (Day 3):** Make tasks persist between sessions using localStorage and learn the data-driven UI pattern.

---

## 🎉 END OF DAY 2 MILESTONE

**You built a working interactive app in one day!**

Test everything:
- Add several tasks
- Mark some complete
- Delete some tasks
- Toggle tasks multiple times
- Try edge cases (empty input, very long text)

**Commit your work:**
```bash
git add .
git commit -m "Add delete and complete toggle functionality"
git push
```

**Refresh your GitHub Pages site** - your deployed app now has full interactivity!

---

## IF YOU FINISH EARLY

1. Add a "complete all" button that toggles all tasks to completed
2. Add a counter showing "X tasks completed"
3. Try double-click to toggle instead of single-click
4. Experiment: What happens if you add the `completed` class in HTML before JavaScript runs?
5. Add a different visual style for completed tasks (background color change, different icon)