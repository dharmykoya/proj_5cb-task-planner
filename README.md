# Task Planner

A simple, static frontend task planning application that allows users to create, organize, and manage their daily tasks. Built entirely with HTML, CSS, and vanilla JavaScript without any backend or database dependencies. All data is stored locally in the browser using localStorage, making it a lightweight and privacy-friendly solution for personal task management.

## Project Overview

Task Planner is a client-side-only web application designed for personal productivity. It requires no installation, no server, and no account — just open it in a browser and start managing your tasks.

## Features

- **Task Creation** — Add new tasks with a title and optional description
- **Task Editing** — Update task details inline
- **Task Completion** — Mark tasks as done with a single click
- **Task Deletion** — Remove tasks individually
- **Export / Import** — Export your task list to JSON and import it back on any session

## Architecture

The application is built with plain web technologies:

- **HTML** — Structure and markup
- **CSS** — Styling and layout
- **JavaScript (Vanilla)** — Application logic and DOM manipulation
- **localStorage** — Persistent client-side storage (no backend required)

The codebase is organized into focused modules:

| File | Responsibility |
|---|---|
| `index.html` | Application shell and markup |
| `styles.css` | Visual styles and responsive layout |
| `app.js` | Application bootstrap and event wiring |
| `storage.js` | localStorage read/write helpers |
| `export-import.js` | JSON export and import logic |
| `animations.js` | UI transition and animation utilities |
| `performance.js` | Performance monitoring helpers |

## localStorage Schema

All tasks are stored under a single key:

**Key:** `taskPlannerTasks_v1`

**Value:** JSON array of task objects

```json
[
  {
    "id": "string (UUID)",
    "title": "string",
    "description": "string",
    "completed": false,
    "createdAt": "ISO 8601 timestamp",
    "updatedAt": "ISO 8601 timestamp"
  }
]
```

## Setup Instructions

No build process or package installation is required.

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd proj_5cb-task-planner
   ```

2. Serve the files with any static file server. Examples:
   ```bash
   # Python 3
   python3 -m http.server 8080

   # Node.js (npx)
   npx serve .
   ```

3. Open `http://localhost:8080` in your browser.

Alternatively, open `index.html` directly in a browser (file:// protocol works for most features).

## Deployment to GitHub Pages

1. Push the repository to GitHub.
2. Go to **Settings → Pages** in your repository.
3. Set the source branch to `main` and the folder to `/ (root)`.
4. GitHub Pages will publish the site automatically. No build step needed.

## Browser Compatibility

| Browser | Minimum Version |
|---|---|
| Chrome | 90+ |
| Firefox | 88+ |
| Safari | 14+ |
| Edge | 90+ |

Older browsers may work but are not tested or supported.

## Privacy & Security

- All task data is stored exclusively in your browser's localStorage.
- No data is sent to any server or third party.
- No analytics, tracking, or network requests of any kind.
- Clearing browser data will erase all stored tasks.

## File Structure

```
proj_5cb-task-planner/
├── index.html          # Main HTML entry point
├── styles.css          # Application styles
├── app.js              # Core application logic
├── storage.js          # localStorage utilities
├── export-import.js    # Export and import functionality
├── animations.js       # UI animation helpers
├── performance.js      # Performance utilities
├── .gitignore          # Version control exclusions
└── README.md           # This file
```

## Development Guidelines

- Keep all logic in the relevant module file; avoid putting business logic in `index.html`.
- Use plain ES6+ JavaScript — no frameworks or transpilers.
- Store all persistent state via `storage.js` helpers; never write to localStorage directly from other modules.
- Keep CSS scoped to logical component sections and avoid deep specificity chains.
- Test in all supported browsers before submitting changes.

## Known Limitations

- **localStorage quota** — Browsers typically limit localStorage to ~5 MB per origin. Very large task lists may hit this limit.
- **Single-device** — Data is local to the browser and device. There is no sync across devices or browsers.
- **No offline SW** — The app works offline by nature (no network calls), but there is no Service Worker for PWA installation.
