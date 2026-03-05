# TaxFlow GST — Smart Compliance Platform

Full-stack Indian GST compliance management system.

## Project Structure

```
taxflow-gst/
├── frontend/          # Vanilla JS frontend (ready to migrate to React)
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/       # Reusable UI: Badge, Table, Modal, StatCard
│   │   │   ├── layout/       # Sidebar, Topbar, Layout
│   │   │   └── modals/       # All modal dialogs
│   │   ├── pages/            # One JS file per page/module
│   │   ├── api/              # All fetch() calls to FastAPI backend
│   │   ├── utils/            # Formatters, validators, date helpers
│   │   └── styles/           # CSS split by concern
│   └── public/
│       └── index.html        # Shell HTML (no inline CSS/JS)
│
├── backend/           # FastAPI (Python) backend
│   ├── app/
│   │   ├── routers/   # One file per module (gstr1, recon, etc.)
│   │   ├── models/    # SQLAlchemy ORM models
│   │   ├── schemas/   # Pydantic request/response schemas
│   │   ├── services/  # Business logic (recon engine, import, etc.)
│   │   └── core/      # Config, DB session, auth
│   ├── alembic/       # Database migrations
│   └── tests/
│
└── docker-compose.yml
```

## Quick Start

### Frontend (no build step needed)
```bash
cd frontend
npx serve public   # or just open public/index.html
```

### Backend
```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
alembic upgrade head
uvicorn app.main:app --reload --port 8000
```

### Full Stack (Docker)
```bash
docker-compose up --build
# Frontend: http://localhost:3000
# API:      http://localhost:8000
# API Docs: http://localhost:8000/docs
```
