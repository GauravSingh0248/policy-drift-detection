# Policy Drift Detection Quick Start Guide

## Prerequisites Check

Before starting, ensure you have:
- ✅ Python 3.9+ installed
- ✅ Node.js 18+ installed
- ✅ MongoDB running (local or remote)

## Quick Setup (5 minutes)

### 1. Start MongoDB

**Local MongoDB:**
```bash
# If installed via Homebrew (Mac)
brew services start mongodb-community

# If installed via apt (Linux)
sudo systemctl start mongod

# If running as service (Windows)
# MongoDB should start automatically
```

**Or use MongoDB Atlas (cloud):**
- Create account at https://www.mongodb.com/cloud/atlas
- Get connection string
- Set `MONGODB_URI` environment variable

### 2. Backend Setup

```bash
cd policy-lens/backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install spaCy model
python -m spacy download en_core_web_sm

# (Optional) Set MongoDB connection
export MONGODB_URI="mongodb://localhost:27017"
export MONGODB_DB="policy_drift_detection"

# Start backend
python main.py
```

Backend should be running at `http://localhost:8000`

### 3. Frontend Setup

```bash
# In a new terminal
cd policy-lens/frontend

# Install dependencies
npm install

# Start frontend
npm run dev
```

Frontend should be running at `http://localhost:3000`

## First Steps

1. **Open the application**: Navigate to `http://localhost:3000`

2. **Upload a policy**:
   - Click "Upload Policy"
   - Select `data/sample_policy.txt` or any PDF/TXT file
   - Wait for parsing to complete

3. **Upload implementation data**:
   - Click on the uploaded policy
   - Click "Upload Dataset (CSV)"
   - Select `data/sample_implementation.csv`

4. **Run drift detection**:
   - Click "Run Drift Detection" on the dataset
   - View results in the Drift Dashboard

5. **Try the chatbot**:
   - Scroll to "Policy Intelligence Assistant"
   - Ask: "Why was District X flagged?"
   - Or try other suggested questions

## Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running: `mongosh` or `mongo`
- Check connection string in environment variables
- Verify MongoDB port (default: 27017)

### spaCy Model Not Found
```bash
python -m spacy download en_core_web_sm
```

### Port Already in Use
- Backend: Change port in `backend/main.py` (line 194)
- Frontend: Change port in `frontend/vite.config.js`

### Import Errors
- Ensure you're in the correct directory
- Activate virtual environment
- Reinstall dependencies: `pip install -r requirements.txt`

## Next Steps

- Read the full [README.md](README.md) for detailed documentation
- Check [ARCHITECTURE.md](ARCHITECTURE.md) for system design
- Upload your own policy documents and datasets
- Explore the API at `http://localhost:8000/docs`
