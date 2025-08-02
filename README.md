# WhatsApp-Driven-Google-Drive-Assistant-n8n-Workflow-
This project implements an automation workflow using **n8n** that connects WhatsApp (via Twilio) with Google Drive, enabling file operations and AI-powered document summaries directly via chat commands.
## 🚀 Features

- 🔍 `LIST /folder` — Lists all files in the specified Google Drive folder.
- 🗑 `DELETE /folder/file.ext` — Deletes a file from the folder (with safety checks).
- 📁 `MOVE /folder/file.ext /newfolder` — Moves file between folders.
- 📄 `SUMMARY /folder` — Summarizes the content of PDF/DOCX/TXT files using OpenAI GPT-4o.

---

## 🧰 Tech Stack

- [n8n](https://n8n.io) (workflow automation)
- [Twilio Sandbox for WhatsApp](https://www.twilio.com/whatsapp)
- Google Drive API
- OpenAI GPT-4o (for summarization)
- Docker (for local deployment)

---

## 📦 Files in This Repo

| File                  | Description |
|-----------------------|-------------|
| `workflow.json`       | The main n8n workflow to import |
| `.env.sample`         | Sample environment file |
| `README.md`           | Setup guide |


## 🔧 Setup Instructions

### 1. Clone the Repo


git clone https://github.com/your-username/whatsapp-drive-assistant
cd whatsapp-drive-assistant
# 2. Configure .env
Create a .env file with the following:

TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886
USER_WHATSAPP_NUMBER=whatsapp:+91XXXXXXXXXX

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_REFRESH_TOKEN=your_refresh_token

OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxx
# 3. Set Up Twilio Sandbox for WhatsApp
Sign in to Twilio: https://www.twilio.com/console

Navigate to Messaging > Try it out > Send a WhatsApp message

Follow instructions to:

Join sandbox using a code (e.g., "join salt-table")

Get your sandbox number (usually +14155238886)

Set your Webhook URL in the Twilio Sandbox to point to your n8n endpoint:

https://<your-n8n-host>/webhook/whatsapp
# 4. Set Up Google OAuth2 Credentials
Go to Google Cloud Console

Create a new project > Enable Google Drive API

Create OAuth2 credentials:

App type: Desktop

Get Client ID, Secret

Generate a Refresh Token manually using OAuth Playground
# 5. Run n8n via Docker
docker run -it --rm \
  -p 5678:5678 \
  --env-file .env \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
Once running, access it at http://localhost:5678

📥 Import Workflow
Open the n8n editor UI

Click Import > Upload workflow.json

Review each node’s credentials:

WhatsApp Webhook

Google Drive credentials (OAuth2)

OpenAI API key

Save & Activate the workflow.



5. Run n8n via Docker
