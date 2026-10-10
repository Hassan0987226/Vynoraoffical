# Vynora

Vynora is a media discovery and download dashboard inspired by premium video platforms, designed for local development and extensibility.

## Stack

- Frontend: React + Vite
- Backend: FastAPI
- Database: PostgreSQL
- Auth: Google Sign-In + JWT sessions
- Media: HTML5 video playback, upload support, and direct media validation

## Prerequisites

- Windows 10/11
- Node.js 18+
- Python 3.11+
- PostgreSQL running locally

## Environment setup

### 1) Root environment

Create a `.env` file in the project root, with PostgreSQL values:

```env
POSTGRES_USER=vynora
POSTGRES_PASSWORD=vynora
POSTGRES_DB=vynora
```

### 2) Backend environment

Create `backend/.env` with:

```env
DATABASE_URL=postgresql+psycopg://vynora:vynora@localhost:5432/vynora
JWT_SECRET_KEY=change_this_to_a_strong_32_character_secret_value
GOOGLE_CLIENT_ID=
COOKIE_SECURE=false
CORS_ORIGINS=http://localhost:5173,http://127.0.0.1:5173
MEDIA_STORAGE_DIR=C:/Users/Hassan/Desktop/ZentroMedia/backend/media
MAX_UPLOAD_BYTES=524288000
MAX_DOWNLOAD_BYTES=2147483648
APP_ENV=development
```

## Install dependencies

### Backend

```powershell
cd "C:\Users\Hassan\Desktop\ZentroMedia\backend"
& "C:\Users\Hassan\AppData\Local\Programs\Python\Python314\python.exe" -m pip install -r requirements.txt
```

### Frontend

```powershell
& "C:\Program Files\nodejs\npm.cmd" --prefix "C:\Users\Hassan\Desktop\ZentroMedia\frontend" install
```

## Run locally

### Backend

```powershell
cd "C:\Users\Hassan\Desktop\ZentroMedia\backend"
& "C:\Users\Hassan\AppData\Local\Programs\Python\Python314\python.exe" -m uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Frontend

```powershell
& "C:\Program Files\nodejs\npm.cmd" --prefix "C:\Users\Hassan\Desktop\ZentroMedia\frontend" run dev
```

Then open:

- http://localhost:5173
- http://localhost:8000/api/health

## Notes

- Google Sign-In needs a valid `GOOGLE_CLIENT_ID` to work.
- The project includes demo UI flows and local previews for the dashboard UI.
- Protected API endpoints expect a valid JWT session cookie.
- Download validation blocks private/internal network destinations to reduce SSRF risk.
