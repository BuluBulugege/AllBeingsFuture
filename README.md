[中文](./README.zh.md) | **English**

<div align="center">
<img src="public/logo-text.png" width="480" />

# AllBeingsFuture
**THE COMMAND CENTER FOR PARALLEL AI WORK**

[![License](https://img.shields.io/badge/license-BSD_3--Clause-orange.svg?style=flat-square)](LICENSE)
[![Electron](https://img.shields.io/badge/Electron-33-black.svg?style=flat-square&logo=electron)](https://electronjs.org)
[![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows-black.svg?style=flat-square)](https://github.com/AllBeingsFuture/AllBeingsFuture/releases)
[![React](https://img.shields.io/badge/React-18-black.svg?style=flat-square&logo=react)](https://reactjs.org)

[Features](#-features) · [How It Works](#-how-it-works) · [Quick Start](#-quick-start) · [Tech Stack](#-tech-stack) · [中文](./README.zh.md)
</div>

---

**AllBeingsFuture** is a *desktop AI workbench* that puts Claude, Codex, Gemini, and OpenCode under one roof — and lets them work in parallel. Spawn a Supervisor agent that breaks down complex tasks, dispatches sub-agents to isolated Git worktrees, and coordinates results — all without leaving a single window. With 72 built-in skills covering everything from code review to PDF processing, it is the operating table for serious AI-assisted development.

## ✨ Features

- **5 AI Providers in One UI** — Claude Code, Codex CLI, Gemini CLI, OpenCode, iFlow CLI; switch or run simultaneously
- **Supervisor Mode** — one master agent spawns and coordinates parallel sub-agents for complex multi-step tasks
- **Git Worktree Isolation** — each agent works in its own branch; no merge conflicts, no file clobbering
- **72 Built-in Skills** — code review, PPT/PDF/Excel generation, image understanding, translation, web scraping, Bilibili tools, and more
- **MCP Protocol** — extensible via Agent Control, Web Search, Chrome DevTools, and custom MCP servers
- **Built-in Terminal** — full xterm.js + node-pty terminal inside the app
- **Token Dashboard** — real-time usage tracking across all providers and sessions
- **Policy Engine** — audit logs, access control, and governance for team deployments
- **Bot Management** — connect and manage IM bots (Telegram, etc.) directly from the workbench
- **Task Queue** — background task management with status monitoring

## 🖼 How It Works

### Phase 1 — Connect Your AI Providers

<div align="center"><img src="public/illus-multi-provider.en.png" width="700" /></div>

1. Launch AllBeingsFuture and open **Settings → AI Provider**
2. Configure API keys or CLI paths for any combination of Claude, Codex, Gemini, OpenCode, or iFlow
3. Each session picks a provider — or let the Supervisor choose based on the task
4. Providers run independently; switch mid-session without losing context

### Phase 2 — Orchestrate Multiple Agents

<div align="center"><img src="public/illus-multi-agent.en.png" width="700" /></div>

1. Create a session in **Supervisor** mode
2. Describe the high-level goal — the Supervisor decomposes it into subtasks
3. Sub-agents spawn automatically, each in its own **Git Worktree**
4. Work proceeds in parallel; results are collected and merged by the Supervisor
5. Monitor all agents in real time from the Sessions sidebar

## 📸 Screenshots

<div align="center">
<img src="public/screenshots/main-ui.png" width="700" />

*Main workspace — brutalist dark UI with session sidebar, multi-provider feature cards, and real-time status bar*
</div>

<br />

<div align="center">
<img src="public/screenshots/new-session.png" width="700" />

*New session dialog — select provider (Claude, Codex, Gemini, OpenCode, iFlow), working directory, and session mode*
</div>

<br />

<div align="center">
<img src="public/screenshots/settings.png" width="700" />

*Settings panel — proxy, speech-to-text, Git Worktree isolation, and full system configuration*
</div>

## 🚀 Quick Start

**Prerequisites:** [Node.js 22+](https://nodejs.org/)

```bash
# Clone and install
git clone https://github.com/AllBeingsFuture/AllBeingsFuture.git
cd AllBeingsFuture
npm install

# Development (hot reload)
npm run dev

# Production build
npm run build

# Package — Windows installer
npm run pack

# Package — macOS DMG (arm64 + x64)
npm run pack:mac
```

> **macOS note:** First launch may show "unverified developer" — go to **System Settings → Privacy & Security → Open Anyway**.

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Desktop | Electron 33 (Main + Renderer dual-process) |
| Frontend | React 18 · TypeScript 5.7 · Vite 6 · Zustand 5 · TailwindCSS 3 |
| Backend | better-sqlite3 · node-pty · Claude Agent SDK |
| AI Providers | Claude Code · Codex CLI · Gemini CLI · OpenCode · iFlow CLI |
| MCP Servers | Agent Control · Web Search · Chrome DevTools |
| Build | electron-builder → NSIS (Windows) · DMG (macOS) |

## 📁 Project Structure

```
electron/
├── main.ts              # Entry: window, IPC, SQLite, system tray
├── bridge/adapters/     # Claude / Codex / Gemini / OpenCode adapters
├── parser/              # CLI output parsing engine
├── services/            # 45 service modules (~9000+ LOC)
└── ipc/handlers.ts      # 50+ IPC channel routes

frontend/src/
├── stores/              # 30+ Zustand stores
├── components/          # UI components
└── hooks/               # Custom hooks

mcps/                    # MCP Servers (Agent Control, Web Search, Chrome DevTools)
skills/                  # 72 built-in skill templates
```

## 🤝 Contributing

Pull requests welcome. Check the issue tracker or open a discussion.

---

## 📜 License

[BSD 3-Clause](LICENSE) — open source.

## 🔗 Links

- [LINUX DO Community](https://linux.do/)
