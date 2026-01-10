# How to Start Policy Drift Detection Servers

## Quick Start Guide

### Option 1: Using PowerShell Scripts (Easiest)

#### Start Backend:
```powershell
cd C:\Users\Offic\Desktop\LLM\policy-lens\backend
.\start_backend.ps1
```

#### Start Frontend:
Open a **new** PowerShell window:
```powershell
cd C:\Users\Offic\Desktop\LLM\policy-lens\frontend
npm run dev
```

---

### Option 2: Manual Start (Step by Step)

#### Step 1: Start Backend Server

Open PowerShell and run:
```powershell
# Navigate to backend directory
cd C:\Users\Offic\Desktop\LLM\policy-lens\backend

# Set MongoDB connection (your Atlas cluster)
$env:MONGODB_URI="mongodb+srv://gaurav2921singh_db_user:0LWiCzxExxUU4BC3@policydrift.slmbmvv.mongodb.net/"
$env:MONGODB_DB="policy_drift_detection"
$env:GEMINI_API_KEY="AIzaSyAiXDiHETqw5lTb75NPUugSQxZhaSd4ukM"

# Start the server
python main.py
```

**You should see:**
```
INFO:     Uvicorn running on http://0.0.0.0:8000
```

**Backend will be available at:** http://localhost:8000

---

#### Step 2: Start Frontend Server

Open a **NEW** PowerShell window (keep backend running) and run:
```powershell
# Navigate to frontend directory
cd C:\Users\Offic\Desktop\LLM\policy-lens\frontend

# Start the development server
npm run dev
```

**You should see:**
```
VITE ready in XXX ms
➜  Local:   http://localhost:3000/
```

**Frontend will be available at:** http://localhost:3000

---

## Verification

### Check Backend:
Open browser: http://localhost:8000/health

Should show:
```json
{
  "status": "healthy",
  "mongodb_connected": true
}
```

### Check Frontend:
Open browser: http://localhost:3000

Should show the Policy Drift Detection application.

---

## Important Notes

1. **Two Separate Windows**: You need TWO PowerShell windows - one for backend, one for frontend
2. **Backend First**: Start backend first, then frontend
3. **Keep Both Running**: Don't close either window while using the application
4. **MongoDB**: The backend automatically connects to your MongoDB Atlas cluster

---

## Troubleshooting

### Backend won't start?
- Check if port 8000 is already in use
- Make sure MongoDB connection string is correct
- Verify Python dependencies are installed: `pip install -r requirements.txt`

### Frontend won't start?
- Check if port 3000 is already in use
- Make sure Node.js dependencies are installed: `npm install`
- Verify you're in the frontend directory

### MongoDB connection error?
- Verify your MongoDB Atlas connection string
- Check your internet connection
- Ensure MongoDB Atlas cluster is running

---

## Quick Commands Summary

**Backend:**
```powershell
cd policy-lens\backend
$env:MONGODB_URI="mongodb+srv://gaurav2921singh_db_user:0LWiCzxExxUU4BC3@policydrift.slmbmvv.mongodb.net/"
$env:MONGODB_DB="policy_drift_detection"
$env:GEMINI_API_KEY="AIzaSyAiXDiHETqw5lTb75NPUugSQxZhaSd4ukM"
python main.py
```

**Frontend:**
```powershell
cd policy-lens\frontend
npm run dev
```
