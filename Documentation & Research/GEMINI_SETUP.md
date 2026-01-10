# Gemini API Setup Guide

The Policy Drift Detection chatbot now uses Google's Gemini API to provide intelligent answers about your policy documents. Follow these steps to set it up:

## Step 1: Get a Gemini API Key (Free)

1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey) or [Google Cloud Console](https://console.cloud.google.com/)
2. Sign in with your Google account
3. Navigate to "Get API Key" section
4. Create a new API key (or use an existing one)
5. Copy the API key

**Note:** The Gemini API has a generous free tier, perfect for development and moderate usage.

## Step 2: Set the API Key

### Option A: Environment Variable (Recommended)

#### Windows (PowerShell):
```powershell
$env:GEMINI_API_KEY="your-api-key-here"
```

#### Windows (Command Prompt):
```cmd
set GEMINI_API_KEY=your-api-key-here
```

#### Linux/Mac:
```bash
export GEMINI_API_KEY="your-api-key-here"
```

### Option B: Create .env File

Create a `.env` file in the `backend` directory with:

```
GEMINI_API_KEY=your-api-key-here
```

The application will automatically load it using `python-dotenv`.

### Option C: Set in Start Scripts

You can also add it to your start scripts:

**backend/start_backend.ps1:**
```powershell
$env:GEMINI_API_KEY = "your-api-key-here"
```

**backend/start_backend.bat:**
```batch
set GEMINI_API_KEY=your-api-key-here
```

## Step 3: Install Dependencies

Make sure you have the required package installed:

```bash
cd backend
pip install -r requirements.txt
```

This will install `google-generativeai>=0.3.0`.

## Step 4: Verify Setup

1. Start your backend server
2. Check the console output - it should not show the "GEMINI_API_KEY not found" warning
3. Try asking a question in the chatbot interface

## How It Works

When the Gemini API key is configured:
- The chatbot reads the full PDF/TXT policy document content
- It includes extracted policy intent, drift results, and summaries in the context
- Gemini AI provides intelligent, context-aware answers about your policies

**Without the API key:**
- The chatbot falls back to simple rule-based responses
- It still works but with limited capabilities
- You'll see a message suggesting to set up the API key for better results

## Troubleshooting

### "GEMINI_API_KEY not found" Warning
- Make sure the environment variable is set correctly
- Restart your backend server after setting the variable
- Check that the variable name is exactly `GEMINI_API_KEY`

### API Errors
- Verify your API key is valid
- Check your internet connection
- Ensure you haven't exceeded the free tier limits
- The chatbot will automatically fall back to simple responses if the API fails

### Still Not Working?
1. Check that `google-generativeai` is installed: `pip list | grep google-generativeai`
2. Verify the API key is being loaded: Add `print(f"API Key: {os.getenv('GEMINI_API_KEY')}")` temporarily in your code
3. Check the backend logs for error messages

## Benefits of Using Gemini API

✅ Answers questions about the actual PDF content  
✅ Understands context and provides detailed explanations  
✅ Handles complex questions naturally  
✅ References specific parts of policy documents  
✅ Explains drift detection results intelligently  

The free tier is sufficient for most development and testing needs!
