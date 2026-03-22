# 🗳️ PULSE — Polling App

A mobile-responsive, single-page polling website built with **HTML5 + CSS3 + JS** (frontend) and **Node.js + Express** (backend), using a **JSON file** as the database.

---

## 📁 Project Structure

```
polling-app/
├── server.js          ← Express backend (API + routing)
├── package.json
├── votes.json         ← Auto-created on first vote (your database)
└── public/
    ├── index.html     ← Voter-facing poll page
    └── results.html   ← Admin results dashboard (/results)
```

---

## 🚀 Quick Start

### 1. Install dependencies
```bash
npm install
```

### 2. Start the server
```bash
npm start
# → Running at http://localhost:3000
```

Or for hot-reload during development:
```bash
npm run dev
```

### 3. Open in browser
| Page        | URL                          |
|-------------|------------------------------|
| Poll        | http://localhost:3000        |
| Results     | http://localhost:3000/results |

---

## ⚙️ Customizing the Poll

Edit the `POLL` constant near the top of `server.js`:

```js
const POLL = {
  question: "Which technology are you most excited about in 2025?",
  options: [
    { id: "a", label: "Artificial Intelligence & LLMs" },
    { id: "b", label: "Quantum Computing" },
    { id: "c", label: "Augmented Reality (AR/XR)" },
    { id: "d", label: "Biotech & Gene Editing" },
  ]
};
```

To reset votes, delete `votes.json` and restart the server.

---

## 🔌 API Endpoints

| Method | Route          | Description                     |
|--------|----------------|---------------------------------|
| GET    | `/api/poll`    | Returns question & options      |
| POST   | `/api/vote`    | Submit a vote `{name, choice}`  |
| GET    | `/api/results` | Returns all votes + tally       |
| GET    | `/results`     | Admin results page (HTML)       |

---

## ✅ Features

- **Name required** — duplicate names are rejected
- **One vote per name** — prevents repeat voting
- **Thank You screen** — shown immediately after submission
- **Live results** — `/results` shows bar chart + full voter log table
- **Refresh button** — updates results in real time
- **Mobile responsive** — works on all screen sizes

---

## 🗄️ Data Format (`votes.json`)

```json
[
  {
    "id": 1712345678901,
    "name": "Alex Johnson",
    "choice": "a",
    "choiceLabel": "Artificial Intelligence & LLMs",
    "votedAt": "2025-04-05T10:23:45.000Z"
  }
]
```

---

## 🌐 Deploying

To deploy on **Railway**, **Render**, or **Fly.io**:

1. Push this folder to a GitHub repo
2. Connect to your platform of choice
3. Set start command: `node server.js`
4. Set `PORT` env variable if needed (defaults to 3000)

> **Note:** For production, replace `votes.json` with a real database like MongoDB Atlas or PostgreSQL for persistence across restarts.
