# Sticky Notes React

A modern, sticky notes application built with React, Vite, and Appwrite. Features a dynamic drag-and-drop interface, auto-saving capability, and real-time backend synchronization.

![Notes Screenshots](https://github.com/user-attachments/assets/aef7e95a-c900-43d8-879d-f23fbe40f60c)

## Features

- **📝 Create & Edit Notes**: Easily add new sticky notes and edit their content seamlessly.
- **💾 Auto-Saving**: Content changes are automatically saved to the Appwrite backend safely and securely.
- **🖱️ Drag & Drop**: Organize your workspace by dragging notes anywhere on the screen. The position is persisted.
- **🎨 Dynamic Colors**: Each note gets assigned coordinated header and body colors for a polished look.
- **🗑️ Delete Notes**: intuitive controls to remove notes you no longer need.
- **⚡ Fast & Reactive**: Built with Vite for lightning-fast development and production performance.

## Tech Stack

- **Frontend**: [React](https://react.dev/)
- **Build Tool**: [Vite](https://vitejs.dev/)
- **Backend**: [Appwrite](https://appwrite.io/) (Database & API)
- **Icons**: Custom SVG Icons

## Getting Started

Follow these steps to get the application running on your local machine.

### Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- An [Appwrite](https://appwrite.io/) account and project

### Installation

1.  **Clone the repository**

    ```bash
    git clone <repository-url>
    cd NotesWithBackend
    ```

2.  **Install dependencies**

    ```bash
    npm install
    ```

3.  **Environment Configuration**
    Create a `.env.local` file in the root directory. You can use `.env.example` as a reference. Add your Appwrite configuration keys:

    ```properties
    VITE_ENDPOINT="https://cloud.appwrite.io/v1"
    VITE_PROJECT_ID="your_project_id"
    VITE_DATABASE_ID="your_database_id"
    VITE_COLLECTION_NOTES_ID="your_collection_id"
    ```

4.  **Run the application**

    ```bash
    npm run dev
    ```

    Open `http://localhost:5173` in your browser to view the app.

## Project Structure

- `src/appwrite`: Appwrite configuration and service setup.
- `src/components`: Reusable UI components (NoteCard, Controls, etc.).
- `src/context`: React Context for state management.
- `src/pages`: Main application pages.
- `src/utils.js`: Utility functions for logic like auto-grow and positioning.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
