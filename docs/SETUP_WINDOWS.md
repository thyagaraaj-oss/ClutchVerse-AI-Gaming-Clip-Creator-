# Windows Development Setup

## Prerequisites

- Windows 10 or 11, 64-bit.
- Python 3.10 or later.
- FFmpeg and ffprobe available on PATH.
- Git.
- Optional: Google Gemini API key for AI metadata or model-assisted suggestions.

## 1. Verify tools

Open PowerShell:

```powershell
python --version
git --version
ffmpeg -version
ffprobe -version
```

If `ffmpeg` is not recognized, install an FFmpeg Windows build and add its `bin` directory to PATH. Reopen PowerShell after changing PATH.

## 2. Get the source

After creating the GitHub repository:

```powershell
git clone https://github.com/YOUR_USERNAME/ClutchVerse.git
cd ClutchVerse
```

Replace `YOUR_USERNAME` with the actual GitHub username and use the repository URL that really exists.

## 3. Create a virtual environment

```powershell
python -m venv .venv
.venv\\Scripts\\Activate.ps1
python -m pip install --upgrade pip
```

If PowerShell blocks activation, use Command Prompt:

```bat
.venv\\Scripts\\activate.bat
```

## 4. Install dependencies

```powershell
pip install -r requirements.txt
```

The requirements file in this documentation package is a proposed baseline. Pin and test versions before a production release.

## 5. Configure secrets

```powershell
Copy-Item .env.example .env
```

Edit `.env` locally. Do not commit it.

## 6. Run

When the Streamlit entry point has been implemented:

```powershell
streamlit run app.py
```

## Troubleshooting

- `python` not found: install Python and enable the PATH option.
- `ffmpeg` not found: check PATH and restart the terminal.
- Package installation fails: update pip and check Python compatibility.
- Model downloads are large: use a smaller Whisper model for limited hardware.
- Rendering is slow: lower preview resolution or use shorter source segments while testing.
