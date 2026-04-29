# 📧 AI Email Reply Agent — n8n Workflow

> **Automatically reads unread Gmail, drafts professional AI replies, sends them, and logs everything to Airtable.**
> Powered by n8n + OpenAI + Gmail + Airtable

---

## 💡 What It Does

| Feature | Description |
|--------|-------------|
| 📬 **Auto Email Reading** | Fetches all unread Gmail messages on a schedule |
| 🤖 **AI Reply Drafting** | GPT-4o-mini writes 100% human-like professional replies |
| 📤 **Auto Send Reply** | Automatically sends the AI reply back to the sender |
| 💾 **Airtable Logging** | Saves sender name, email, body & AI reply to Airtable |
| ✅ **Mark as Read** | Marks emails as read after processing |
| 🔒 **Context-Aware** | Reads sender name & intent before replying |

---

## 🏗️ Architecture

```
Schedule Trigger (every X minutes)
        │
        ▼
  Gmail → Get All UNREAD Emails
        │
        ▼
  Gmail → Get Full Email (with attachments)
        │
        ▼
  AI Agent (GPT-4o-mini)
  └── Drafts professional human-like reply
        │
        ▼
  Airtable → Save Record
  (Sender Name, Email, Body, AI Response)
        │
        ▼
  Gmail → Send Reply to Sender 📤
        │
        ▼
  Gmail → Mark as Read ✅
```

---

## 📁 Project Structure

```
email-reply-agent/
├── README.md
├── workflow/
│   └── email-reply-agent.json   ← Import this into n8n
└── .gitignore
```

---

## 🚀 Quick Start

### 1. Import Workflow into n8n

```
Open n8n → Workflows → Import from file
→ Select: workflow/email-reply-agent.json
```

---

### 2. Connect Credentials

- ✅ **Gmail OAuth2** — to read, send, and mark emails
- ✅ **OpenAI API key** — for GPT-4o-mini replies
- ✅ **Airtable Personal Access Token** — to log email data

---

### 3. Set Up Airtable

Create a base named **`Mail recieved data`** with these columns:

| Column | Type |
|--------|------|
| `Sender Name` | Single line text |
| `Sender Email` | Email |
| `Email Body` | Long text |
| `Response` | Long text |

---

### 4. Update Airtable IDs

Replace in the workflow:
```
YOUR_AIRTABLE_BASE_ID  → found in your Airtable URL
YOUR_AIRTABLE_TABLE_ID → found in your Airtable URL
```

---

### 5. Set Schedule

In the **Schedule Trigger** node, set how often to check emails:
- Every 5 minutes
- Every 1 hour

---

### 6. Activate Workflow

Click **Publish** in n8n to go live ✅

---

## 🤖 AI Agent Persona

The agent replies as:

```
Name    : Muhammad Masood Anwar
Company : AI Learners Pakistan
Mission : Teaching AI in the simplest way
Focus   : Community building over promotions
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| ⚙️ Workflow Automation | n8n |
| 🤖 AI Model | OpenAI GPT-4o-mini |
| 📬 Email | Gmail OAuth2 |
| 🗄️ Database | Airtable |

---

## 🔐 Security Notes

```
✅ Credential IDs removed from public workflow
✅ Airtable IDs replaced with placeholders
✅ No real API keys committed
```

---

## 📄 License

**MIT** — free to use and modify.
