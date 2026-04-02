# Assignment 1 — Vue Setup & Directives

## Overview

You will build a small **Movie Watchlist** app from scratch using Vue + Vite.  

The app lets a user manage a list of movies they want to watch: add them, mark them as watched, filter the list, and see some basic stats.

---

## Setup

1. Create a new Vue project:
   ```bash
   npm create vue@latest
   ```
   - Project name: `movie-watchlist`
   - All optional features: **No**

2. Install dependencies and run the dev server:
   ```bash
   cd movie-watchlist
   npm install
   npm run dev
   ```

3. Clear `src/App.vue` and start from a blank component.

> The only file you need to edit is `src/App.vue`.  
> Do not install any UI libraries. Plain HTML + Vue + your own CSS only.

---

## Requirements

### Part 1 — Add Movies `[ref, v-model, @click]`

- There is a text input and an "Add" button
- The user types a movie title and clicks Add (or presses Enter)
- The movie is added to the list with `watched: false`
- After adding, the input clears automatically
- If the input is empty or whitespace only, nothing is added

---

### Part 2 — Display the List `[v-for, v-if]`

- All movies are displayed in a list
- Each item shows the movie title
- If the list is empty, show a message: *"No movies yet. Add one above!"*
- Each movie has two buttons: **"Mark watched"** and **"Remove"**

---

### Part 3 — Mark as Watched `[v-bind, v-if / v-else]`

- Clicking "Mark watched" toggles the `watched` state
- When a movie is watched:
  - Its title is displayed with a strikethrough
  - The button label changes to **"Unmark"**
- When a movie is unwatched, it looks normal and the button says **"Mark watched"**

---

### Part 4 — Stats `[computed]`

Display the following below the list, always up to date:

- Total movies in the list
- How many are watched
- How many are left to watch

Example: `3 movies — 1 watched — 2 remaining`

---

### Part 5 — Filter `[v-model, computed, v-for]`

Add three filter buttons: **All**, **Watched**, **Unwatched**

- Clicking a filter shows only the matching movies
- The active filter button looks visually different from the others (a CSS class is enough)
- The stats from Part 4 always reflect the **full list**, not the filtered view

---

## Checklist

Before submitting, go through this list yourself:

- [ ] Project created with `npm create vue@latest`, runs with `npm run dev`
- [ ] Can add a movie by typing and pressing Enter or clicking Add
- [ ] Empty input is rejected (nothing added)
- [ ] Input clears after a successful add
- [ ] Empty list shows the placeholder message
- [ ] Each movie can be marked watched / unmarked
- [ ] Watched movies have strikethrough title and different button label
- [ ] Remove button deletes the movie from the list
- [ ] Stats are correct at all times
- [ ] Filter buttons work correctly
- [ ] Active filter is visually distinguishable
- [ ] Stats always count the full list, not the filtered view
- [ ] No errors in the browser console

---

## What to Submit

**Don't forget to add node_modules in .gitignore**

```
movie-watchlist/
├── src/
│   └── App.vue     ← the only file that matters
├── package.json
└── ...
```

---

## Hints

- You don't need anything beyond what was covered in the lecture.
- The entire app fits in one `App.vue` file - don't over-engineer it.
- `array.filter()` and `array.push()` work normally on reactive arrays — just access them via `.value`.
- For the active filter button, look at how `:class` binding works with an object: `:class="{ active: filter === 'all' }"`.
- If something doesn't update when you expect it to, double-check you're using `.value` when reading or writing in `<script setup>`.

---

## Grading

| Part | Points |
|------|--------|
| 1 — Add movies | 20 |
| 2 — Display list | 20 |
| 3 — Mark watched | 20 |
| 4 — Stats | 20 |
| 5 — Filter | 20 |
| **Total** | **100** |
