
<div align="center">

# ☢️ BodyaSync-Server (The Engine Room)

<!-- BADGES -->
![Status](https://img.shields.io/badge/STATUS-OPERATIONAL-green?style=for-the-badge&logo=server)
![Python](https://img.shields.io/badge/CORE-PYTHON_3.10+-yellow?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FRAMEWORK-FASTAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Telegram](https://img.shields.io/badge/MODULE-TELEGRAM_USERBOT-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)
![AI](https://img.shields.io/badge/AI-OLLAMA_%2B_HUGGINGFACE-purple?style=for-the-badge&logo=openai)

<h3>The Brain. The Muscle. The Vault.</h3>
<p>This is the backend beast that powers the BodyaSync-Compose and BodyaGram app.</p>

</div>

---

## 💀 Mission Briefing

This isn't just a file server. It's a highly optimized media processing unit designed to run on anything from a high-end rack server to a Raspberry Pi in a shoebox.

It handles the dirty work: compressing images, managing storage, generating AI memories, and "smuggling" files directly into Telegram so your phone doesn't have to lifting a finger.

---

## 💥 Heavy Artillery (Features)

### 1. 🤫 RAM Cache (Stealth Mode)
Your hard drives make noise and eat power. We hate that.
*   **The Solution:** This server loads thumbnails and metadata directly into **RAM**.
*   **The Result:** Your HDDs stay parked (sleeping). Browsing the gallery is silent and instant. We only wake up the drives when you actually download a full-size original.

### 2. ⚡ Aggressive Compression
*   **Photos:** Converted to **WebP**. Quality 70-75%. Size ~5-10KB.
*   **Videos:** FFmpeg generates instant snapshots.
*   **Network:** Optimized so you can browse 10,000 photos over a weak 3G connection without lagging.

### 3. 🤖 AI Memories & Collages
It doesn't just store files; it *remembers*.
*   **Captioning:** Uses Gradio/HuggingFace to see what's in your photos.
*   **Storytelling:** Uses **Ollama** to write nostalgic, warm descriptions in Ukrainian (or any language configured).
*   **Collages:** Auto-generates backgrounds based on dominant colors and stitches photos together.

### 4. ✈️ The Telegram Smuggler
Integrated **Telethon Userbot**.
*   You click a button in the app.
*   The server grabs the file from the disk.
*   The server sends it directly to your Telegram chat.
*   **Zero data usage on your phone.**

### 5. 🎥 Video "Fast Start"
Automatically moves the `moov` atom to the beginning of MP4 files. This means videos start playing *immediately* while streaming, no buffering required.

---

## 🛠 Loadout (Prerequisites)

Before you deploy, you need the right tools.

### System Requirements (Linux/Ubuntu/Debian)
You need **FFmpeg** for video processing. Don't skip this, or the server will jam.

```bash
sudo apt update
sudo apt install ffmpeg libsm6 libxext6 -y
```

### Python Dependencies
Install the required libraries.

```bash
pip install -r requirements.txt
```

*(If you don't have a `requirements.txt` yet, copy the one at the bottom of this README).*

---

## ⚙️ Configuration (.env)

This server needs credentials to talk to Telegram. Create a file named `.env` in the root directory.

**File:** `.env`
```ini
# Get these from https://my.telegram.org/apps
API_ID=123456
API_HASH=abcdef1234567890

# Optional: Adjust if needed, but the code handles defaults
# HOST=0.0.0.0
# PORT=8000
```

> **Warning:** Never commit your `.env` file to GitHub. That's how you get hacked.

---

## 🚀 Launch Sequence

Fire up the engine. We use `uvicorn` as the ASGI server.

```bash
# Standard Launch
uvicorn server:app --host 0.0.0.0 --port 8000

# For Development (Auto-reload)
uvicorn server:app --host 0.0.0.0 --port 8000 --reload
```

Once running, the server will:
1.  Connect to Telegram (you might need to enter a code in the terminal on first run).
2.  Scan your storage (`/mnt/storage`).
3.  Load the RAM cache.
4.  Wait for orders.

---

## 📦 Requirements.txt (Copy/Paste)

Create a `requirements.txt` file and paste this list of ammo:

```text
fastapi
uvicorn
python-multipart
python-dotenv
Pillow
telethon
ffmpeg-python
hachoir
requests
gradio_client
pydantic
```

---

## 📂 File Structure

The server expects a specific directory structure. It will try to create it, but keep this in mind:

```text
/
├── server.py           # The Brain
├── .env                # Credentials
├── assets/             # Fonts, frames, resources
└── /mnt/storage/       # YOUR DATA (Mount your HDD here)
    ├── originals/      # Full resolution photos/videos
    ├── thumbnails/     # Generated WebP previews
    ├── memories/       # AI generated stories
    ├── music/          # Music for memories
    └── metadata.json   # Cache file
```

---

<div align="center">

**⚠️ SYSTEM STATUS: CLASSIFIED ⚠️**
*Built for speed. Optimized for low-end hardware. 
No warranties. Use at your own risk.*

</div>
