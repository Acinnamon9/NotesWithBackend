# Architecture & Codebase Overview

This document provides a technical deep-dive into the "Sticky Notes" application. It is designed to help new developers understand how the parts fit together.

## 🛠 Tech Stack

- **Frontend**: React (Vite)
- **Language**: JavaScript (ES6+)
- **Backend / Database**: Appwrite (BaaS)
- **Styling**: Plain CSS (with CSS Variables for theming)

## 📂 Project Structure `src/`

```text
src/
├── appwrite/       # Backend configuration and service wrappers
│   ├── config.js   # Env var imports and client setup
│   └── databases.js# Database collection references (Notes)
├── assets/         # Static assets (images, fonts)
├── components/     # Reusable UI components
│   ├── NoteCard.jsx    # Individual sticky note logic
│   ├── Color.jsx       # Color picker component
│   └── ...
├── context/        # React Context for global state
│   └── NotesContext.jsx # Manages notes list and loading state
├── icons/          # SVG functional components
├── pages/          # Full page layouts
├── utils.js        # Helper functions (positioning, auto-grow)
├── App.jsx         # Main router/wrapper
└── main.jsx        # Entry point
```

## 🔑 Key Concepts

### 1. State Management (`NotesContext`)

We use React Context to share the state of notes across the application.

- **File**: `src/context/NotesContext.jsx`
- **Data**: `notes` (Array of objects), `selectedNote` (Currently active note).
- **Initialization**: On load, `init()` calls `db.notes.list()` to fetch existing notes from Appwrite.
- **Loading State**: Displays a `<Spinner />` while fetching data.

### 2. Backend Integration (Appwrite)

All backend logic is abstracted in `src/appwrite/databases.js`.

- **Collections**: We target a specific Notes collection defined in `.env.local`.
- **Operations**: Standard CRUD operations (List, Create, Update, Delete) are handled directly via the Appwrite SDK.

### 3. Note Mechanics (Drag & Drop)

The "sticky" behavior is calculated manually in `src/utils.js`.

- **`setNewOffset`**: Calculates the new (x, y) position of a note based on mouse movement.
- **`setZIndex`**: brings the currently clicked note to the front (`z-index: 999`).
- **Auto-Save**: Changes to text or position trigger updates to the backend. We often use debouncing (or saving on blur/mouse up) to avoid spamming the API.

## 📝 Data Model

A typical **Note** document in Appwrite looks like this:

```json
{
  "$id": "unique_string_id",
  "body": "JSON string or simple text content",
  "colors": "JSON stringify object {id, colorHeader, colorBody, text}",
  "position": "JSON stringify object {x, y}"
}
```

_Note: Some fields like `position` and `colors` are stored as stringified JSON to allow flexibility._

## 🚀 Common Workflows

### Setup

Ensure you have `.env.local` populated with your Appwrite endpoint and IDs.

### Adding a Feature

1.  **UI**: Create component in `src/components`.
2.  **Logic**: If it affects global state, update `NotesContext`.
3.  **Persistance**: If data needs saving, add method to `src/appwrite/databases.js`.
