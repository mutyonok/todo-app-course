# DAY 3 HOUR 4: LOAD ON PAGE RELOAD

## HOUR GOAL

Right now your tasks save to localStorage, but when you refresh the page, they disappear from view. 
The data is *there* in storage—you can see it in DevTools—but nothing reads and displays it when the page loads.

This hour you'll fix this: you'll write a `loadTasks()` function that runs automatically when the page opens, retrieves the saved tasks from localStorage, puts them back into your `tasks` array, and renders them to the screen.

**The flow:**
1. Page loads → `loadTasks()` runs immediately
2. Check localStorage for saved tasks
3. If found, parse the JSON string back into an array
4. Put that array into your `tasks` variable
5. Call `renderTasks()` to display them

**New concepts you'll learn:**
- Handling `null` values (when localStorage is empty)
- Default values with the OR operator (`||`)
- What "truthy" and "falsy" mean in JavaScript
- Page lifecycle: code that runs on load vs. on click

---

## Key Concept: Handling Missing Data

When you try to get something from localStorage that doesn't exist, you get `null` back. You can't parse `null` as JSON—it'll crash.

**Null check example:**
```javascript
// Getting user preferences that might not exist yet
let savedTheme = localStorage.getItem('theme');
if (savedTheme === null) {
    savedTheme = 'light'; // default value
}
```

**The OR operator shortcut:**
```javascript
// Same thing as previous example, but shorter
let savedTheme = localStorage.getItem('theme') || 'light';
// If left side - localStorage.getItem('theme') - is falsy (null, undefined, empty string), use right side - 'light'
```

**Truthy vs. Falsy**:
- **Falsy values:** `false`, `0` (zero Number), `''` (empty string), `null`, `undefined`, `NaN`
- **Truthy values:** Everything else (including `'0'` (String with 0 in it), `[]`, `{}`)

```javascript
if ('hello') { } // goes into if - strings with content are truthy
if ('') { }      // doesn't go into if - empty string is falsy
if (null) { }    // doesn't go into if - null is falsy
if ([]) { }      // goes into if - empty arrays are truthy
```

This matters because JavaScript's logical operators return the actual values, not just true/false:
```javascript
let x = null || 'default';        // x = 'default'
let y = 'saved value' || 'default'; // y = 'saved value'
```

---

## The Process

**Think through the logic before coding:**

1. When should this run? → As soon as page loads (not on button click)
2. What if there's no saved data? → Use an empty array as default
3. After loading data, what next? → Render it to screen

**The pattern:**
```
Get JSON string from storage → Parse JSON to array → Store in tasks variable → Render
```

---

## Tasks

### 1. Create the loadTasks function (15 min)

Write a function that:
- Gets the 'tasks' item from localStorage (use your local storage key)
- If localStorage returns `null` - default value is empty array
- Otherwise - Parses the JSON string and stores result in your tasks array
- Calls `renderTasks()` to display them

**Success check:**
- Function exists
- Open browser and create some tasks
- Refresh the page - tasks should disappear from page
- Open Dev Console and call your new function
- Tasks should appear on page

---

### 2. Call loadTasks when page loads (5 min)

Add one line at the bottom of your JavaScript file (outside any function) that calls `loadTasks()`.

**Why outside a function?** Code at the top level of your JS file runs immediately when the script loads. Code *inside* functions only runs when you call them.

**Why at the bottom of the file?** JavaScript reads your file from top to bottom. It's a rule of thumb: first define a function, only then call it. 
This makes code readable and error-prone.

**Success check:**
- Refresh the page → saved tasks appear
- Open DevTools Application tab → localStorage still has your data
- Delete all localStorage data → page loads without crashing, shows empty list

---

### 3. Test the persistence cycle (10 min)

**Systematic testing:**

1. Clear localStorage completely (Application tab → Clear all)
2. Refresh page → should show empty list (not crash)
3. Add 3 tasks
4. Refresh → all 3 should reappear
5. Mark one complete
6. Refresh → completion state should persist
7. Delete one task
8. Refresh → deletion should persist
9. Add a task, then immediately refresh → should appear

**If anything fails:** Use console.log to debug:
```javascript
console.log('Loading tasks...');
console.log('Retrieved from storage:', localStorage.getItem('tasks'));
console.log('Parsed tasks array:', tasks);
```

---

### 4. Optional: Add error handling (10 min)

What if localStorage contains invalid JSON? Your app would crash. Wrap the JSON.parse in a try-catch:

**Try-catch example (not from project):**
```javascript
const possiblyBadData = localStorage.getItem('data');
let result;
try {
    result = JSON.parse(possiblyBadData);
} catch (error) {
    console.log('Parsing failed:', error);
    // Use default value instead
    result = [];
}
```

Apply this pattern to your `loadTasks()` function. If parsing fails, default to an empty array.

---

## Understanding Checks

Answer these before moving on:

1. **Why do we need default value when reading from localStorage?**
    - What happens on the very first page load before any tasks exist?

2. **Trace the full cycle:**
    - User adds task → what happens to the data?
    - User refreshes page → what happens to the data?
    - Draw or write out each step

3. **What would break if you forgot to call `renderTasks()` at the end of `loadTasks()`?**

---

## Complete Data Flow

**Now your app has this complete cycle:**

1. **Page loads** → `loadTasks()` runs → retrieves from localStorage → displays tasks
2. **User adds task** → object pushed to `tasks` array → `saveTasks()` → `renderTasks()`
3. **User deletes task** → `tasks.filter()` removes it → `saveTasks()` → `renderTasks()`
4. **User toggles complete** → find task in array, flip `.completed` → `saveTasks()` → `renderTasks()`
5. **Page refreshes** → back to step 1

**This pattern (data → save → render) is how React, Vue, and all modern frameworks work.** You're learning the fundamental concept behind state management.

---

## Success Criteria

✅ `loadTasks()` function exists and handles null/empty storage  
✅ Function is called when page loads (not on button click)  
✅ Tasks persist across page refreshes  
✅ Completed states persist  
✅ App doesn't crash when localStorage is empty  
✅ You can explain the full data cycle from add → save → refresh → load

**Next:** Day 4 will pause new features to ensure you deeply understand what you've built. You'll refactor, add comments, and test your knowledge through active recall.