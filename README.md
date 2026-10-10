# ✨ Lumière Salon AI - Luxury Beauty & Styling Intelligence

Welcome to the **Lumière Salon AI & Beauty Lab**. This application provides an AI-powered face-shape analyzer, facial landmark mesh visualization, skin undertone detector, and bespoke haircut, hairstyle, makeup, nail, and accessory recommendations.

---

## 🚀 Quick Start Guide (How to Run on Any Computer)

You have **two seamless options** to run this project:

### Option 1: Zero-Setup Instant Mode (No Python Required! ⚡)
If you do not have Python installed or just want to explore the application immediately:
1. Double-click **`start_frontend.bat`** (or open `index.html` in Chrome, Edge, or Firefox).
2. Navigate to **AI Styling Lab** (`ai-recommendation/ai.html`).
3. Upload a selfie, take a live webcam photo, or click any of the **Demo Models**.
4. Click **✦ Analyze My Look**.
5. The **in-browser AI engine** will instantly analyze your facial geometry, compute measurements, detect your skin undertone, and render your personalized lookbook!

---

### Option 2: Full-Stack Mode (Python FastAPI Backend 🐍)
For maximum machine-learning precision using the dedicated local FastAPI server:
1. Ensure Python 3.10+ is installed on your Windows PC (from [python.org](https://www.python.org/), ensuring *"Add Python to PATH"* is checked).
2. Double-click **`run_all.bat`** in the project folder.
   - It will automatically create a local virtual environment (`venv`).
   - It will install all required packages from `requirements.txt`.
   - It will launch the FastAPI backend on `http://127.0.0.1:8000`.
   - It will launch the frontend on `http://127.0.0.1:5500` and open your default browser.
3. Keep the terminal windows open while using the app.

---

## 📂 Project Structure

```text
beautysalonAI/
├── run_all.bat                      # One-click launcher for both backend & frontend
├── start_backend.bat                # Starts the Python FastAPI backend server
├── start_frontend.bat               # Starts the frontend server and opens browser
├── README.md                        # Documentation and setup guide
├── .gitignore                       # Prevents committing machine-specific venvs
│
└── beautysalon (2)/
    └── beautysalon/
        ├── index.html               # Main Lumière Salon landing & booking website
        ├── script.js                # Main website interactivity and booking logic
        ├── style.css                # Luxury styling and responsive design
        │
        ├── ai-recommendation/
        │   ├── ai.html              # AI Styling Lab interface
        │   ├── ai.js                # Hybrid AI logic (FastAPI + In-Browser Engine)
        │   └── ai.css               # AI Lab luxury aesthetics and animations
        │
        ├── backend/
        │   ├── app.py               # FastAPI backend with MediaPipe & OpenCV
        │   ├── requirements.txt     # Complete Python dependencies
        │   ├── start_backend.bat    # Dedicated backend startup script
        │   └── models/
        │       └── face_landmarker.task   # MediaPipe 3D Face Landmark model
        │
        └── images/                  # Salon gallery images & demo model selfies
```

---

## 🛠️ How It Works Under the Hood

### 1. Hybrid Client/Server Architecture
- The frontend dynamically determines the backend URL (`http://127.0.0.1:8000` or current host).
- When you click **Analyze My Look**, the app first pings the local Python FastAPI backend.
- If the Python server is running, it uses the high-precision backend.
- If the Python server is **not running** (e.g. on a computer without Python), it **automatically falls back to the in-browser AI engine**, ensuring the app **never fails**.

### 2. MediaPipe Model Discovery & Auto-Download
- The 3D Face Landmarker model is stored in:
  `backend/models/face_landmarker.task`
- `backend/app.py` automatically searches multiple relative candidate locations. If the file is missing, it **automatically downloads** the official model from Google Cloud Storage on first run.

### 3. Cross-Origin Resource Sharing (CORS)
- `backend/app.py` is configured with `CORSMiddleware` (`allow_origins=["*"]`), allowing any local port (5500, 3000, 8080) to communicate with the backend.
