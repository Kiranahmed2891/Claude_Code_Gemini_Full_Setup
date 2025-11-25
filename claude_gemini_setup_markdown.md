# 🚀 Claude Code + Gemini Full Setup (Windows Guide)

This guide helps you set up **Claude Code + Gemini Models** together using `claude-code` and `claude-code-router` on **Windows**.

---

## 🔥 STEP 0 — Confirm Node.js
**PowerShell open karein → run:**
```sh
node --version
```
Agar version **18+** nahi hai → install karein:
- https://nodejs.org

---

## 🔥 STEP 1 — Get Google API Key
1. Open: https://aistudio.google.com
2. Click → **Get API Key**
3. Click → **Create API Key**
4. API key copy kar len (example):
```
AIzaSy........
```

---

## 🔥 STEP 2 — Install Required Tools
**PowerShell (Run as Administrator):**
```sh
npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router
```

---

## 🔥 STEP 3 — Create Config Folders
**PowerShell (normal mode):**
```sh
mkdir $HOME/.claude-code-router
mkdir $HOME/.claude
```

---

## 🔥 STEP 4 — Create `config.json` (Windows Version)
Windows me `cat << EOF` work nahi karta, isliye **Notepad method** use hoga.

Run:
```sh
notepad $HOME/.claude-code-router/config.json
```
Notepad open hoga → isme ye **exact JSON** paste karein:

```json
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
```
✔ Save
✔ Close

---

## 🔥 STEP 5 — Set API Key (Windows Method)
**PowerShell (Run as Admin):**
```sh
[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YOUR_KEY_HERE', 'User')
```
Replace:
```
YOUR_KEY_HERE
```
With your actual Google API Key.

Example:
```sh
[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'AIzaSyXXXXX...', 'User')
```

### ⚠️ IMPORTANT
PowerShell **close** karen → **new PowerShell** open karein → check:
```sh
echo $env:GOOGLE_API_KEY
```
Agar value show ho jaye → ✔ Perfect!

---

## 🔥 STEP 6 — Verify Everything
Run:
```sh
claude --version
ccr version
echo $env:GOOGLE_API_KEY
```
Agar sab commands ka output aa jaye → ✔ **Setup Successful**

---

## 🔥 STEP 7 — Daily Workflow
### Terminal 1:
```sh
ccr start
```
Wait until you see:
```
✔ Service started successfully
```
### Terminal 2:
```sh
cd your-project-folder
ccr code
```
**OR:**
```sh
eval "$(ccr activate)"
claude
```

---

## 🔥 Verification Test
Terminal me run karein:
```sh
ccr code
```
Then type:
```
hi
```
Agar Claude reply kare →

# 🎉 Congratulations! FREE Claude Code + Gemini Working! 🚀💯

---

