# HR Workflow Designer

A functional prototype for a visual HR workflow designer using React, React Flow, and Logic.

## Architecture

The project follows a modular React architecture with a clear separation of concerns:

- **Canvas Logic (`src/components/WorkflowDesigner.tsx`)**: Manages the core React Flow instance, drag-and-drop logic, and global event handlers.
- **Node Components (`src/nodes/`)**: Custom components for each node type (Start, Task, Approval, etc.) that define how nodes look on the canvas.
- **Configuration Forms (`src/components/forms/`)**: Isolated form components for editing the properties of specific node types. This makes adding new node types easy and scalable.
- **State Management (`src/store/useStore.ts`)**: Uses `zustand` to manage global selection state, avoiding prop drilling between the canvas and the properties panel.
- **Mock Service (`src/api/mockApi.ts`)**: Encapsulates all "backend" logic, including fetching automation actions and running the simulation traversal.

## How to Run

1. **Install Dependencies**
    ```
   npm install
   ```

2. **Start Development Server**
   ```bash
   npm run dev
   ```
   Open [http://localhost:5173](http://localhost:5173) in your browser.

3. **Build for Production**
  
   npm run build
   ```

## Design Decisions

- **React Flow**: Chosen for its robust drag-and-drop capabilities and customization API. It handles the heavy lifting of graph rendering.
- **Zustand**: Selected for state management over Context/Redux because it provides a simple, hook-based API that is perfect for shared transient UI state like "selected node".
- **Tailwind CSS**: Used for styling to ensure consistency and rapid development. Custom CSS variables were added for a "premium" theme layer on top of utilities.
- **Type Safety**: TypeScript was used strictly to ensure that node data structures (which can be complex) are predictable across the application.
- **Simulation**: Implemented as a client-side topological sort/traversal. This demonstrates how a backend would technically execute the flow without needing a real server for this prototype.

## Completed vs. Future Improvements

### What is Completed 
- **Visual Canvas**: Drag-and-drop node placement and connections.
- **Custom Nodes**: 5 distinct node types with unique visual identifiers.
- **Properties Panel**: Dynamic editing forms that update node data in real-time.
- **Mock API Integration**: Simulates fetching system actions (e.g., "Send Email").
- **Workflow Simulation**: A working engine that traverses the graph, checks for cycles, and produces an execution log.
- **Responsive Layout**: Sidebar, Canvas, and Properties panel layout.

### What I Would Add with More Time 
- **Undo/Redo History**: Critical for a complex design tool.
- **Copy/Paste Support**: To duplicate sub-process structures.
- **Vertical Auto-Layout**: Using `dagre` or `elkjs` to automatically organize messy graphs.
- **Complex Validation**: More robust verification (e.g., checking for unreachable nodes, specific business rule constraints).
- **Backend Persistence**: Saving workflows to a real database (PostgreSQL/Mongo).
- **Custom Handles**: Allowing multiple output paths (e.g., "Approved" vs "Rejected" paths for the Approval Node).

