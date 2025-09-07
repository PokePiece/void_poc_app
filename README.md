# 🧠 Scomaton Backend

Intelligence Brain

This is the FastAPI backend for the **Scomaton**, a personal AI assistant powered by [Together AI](https://platform.together.ai/) using the LLaMA 3 70B model. It handles chat routing, returns model responses, tracks token usage, and supports minimal in-memory conversation context.

---

## 🚀 Features

- 🌐 **FastAPI** backend with full CORS support
- 🤖 Connects to **Together AI’s chat-completion API**
- 🔁 Modular routing logic via OS AI interface
- 💬 Maintains lightweight conversation memory (non-persistent)
- 📊 Tracks and logs token usage (`token_log.jsonl`)
- 🔐 `.env`-based credential loading for API keys
- 🧼 Memory reset endpoint for clean session starts

---

## 📦 Requirements

Install dependencies:

```bash
pip install -r requirements.txt
Create a .env file:

env
Copy
Edit
TOGETHER_API_KEY=your_together_api_key
🛠️ Usage
Start the server locally:

bash
Copy
Edit
uvicorn main:app --reload
Example POST to /chat:
json
Copy
Edit
{
  "prompt": "What is the Scomaton?",
  "max_tokens": 1000
}
🧪 API Endpoints
Method	Endpoint	Description
POST	/chat	Routes prompt through OS AI to Together
GET	/usage-stats	Returns total token usage
GET	/daily-tokens	Returns token usage for today
POST	/reset-memory	Clears conversation history

🧾 Token Logging
Token usage is logged to token_log.jsonl as newline-delimited JSON:

json
Copy
Edit
{
  "timestamp": "2025-07-03T00:00:00Z",
  "prompt_tokens": 120,
  "completion_tokens": 100,
  "total_tokens": 220
}
🚀 Deployment (Render)
Required Files:

main.py

requirements.txt

start.sh:

bash
Copy
Edit
#!/usr/bin/env bash
gunicorn -w 1 -k uvicorn.workers.UvicornWorker main:app
Optional: render.yaml for infrastructure config.

Render Setup:
Push project to GitHub

Go to Render

New → Web Service

Use:

Environment: Python

Build Command: (leave blank)

Start Command: ./start.sh

Manually add .env variables

🔒 Security Notes
This backend connects to external AI models and may process sensitive data. Current protections include:

API key stored in .env

Local-only use recommended during development

Future features will include:

JWT-based user auth

Route-level protection

Rate limiting and per-user memory

✍️ Author
Developed by Dillon Carey
Director of Personal AI Systems
https://dilloncarey.com
