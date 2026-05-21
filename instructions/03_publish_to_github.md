# 03 - Publish to GitHub and Host

## Important hosting note

`GitHub Pages` hosts only static files, not Flask/Python backend.

So for a live full dashboard:

1. Push this project to GitHub.
2. Deploy Flask backend to a Python host (Render, Railway, Fly.io, VPS).
3. (Optional) Host only frontend on GitHub Pages and point it to deployed API.

## 1) Create GitHub repository

Create a new empty repo in GitHub web UI, e.g. `forest-dashboard`.

## 2) Initialize and push local project

Run in PowerShell:

```powershell
cd "D:\alert sytem web\forest-dashboard"
git init
git add .
git commit -m "Initial forest dashboard app"
git branch -M main
git remote add origin https://github.com/<your-username>/forest-dashboard.git
git push -u origin main
```

## 3) Deploy backend (recommended: Render)

Basic flow:

1. Sign in to Render.
2. New Web Service -> connect GitHub repo.
3. Runtime: Python.
4. Build command:
   `pip install -r backend/requirements.txt`
5. Start command:
   `python backend/app.py`
6. Add environment variables from `.env` (`DB_HOST`, `DB_PORT`, etc).
7. Deploy and copy your backend URL (example: `https://forest-dashboard.onrender.com`).

## 4) (Optional) Host frontend on GitHub Pages

If you want GitHub Pages for frontend:

1. Create a `docs/` folder and copy `frontend/index.html`.
2. Copy `static/css` and `static/js` into `docs/static/...`.
3. In JS, replace API paths:
   - from `/api/alerts` to `https://your-backend-url/api/alerts`
   - from `/api/summary` to `https://your-backend-url/api/summary`
4. Commit and push.
5. In GitHub repo settings:
   - Pages -> Deploy from branch
   - Branch: `main`, Folder: `/docs`

## 5) Verify production

- Frontend URL opens correctly.
- Map loads tiles.
- API calls return data.
- Filters and table interactions work.
