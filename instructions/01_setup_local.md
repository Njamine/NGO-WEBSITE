# 01 - Local Setup

Follow these steps in PowerShell.

## 1) Open project folder

```powershell
cd "D:\alert sytem web\forest-dashboard"
```

## 2) Create Python virtual environment

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

## 3) Install backend dependencies

```powershell
cd backend
pip install -r requirements.txt
```

## 4) Add DB credentials

```powershell
cd ..
copy .env.example .env
```

Edit `.env` and set your real PostgreSQL/PostGIS credentials.

## 5) Confirm database table

Your database must contain an `alerts` table with at least:

- `alert_id`
- `date_detected`
- `severity`
- `likely_cause`
- `confidence_score`
- `area_ha`
- `shape_index`
- `pre_ndvi`
- `detection_method`
- `geom` (geometry, PostGIS)

## 6) Start Flask app

```powershell
cd backend
python app.py
```

You should see Flask running on `http://localhost:5000`.
