# project2-group6
Ray, Faith, Suryash, and George

## Pitch
### Overview


This project delivers a collaborative, web-based writing environment tailored specifically for journalists and editors, streamlining the process of composing, sourcing, and publishing stories. The application supports two primary user roles: writers and editors. Writers can create and manage documents from their dashboard, while editors are invited collaborators with read-only access and commenting capabilities.

The platform integrates a built-in research and citation system. Users can search or paste links directly into the sidebar, automatically generating editable citations categorized by source type (e.g., website, book, interview). An embedded browser allows in-app viewing of non-commercial sources, while commercial links open externally. Writers can organize sources, quotes, and media efficiently within each document.

The rich text editor includes formatting tools, image insertion, commenting, and document sharing. A real-time collaboration panel displays active users, roles, and access modes. Only document owners can edit and publish content, with direct publishing supported via WordPress integration.

Overall, the app centralizes writing, research, collaboration, and publishing into a single workflow, reducing friction for newsroom teams and enabling more organized, transparent, and efficient content production.

## Key Features Summary
Role-based access control (writer vs editor)
Built-in research and browsing tools
Automatic citation generation and editing
Rich text editing with formatting tools
Commenting and collaboration system
Real-time document access tracking
WordPress publishing integration


## Class Diagram
[![Class Diagram](ClassDiagramUpdated.png)]


## Use Case Diagram
[Visit the Mermaid Diagram here](https://mermaid.ink/img/pako:eNptUktOwzAUvIr1Vq6UlsTNx82CTUFsioQACQnCwk0eTdQ6jpwEEaoeghOw4YAcASdRU6R0Zb8Zz7yx_fYQqwQhhI0WRUpW91FOiIgrpR36EsHv99cPedJZhTqC18lAsoG8TjJT92RLl_W6t3poygplDxISK1lQulSFVCVOJke40iLeUvrYLuRB1TrG8sQW9ZrSu3q9y0rjZ9o0Jy5OsVUu28VwzQ4vbrSQUujTGTTZKF2heMcu52CNedJv-puS6fSySzgCu3wj1OQay9sg_1B2Vs_O6HuszToCO1OwzOdkCYSVrtECiVqKtoR9ezqCKkWJEYRmmwi9jSDKD0ZTiPxZKXmUaVVvUgjfxK40VV0kosKrTJi_kgOqzbugXqo6ryAMfLszgXAPHxAyx59x13ED2-U-9x3OLWgg9PjM9ZkbuJzNuTNnrnew4LPra884Y9z1Ai-w7cBb8IUF2E3LbT9y3eQd_gAcusvy?type=png)

<img width="300" height="800" alt="Project2-Group6-Diagram" src="https://github.com/user-attachments/assets/e51b1dac-09a9-43d1-975e-07527e1ec1f2" />

# Sequence Diagrams
## Managing Commenting on Documents and Publishing:
<img width="5370" height="5140" alt="Writer to Website-2026-04-09-144210" src="https://github.com/user-attachments/assets/16055f12-e93e-4e28-be79-755bbb224c46" />

## Share A Document between a Writer and Editor:
<img width="857" height="847" alt="Screenshot 2026-04-28 at 8 46 33 PM" src="https://github.com/user-attachments/assets/13ddb05e-2ba1-4ddf-af7e-0d0e568fc907" />

## Use In-App Browser with Citation Formatter:
<img width="1006" height="691" alt="Screenshot 2026-04-28 at 9 31 34 PM" src="https://github.com/user-attachments/assets/fc94e53b-6793-4efd-a5f1-06fced85116c" />

## State Diagram 
![State Diagram](state-diagram.png)


## Technologies

### Frontend

- React 19
- TypeScript
- Vite
- React Router
- Yoopta Editor and Yoopta UI
- Slate
- Yjs and `y-websocket` for collaboration support
- `lucide-react` and `react-icons` for icons

### Backend and development tools

- Node.js
- Express 5
- CORS
- Nodemon for backend development
- Vitest for automated tests
- npm workspaces are not used; the root, `backend`, and `word-processor`
  directories each have their own dependency manifest

The API stores local account and document data in
[`backend/accounts.json`](./backend/accounts.json). This is suitable for local
development only and is not a production database.

## Prerequisites

- Node.js 20 or newer
- npm
- A modern web browser

## Installation

Clone the repository and install dependencies for each Node.js project:

```bash
git clone https://github.com/faithowino/Word-Processor.git
cd Word-Processor

npm install
cd backend
npm install
cd ../word-processor
npm install
cd ..
```

## Running the application

From the repository root, start the API and frontend together:

```bash
npm run dev
```

This starts:

- The Express API at <http://localhost:3001>
- The Vite development server at <http://localhost:5173>

Open <http://localhost:5173> in a browser. The frontend proxies API requests to
the backend, so both processes must be running. The backend health endpoint is
available at <http://localhost:3001/api/health>.

To run the processes separately, use two terminals:

```bash
# Terminal 1: API
cd backend
npm run dev
```

```bash
# Terminal 2: frontend
cd word-processor
npm run dev
```

The frontend Vite server listens on all network interfaces. To access it from
another device on the same network, use the host machine's IP address with port
5173.

## Environment variables

The frontend can be configured with an optional
[`word-processor/.env`](./word-processor/.env) file. Start with the example:

```bash
cp word-processor/.env.example word-processor/.env
```

Available variables:

| Variable | Purpose | Default |
| --- | --- | --- |
| `VITE_API_BASE_URL` | Absolute base URL for API requests | Empty; uses the Vite proxy |
| `VITE_COLLAB_SERVER_URL` | Optional Yoopta-compatible WebSocket server | Empty; realtime WebSocket transport disabled |

The application currently uses the Express API for authentication, documents,
comments, presence, and WordPress publishing. The optional collaboration
WebSocket URL is only needed when a compatible realtime collaboration server is
available.

## Testing and validation

Run the root Vitest suite:

```bash
npm test
```

Run the frontend lint, type-check/build, or production preview:

```bash
cd word-processor
npm run lint
npm run build
npm run preview
```

The production preview is served by Vite after a successful build.

## Project structure

```text
.
├── backend/          Express API, authentication, documents, and local data
├── tests/             Vitest tests for backend and application behavior
└── word-processor/   React/TypeScript frontend and Vite configuration
```

Additional design and feature documentation is available in
[`DOCUMENTATION.md`](./DOCUMENTATION.md), [`RESOURCES.md`](./RESOURCES.md), and
the diagrams in the repository root.

## Notes

- Local JSON files contain application state and may change while the app runs.
- Do not use the included JSON storage or development credentials for production.
- WordPress publishing requires a WordPress site URL, username, and WordPress
  Application Password.



