# 🖥️ IT Helpdesk Bot

![Python 3.11+](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat-square&logo=python&logoColor=white) ![MIT License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square) ![Gemma 4](https://img.shields.io/badge/Gemma_4-Google-4285F4?style=flat-square&logo=google&logoColor=white) ![Privacy-First](https://img.shields.io/badge/Privacy--First-100%25_Local-8b5cf6?style=flat-square) ![Ollama](https://img.shields.io/badge/Ollama-Powered-000000?style=flat-square&logo=ollama&logoColor=white)

**AI-powered IT support assistant that diagnoses issues, searches a built-in knowledge base, and tracks tickets — all running 100 % locally via Ollama.**

---

## Architecture

```
┌──────────────────────────────────────────────────┐
│                 IT Helpdesk Bot                   │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────────┐   │
│  │   CLI    │  │  Web UI  │  │  REST API    │   │
│  │  (Click) │  │(Streamlit)│  │  (FastAPI)   │   │
│  └────┬─────┘  └────┬─────┘  └──────┬───────┘   │
│       └──────────────┼───────────────┘           │
│              ┌───────┴───────┐                   │
│              │  Core Engine  │                   │
│              │ get_response()│                   │
│              └───────┬───────┘                   │
│       ┌──────────────┼──────────────┐            │
│  ┌────┴─────┐  ┌─────┴─────┐  ┌────┴────┐       │
│  │  Ollama  │  │ Knowledge │  │ Ticket  │       │
│  │  Gemma 4 │  │   Base    │  │ Tracker │       │
│  └──────────┘  └───────────┘  └─────────┘       │
│  ┌───────────────────────────────────────────┐   │
│  │  Storage: tickets.json | knowledge_base   │   │
│  └───────────────────────────────────────────┘   │
└──────────────────────────────────────────────────┘
```

---

## ✨ Key Features

- **7 Support Categories** — hardware, software, network, security, email, printer, and general IT questions
- **Conversational Diagnosis** — multi-turn chat with context-aware troubleshooting from Gemma 4
- **Built-in Knowledge Base** — searchable library of common solutions (password reset, VPN, printers, slow PC, email sync)
- **Ticket Tracking** — create, list, and close tickets with JSON-based persistent storage
- **Solution Templates** — pre-built troubleshooting checklists for hardware, software, network, and security
- **Interactive CLI** — Rich-powered terminal with category selection, inline KB search, and ticket management
- **Streamlit Web UI** — browser-based helpdesk interface with chat and ticket views
- **FastAPI REST API** — /chat, /categories, and /health endpoints for integration
- **Conversation History** — full session context maintained for accurate follow-up diagnosis
- **100 % Local & Private** — no cloud APIs, no data exfiltration, GDPR/HIPAA-friendly by design

---

## 🚀 Quick Start

### Prerequisites

| Requirement | Version |
|-------------|---------|
| Python      | 3.11+   |
| Ollama      | latest  |
| Gemma 4 model | pulled via Ollama |

### Installation

```bash
git clone https://github.com/kennedyraju55/it-helpdesk-bot.git
cd it-helpdesk-bot
pip install -r requirements.txt
ollama pull gemma4
```

### Run

```bash
# CLI (interactive)
python -m src.helpdesk_bot.cli

# CLI with category pre-selected
python -m src.helpdesk_bot.cli --category 3   # Network Issues

# Web UI
streamlit run src/helpdesk_bot/web_ui.py

# REST API
uvicorn src.helpdesk_bot.api:app --host 0.0.0.0 --port 8001

# Docker
docker compose up
```

---

## 🛠️ Tech Stack

| Component        | Technology             |
|------------------|------------------------|
| Language         | Python 3.11+           |
| LLM              | Gemma 4 via Ollama     |
| CLI Framework    | Click + Rich           |
| Web UI           | Streamlit              |
| REST API         | FastAPI + Uvicorn      |
| Data Storage     | JSON files             |
| Configuration    | YAML (config.yaml)     |
| Containerization | Docker + Docker Compose|
| Testing          | pytest                 |

---

## 📁 Project Structure

```
it-helpdesk-bot/
├── src/helpdesk_bot/
│   ├── core.py        # LLM-powered response generation
│   ├── cli.py         # Click CLI with interactive support loop
│   ├── web_ui.py      # Streamlit web interface
│   ├── api.py         # FastAPI REST endpoints
│   ├── utils.py       # Ticket tracking, knowledge base, templates
│   └── config.py      # YAML config loader
├── common/            # Shared LLM client
├── tests/             # pytest test suite
├── config.yaml        # Default configuration
├── requirements.txt   # Python dependencies
├── Dockerfile         # Container build
└── docker-compose.yml # Multi-service orchestration
```

---

## 👤 Author

**Nrk Raju Guthikonda**

- GitHub: [kennedyraju55](https://github.com/kennedyraju55)
- Dev.to: [https://dev.to/kennedyraju55](https://dev.to/kennedyraju55)
- LinkedIn: [https://www.linkedin.com/in/nrk-raju-guthikonda-504066a8/](https://www.linkedin.com/in/nrk-raju-guthikonda-504066a8/)

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
