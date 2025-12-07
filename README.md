# HR Workflow Designer

A functional prototype for a visual HR workflow designer using React, React Flow, and Logic.

## Features

- **Visual Workflow Canvas**: Drag-and-drop interface to design processes.
- **Custom Node Types**: Start, Task, Approval, Automated Action, and End nodes.
- **Configuration Panels**: specialized forms for each node type.
- **Mock API**: Simulates backend interactions and automations.
- **Workflow Simulator**: Validates and "executes" the designed workflow.

## Tech Stack

- React 18
- React Flow (Visual Graph)
- Tailwind CSS (Styling)
- Lucide React (Icons)
- Zustand (State Management)

## Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Run the development server:
   ```bash
   npm run dev
   ```

## Architecture

- `src/components/WorkflowDesigner.tsx`: Main canvas orchestrator.
- `src/nodes/`: Custom React Flow node components.
- `src/components/forms/`: Node property editors.
- `src/api/mockApi.ts`: Simulates backend services.
- `src/store/useStore.ts`: Global application state.

## Simulation & Testing

Use the "Play" button in the bottom left to open the Simulation Panel. This runs a client-side traversal of the graph to verify connectivity and structure (e.g., detecting cycles or missing start nodes).
