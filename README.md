# 🚀 Neon Strike - Tic-Tac-Toe Ultimate

Welcome! **Neon Strike** is a dedicated, visually spectacular, premium **standalone Tic-Tac-Toe application** built using **Node.js (Express)** on the backend and modern **Vanilla HTML/CSS/JS** on the frontend. 

It is designed to deliver a visually breathtaking user experience, featuring customizable neon themes, procedurally synthesized audio effects, a smart minimax AI, and full local scoreboards and streak diagnostics.

---

## 🌟 Key Features

1. **🎨 Rich Visual Aesthetics & Atmos Theme Engine**:
   - Built a sleek glassmorphic container layout featuring `backdrop-filter: blur(16px)` and subtle glowing neon borders.
   - Built a customizable **theme engine** with four pre-loaded premium atmospheric presets:
     - **Cyberpunk Neon** (Dark Violet background, Cyan X, Pink O)
     - **Forest Emerald** (Deep Green background, Mint X, Gold O)
     - **Cosmic Abyss** (Pitch Space Blue background, Purple X, Nebula Blue O)
     - **Sunset Glow** (Charcoal background, Coral Orange X, Sunshine Gold O)
   - Created beautiful animations for hovering tiles, SVG path drawing on placements, and dynamic pulsing glows for the winning sequence.
   - Integrated an **SVG strike-through overlay** that draws a smooth neon line across the physical winning tiles dynamically.

2. **🎵 Procedural Audio Engine (Web Audio API)**:
   - Synthesizes modern, low-latency audio effects **procedurally using the Web Audio API**.
   - Requires zero external audio file downloads (works instantly and 100% offline).
   - Generates distinct tones:
     - Pluck tone on X placement.
     - Warm synth on O placement.
     - Ascending major key arpeggio on Victory.
     - Descending slide on Defeat.
     - Twin dual-tone beeps on Draw.
     - High-frequency laser sweep on Match Restart.
   - Includes a persistent mute/unmute control inside the header.

3. **🤖 Intelligent AI Mechanics**:
   - Implemented three distinct **AI Difficulty Modes**:
     - **Easy**: 45% random plays, 55% perfect play.
     - **Medium**: 25% random plays, 75% perfect play. Offers a balanced casual match.
     - **Perfect**: 100% unbeatable minimax AI (guarantees a win or a draw).
   - **Local PVP Mode**: Allows two local players to compete head-to-head with editable, reactive custom usernames.

4. **📊 Diagnostics & Leaderboard Persistence**:
   - Track wins, losses, stalemates, win ratios, and maximum consecutive winning streaks dynamically.
   - All statistics, player preferences (themes, names, mute state, difficulties) persist across browser refreshes via `localStorage`.
   - Dedicated "Reset Metrics" button to reset the database.

5. **🎉 Canvas Win Celebration**:
   - Renders animated multicoloured floating confetti directly inside an HTML5 Canvas when Player 1 defeats the System AI.

---

## 🛠️ Tech Stack

- **Backend**: Node.js (v26.0.0+), Express.js, Morgan (structured request logger)
- **Frontend**: Single-Page Dashboard (HTML5, Vanilla CSS Grid/Flexbox, Custom variables, Glassmorphism design, Vanilla ES6 JavaScript, Web Audio API, Canvas Confetti)
- **Testing**: Native Node.js Test Runner (`node:test` and `node:assert`)
- **Containers**: Docker (secure Alpine multi-stage production setup)

---

## 📂 Project Directory Structure

```text
├── package.json          # Node.js dependencies, environment, and scripts
├── server.js             # Lightweight Express server and static assets router
├── Dockerfile            # Secure Alpine multi-stage production Docker config
├── docker-compose.yml    # Main orchestration composer (exposes Tic-Tac-Toe App)
├── .dockerignore         # Docker context exclusion filter
├── .gitignore            # Git exclusion filter
├── .github/
│   └── workflows/
│       └── ci.yml        # GitHub Actions continuous integration workflow
├── public/               # Frontend Assets
│   ├── index.html        # Glassmorphic single-page game dashboard
│   ├── css/
│   │   └── style.css     # Premium atmospheric visual styling and variables
│   └── js/
│       └── tictactoe.js  # Gameplay loop, Minimax AI, Audio engine, and Stats tracker
└── tests/
    └── server.test.js    # Native backend server integration tests
```

---

## 🚀 Running the Application

### Method 1: Local Development (Node.js)

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Start the application in Development Mode** (utilizes Node's native hot-reloading `--watch` flag):
   ```bash
   npm run dev
   ```

3. **Start in Production Mode**:
   ```bash
   npm start
   ```

4. **Access the application**:
   - **Play Game**: [http://localhost:3000](http://localhost:3000)
   - **Health Checks**: [http://localhost:3000/health](http://localhost:3000/health)

---

### Method 2: Docker Compose (The DevOps Orchestration)

To spin up the containerized production-grade environment:

1. **Launch container stack**:
   ```bash
   docker compose up -d --build
   ```

2. **Verify services**:
   - Check container health status: `docker compose ps`
   - **Play Game**: [http://localhost:3000](http://localhost:3000)

3. **Stop container stack**:
   ```bash
   docker compose down
   ```

---

## 🧪 Running Automated Tests

We leverage the modern **native Node.js test runner** which executes tests with lightning-fast speeds and zero external testing frameworks.

To run the server startup and health probe diagnostics checks:

```bash
npm test
```

---

## 🛡️ DevOps Best Practices Implemented

- **Multi-Stage Build**: Keeps the runtime Docker image extremely slim (only `~50MB` utilizing `alpine` runtimes), cutting out development build layers.
- **Security Isolation**: Container processes do NOT run as root. They run under the rootless `node` user account to prevent privilege escalation vulnerabilities.
- **Container Probing**: Integrated a custom Docker `HEALTHCHECK` running an inline Node fetch. The container will turn `healthy`/`unhealthy` automatically depending on REST health endpoints.
- **CI/CD Automation**: GitHub actions configures tests to run automatically and builds the docker context on every push or merge.
