🚀 Claude Code + Gemini Full Setup (Windows Guide)
This guide helps you set up Claude-Code + Gemini Models together using
claude-code + claude-code-router.

🔥 STEP 0 — Confirm Node.js
PowerShell open karein → run:

node --version
Agar 18+ version nahi hai → install karein:

👉 https://nodejs.org

🔥 STEP 1 — GET GOOGLE API KEY
Open: https://aistudio.google.com
Click → Get API Key
Click → Create API Key
Key copy kar len (example):
AIzaSy........
🔥 STEP 2 — INSTALL REQUIRED TOOLS
PowerShell (Run as Administrator):

npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router
🔥 STEP 3 — CREATE CONFIG FOLDERS
PowerShell (normal mode):

mkdir $HOME/.claude-code-router
mkdir $HOME/.claude
🔥 STEP 4 — CREATE CONFIG.JSON (WINDOWS VERSION)
Windows me cat << EOF work nahi karta, isliye Notepad method use hoga.

Run:

notepad $HOME/.claude-code-router/config.json
Notepad open hoga → isme ye exact JSON paste karein:

{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": [
        "gemini-2.5-flash",
        "gemini-2.0-flash"
      ],
      "transformer": {
        "use": ["gemini"]
      }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}
✔ Save
✔ Close

🔥 STEP 5 — SET YOUR API KEY (WINDOWS METHOD)
PowerShell (Run as Admin):

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YOUR_KEY_HERE', 'User')
Replace:

YOUR_KEY_HERE
With your actual Google API Key.

Example:

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'AIzaSyXXXXX...', 'User')
⚠️ IMPORTANT
PowerShell close karen → new PowerShell open → check:

echo $env:GOOGLE_API_KEY
Agar value show ho jaye → Perfect! 🔥

🔥 STEP 6 — VERIFY EVERYTHING
Run:

claude --version
ccr version
echo $env:GOOGLE_API_KEY
Agar sab commands ka output aa jaye → ✔ Setup success

🔥 STEP 7 — DAILY WORKFLOW
Terminal 1:
ccr start
Wait until you see:

✔ Service started successfully
Terminal 2:
cd your-project-folder
ccr code
OR:

eval "$(ccr activate)"
claude
🔥 VERIFICATION TEST
Terminal:

ccr code
Then type:

hi
Agar Claude reply kare →
🎉 Congratulations! FREE CLAUDE CODE + GEMINI WORKING! 🚀💯****
