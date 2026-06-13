# 🤖 Jarvis — AI Voice Assistant

A Python-based personal voice assistant inspired by Iron Man's J.A.R.V.I.S. It listens for a wake word, processes voice commands, and responds using text-to-speech — powered by OpenAI GPT, Google Speech Recognition, and real-time news APIs.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎙️ **Wake Word Detection** | Activates on hearing *"Jarvis"* |
| 🌐 **Browser Control** | Opens Google, YouTube, Facebook, LinkedIn via voice |
| 🎵 **Music Playback** | Plays songs from a personal music library on YouTube |
| 📰 **Live News** | Fetches and reads top headlines from India (NewsAPI) |
| 🧠 **AI Conversations** | Handles general queries using OpenAI GPT-3.5 Turbo |
| 🔊 **Natural TTS** | Speaks responses using Google Text-to-Speech (gTTS) + Pygame |

---

## 🗂️ Project Structure

```
jarvis-voice-assistant/
│
├── main.py             # Core assistant — wake word loop, command processing
├── client.py           # Standalone OpenAI API test script
├── musicLibrary.py     # Dictionary of song names → YouTube URLs
└── README.md           # Project documentation
```

---

## 🔁 How It Works

```
Microphone Input
      │
      ▼
Wake Word Check ("jarvis")
      │
      ▼
Listen for Command
      │
      ├── "open google/youtube/..."  →  webbrowser.open()
      ├── "play <song>"              →  musicLibrary lookup → webbrowser.open()
      ├── "news"                     →  NewsAPI → speak headlines
      └── anything else              →  OpenAI GPT → speak response
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- A microphone connected to your system
- API keys for **OpenAI** and **NewsAPI**

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/souravvrc/smart-assistant-jarvis.git
   cd jarvis-voice-assistant
   ```

2. **Install dependencies**
   ```bash
   pip install openai speechrecognition pyttsx3 requests gtts pygame pyaudio
   ```

   > On some systems you may also need:
   > ```bash
   > pip install pocketsphinx
   > ```

3. **Add your API keys**

   In `main.py`, replace the placeholders:
   ```python
   # OpenAI key (in aiProcess function)
   client = OpenAI(api_key="YOUR_OPENAI_API_KEY")

   # NewsAPI key
   newsapi = "YOUR_NEWSAPI_KEY"
   ```

4. **Add your songs** *(optional)*

   Edit `musicLibrary.py` to add your own tracks:
   ```python
   music = {
       "songname": "https://www.youtube.com/watch?v=...",
   }
   ```

5. **Run the assistant**
   ```bash
   python main.py
   ```

---

## 🗣️ Usage

Once running, say **"Jarvis"** to activate, then give a command:

| Voice Command | Action |
|---------------|--------|
| `"Jarvis"` | Wakes the assistant |
| `"Open Google"` | Opens google.com in browser |
| `"Open YouTube"` | Opens youtube.com in browser |
| `"Open Facebook"` | Opens facebook.com in browser |
| `"Open LinkedIn"` | Opens linkedin.com in browser |
| `"Play skyfall"` | Plays the song from musicLibrary |
| `"News"` | Reads today's top headlines |
| `"What is machine learning?"` | GPT answers and speaks the response |

---

## 🔑 API Keys Required

| Service | Purpose | Get it here |
|---------|---------|-------------|
| [OpenAI](https://platform.openai.com/api-keys) | GPT-3.5 Turbo for AI responses | platform.openai.com |
| [NewsAPI](https://newsapi.org/) | Live news headlines | newsapi.org |

> ⚠️ **Never commit API keys to GitHub.** Use environment variables or a `.env` file with `python-dotenv`.

### Recommended: Use environment variables
```python
import os
client = OpenAI(api_key=os.environ.get("OPENAI_API_KEY"))
newsapi = os.environ.get("NEWS_API_KEY")
```

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Pygame](https://img.shields.io/badge/Pygame-008000?style=for-the-badge&logo=python&logoColor=white)

| Library | Role |
|---------|------|
| `speechrecognition` | Captures and converts microphone input to text |
| `openai` | GPT-3.5 Turbo for intelligent responses |
| `gtts` | Converts text responses to natural speech (MP3) |
| `pygame` | Plays the generated MP3 audio |
| `pyttsx3` | Offline TTS fallback engine |
| `webbrowser` | Opens URLs in the default browser |
| `requests` | Fetches live news from NewsAPI |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---
