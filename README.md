# DTErp Open Beta 0.7

Enterprise-style ERP starter platform built with React + Vite frontend and Node.js + Express backend.

## Overview

This version provides a polished ERP experience with:

- Role-based access control and field-level RBAC sanitization
- Admin-configurable settings and logo branding
- Inventory, customers, suppliers, employees, sales, and purchases modules
- Sidebar navigation with permission-aware links
- Dashboard overview with operational metrics
- Global command bar (`Ctrl+K` / `Cmd+K`) for fast app navigation
- Installer packaging for backend server and frontend app bundles

## Repository Structure

- `backend/` - Express + TypeScript API, JSON persistence in `backend/data/db.json`
- `frontend/` - React + TypeScript + Vite UI using Material UI components
- `scripts/` - Installer packaging scripts for backend and frontend
- `dist-installers/` - Generated installer bundles after running package scripts

## Getting Started

### 1. Install dependencies

From the workspace root:

```bash
npm install
```

### 2. Run development mode

```bash
npm run dev
```

This starts both backend and frontend concurrently.

- Frontend: `http://localhost:5173`
- Backend: `http://localhost:4000`

### 3. Default login

- Username: `admin@sys`
- Password: `admin`

> The default admin account is also stored in `backend/data/db.json`.

## Build

Build both workspaces from the root:

```bash
npm run build
```

Then build each workspace individually if needed:

```bash
npm --workspace backend run build
npm --workspace frontend run build
```

## Installer Packaging

After building the backend and frontend, generate installer bundles:

```bash
npm run package:backend-installer
npm run package:frontend-installer
```

Installer bundles are created in:

- `dist-installers/backend`
- `dist-installers/frontend`

Each bundle includes a Windows `.bat` and PowerShell `.ps1` install script plus README guidance.

## Features

### Backend

- `POST /auth/login` - login and return user permissions
- Resource guards with permission enforcement for products, customers, suppliers, employees, sales, and purchases
- Admin-only settings endpoint
- Field-level response sanitization middleware for sensitive data
- Immutable-style JSON persistence via `backend/data/db.json`

### Frontend

- Role-aware sidebar navigation
- Protected routes with `Unauthorized` fallback
- Editable CRUD dialogs for core entities
- Command bar search overlay for fast navigation
- Dashboard overview and summary cards

## Development Notes

- The backend uses a custom JSON store in `backend/data/db.json`.
- Frontend requests attach the current user via `x-current-user` header.
- Permissions are evaluated in the backend and frontend for stronger route and data access control.

## Recommended Next Improvements

- Add persistence to a real database
- Add invoice OCR and AI prompt orchestration hooks
- Add workflow automation engine and event triggers
- Add bulk inline spreadsheet editing and advanced filter state machine
- Add multi-warehouse, BOM management, and payroll formula processing

## License

This project is provided as-is for development and demonstration purposes.
