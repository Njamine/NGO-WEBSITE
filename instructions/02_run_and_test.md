# 02 - Run and Test Dashboard

## 1) Start backend

```powershell
cd "D:\alert sytem web\forest-dashboard"
.\.venv\Scripts\Activate.ps1
cd backend
python app.py
```

## 2) Open dashboard

Open browser:

- `http://localhost:5000/`

## 3) Check APIs directly

- `http://localhost:5000/health`
- `http://localhost:5000/api/summary`
- `http://localhost:5000/api/alerts`

## 4) Test filters

- Change date range and click **Apply Filters**
- Select severity and cause values
- Confirm map polygons and table update
- Click any table row and confirm map zooms to that alert

## 5) Common troubleshooting

- Blank map: check internet access for tile layers.
- No alerts: verify table data exists and filters are not too strict.
- API error: verify `.env` values and Postgres service status.
