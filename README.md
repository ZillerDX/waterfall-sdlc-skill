# Waterfall SDLC for AI Agents 🏗️

<div align="center">

[![Live Interactive Showcase](https://img.shields.io/badge/Live%20Showcase-zillerdx.github.io%2Fwaterfall--sdlc--skill-2563eb?style=for-the-badge&logo=google-chrome&logoColor=white)](https://zillerdx.github.io/waterfall-sdlc-skill/)
<br>

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Antigravity Compatible](https://img.shields.io/badge/Antigravity-Compatible-4285F4.svg)](https://antigravity.google)
[![Claude Code Ready](https://img.shields.io/badge/Claude%20Code-Ready-D97706.svg)](https://anthropic.com)
[![Cursor Ready](https://img.shields.io/badge/Cursor-Ready-0ea5e9.svg)](https://cursor.com)
[![Codex Ready](https://img.shields.io/badge/Codex-Ready-10b981.svg)](https://github.com/features/copilot)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen.svg)](https://github.com/ZillerDX/waterfall-sdlc-skill/pulls)

</div>

> 🌐 **Interactive Web Showcase & Simulator**: **[https://zillerdx.github.io/waterfall-sdlc-skill/](https://zillerdx.github.io/waterfall-sdlc-skill/)**  
> Explore the live 7-phase animated lifecycle, interactive terminal simulator, and copyable prompt templates.

---

## ⚡ The Problem: AI "Premature Coding"

When developers ask an AI to *"build an application"* or *"add a major feature"*, standard AI behavior is to jump straight into writing code:
- ❌ **No Scope Boundaries**: Hallucinating features, missing essential edge cases, or ballooning project scope.
- ❌ **Missing Architecture**: Improvising database schemas and API contracts on the fly, leading to painful refactors.
- ❌ **Zero Evidence**: Declaring "all tasks complete" without automated test proof or build verification.

**Waterfall SDLC** enforces an uncompromising engineering standard: **"No Coding Before Design Sign-off."**

---

## 🧭 The 7-Phase Quality Gate Lifecycle

Every phase requires a concrete, verifiable **Gate Deliverable** before the AI agent is permitted to advance to the next phase:

```mermaid
graph TD
    P1["1. Requirements Gathering<br/>(Scope, User Stories & Acceptance Criteria)"] -->|Gate 1 Sign-off| P2["2. Feasibility & Analysis<br/>(Tech Stack, Dependencies & Risk Matrix)"]
    P2 -->|Gate 2 Sign-off| P3["3. Architectural Design<br/>(DB Schema, API Specs, Component Tree)"]
    P3 -->|Gate 3 Sign-off| P4["4. Implementation (Coding)<br/>(100% Blueprint-Adherent Clean Code)"]
    P4 -->|Gate 4 Pass| P5["5. Verification & Testing<br/>(Unit/Integration Tests, 100% Pass Rate)"]
    P5 <-->|Agile Inner Loop: Bugfix & Refactor| P4
    P5 -->|Gate 5 Pass (100% Proof)| P6["6. Deployment & Packaging<br/>(Build Verification, .env.example, Docker)"]
    P6 -->|Gate 6 Sign-off| P7["7. Support & Handover<br/>(README, Runbooks & Health Monitoring)"]
```

| Phase | Core Objective | Gate Deliverable |
| :--- | :--- | :--- |
| **1. Requirements** | Pin down functional/non-functional goals, personas, and boundaries | Requirements Specification + Acceptance Criteria |
| **2. Analysis** | Evaluate tech stack compatibility, dependencies, and architectural risks | Tech Stack Decision Matrix + Risk Mitigation Plan |
| **3. Design** | Produce complete technical blueprints before writing a single line of code | ERD / Database Schema + API Contracts + UI Hierarchy |
| **4. Implementation** | Translate the approved design into modular, clean, strongly-typed code | Complete codebase with zero syntax/type errors |
| **5. Testing** | Formally prove that the implementation satisfies all initial requirements | Pre-Flight Port Check + Automated Test Suite (Exit Code: 0) |
| **6. Deployment** | Package release artifacts for reproducible, error-free execution | Verified Production Build + Docker / Deployment Scripts |
| **7. Support** | Ensure long-term maintainability and operational clarity | Complete README + Runbook + **Clickable Localhost Preview** |

> [!NOTE]
> **Anti-Rigidity Guardrail (Agile Inner Loop 4 ⇄ 5)**:
> Waterfall SDLC must **never** become an inflexible bureaucracy that hinders rapid iterative bug fixing or refactoring.
> - **High-Speed Feedback Loop**: When unit tests fail or styling bugs emerge in Phase 5, the agent immediately refactors and fixes code directly in Phase 4 and re-tests in Phase 5. No administrative overhead or re-starting from Phase 1 is required for implementation-level defects.
> - **Escalation Threshold**: Only escalate back to Phase 1 or 3 if the user explicitly changes feature scope or if a fundamental architectural flaw requires updating the schema.

> [!IMPORTANT]
> **Zero Port Collision & Instant Preview Guarantees**:
> 1. **Mandatory Pre-Launch Port Purge (Check & Kill First)**: Agents running Waterfall SDLC *must* run the automated port purge command to inspect and forcefully kill any stale process occupying the target port before launching servers:
>    - **Windows**: `Get-NetTCPConnection -LocalPort <port> -ErrorAction SilentlyContinue | ForEach-Object { Stop-Process -Id $_.OwningProcess -Force -ErrorAction SilentlyContinue }`
>    - **Linux / macOS**: `fuser -k <port>/tcp 2>/dev/null || lsof -ti :<port> | xargs -r kill -9 2>/dev/null || true`
> 2. **Terminate Background Tasks**: If a dev server was previously launched in the background, the agent must terminate it cleanly before starting a new one.
> 3. **Mandatory Clickable Link**: The agent *must* output a direct, clickable markdown link (e.g. `👉 **Live Local Preview**: [http://localhost:3000](http://localhost:3000)`) in the chat so you can test the app with a single click.

---

## 🚀 Quickstart & Installation

Select your platform below. All commands are verified and copy-paste ready for **macOS / Linux (Bash)** and **Windows (PowerShell)**.

### 1. Google Antigravity (Global Plugin)
Installs globally across all projects on your machine:

- **macOS / Linux / WSL**:
  ```bash
  git clone https://github.com/ZillerDX/waterfall-sdlc-skill.git ~/.gemini/config/plugins/waterfall-sdlc
  ```
- **Windows (PowerShell)**:
  ```powershell
  git clone https://github.com/ZillerDX/waterfall-sdlc-skill.git "$HOME\.gemini\config\plugins\waterfall-sdlc"
  ```

---

### 2. Per-Project / Universal Agents (`.agents`)
Installs inside a specific repository for any agent conforming to the `.agents/skills` standard:

- **macOS / Linux / WSL**:
  ```bash
  mkdir -p .agents/skills/waterfall-sdlc
  curl -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md \
    -o .agents/skills/waterfall-sdlc/SKILL.md
  ```
- **Windows (PowerShell)**:
  ```powershell
  New-Item -ItemType Directory -Force -Path ".agents\skills\waterfall-sdlc" | Out-Null
  curl.exe -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md -o ".agents\skills\waterfall-sdlc\SKILL.md"
  ```

---

### 3. Claude Code (Anthropic)
Installs into Claude Code global skills:

- **macOS / Linux / WSL**:
  ```bash
  mkdir -p ~/.claude/skills/waterfall-sdlc
  curl -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md \
    -o ~/.claude/skills/waterfall-sdlc/SKILL.md
  ```
- **Windows (PowerShell)**:
  ```powershell
  New-Item -ItemType Directory -Force -Path "$HOME\.claude\skills\waterfall-sdlc" | Out-Null
  curl.exe -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md -o "$HOME\.claude\skills\waterfall-sdlc\SKILL.md"
  ```

---

### 4. Cursor (.cursor/rules)
Installs as an automated project rule for Cursor IDE:

- **macOS / Linux / WSL**:
  ```bash
  mkdir -p .cursor/rules
  curl -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md \
    -o .cursor/rules/waterfall-sdlc.mdc
  ```
- **Windows (PowerShell)**:
  ```powershell
  New-Item -ItemType Directory -Force -Path ".cursor\rules" | Out-Null
  curl.exe -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md -o ".cursor\rules\waterfall-sdlc.mdc"
  ```

---

### 5. OpenAI Codex & Autonomous Agents (`.codex/skills`)
Installs into OpenAI Codex, GitHub Copilot instructions, or multi-agent workflows:

- **macOS / Linux / WSL**:
  ```bash
  mkdir -p .codex/skills/waterfall-sdlc
  curl -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md \
    -o .codex/skills/waterfall-sdlc/SKILL.md
  ```
- **Windows (PowerShell)**:
  ```powershell
  New-Item -ItemType Directory -Force -Path ".codex\skills\waterfall-sdlc" | Out-Null
  curl.exe -sSL https://raw.githubusercontent.com/ZillerDX/waterfall-sdlc-skill/main/skills/waterfall-sdlc/SKILL.md -o ".codex\skills\waterfall-sdlc\SKILL.md"
  ```

---

## 💡 Practical Prompt Templates

### 🌟 1. Full-Stack Application from Scratch
```text
I want to build a "Personal Portfolio & Showcase" web application.
Please enforce the Waterfall SDLC skill strictly:
- Start with Phase 1: Requirements Gathering and define the Acceptance Criteria.
- Proceed to Phase 2 & 3: Propose the Tech Stack (Next.js, Tailwind, Supabase) and produce the Database Schema + API Contract.
- STOP and present the Architectural Blueprint for my approval before writing any code.
```

### 🛠️ 2. Complex Backend Service / Microservice
```text
We need to design and build an authenticated Payment Webhook service with Stripe.
Apply Waterfall SDLC:
1. Specify all webhook event types and failure handling requirements.
2. Design the idempotent database schema and transaction state machine.
3. Once approved, implement with TDD (unit tests first) and verify exit code 0.
```

### 🎨 3. Enterprise Design System & Dashboard
```text
Create an Analytics Dashboard following Waterfall SDLC and frontend-design standards:
- Outline user journeys, metrics, and chart requirements first.
- Present layout tokens, typography hierarchy (tracking-tight), and vector iconography (Lucide only, no emojis).
- Build and verify locally on localhost before release.
```

---

## 🤝 Synergy with the Modern AI Toolchain

- **`frontend-design`**: Seamlessly pairs with Phase 3 & 4 to eliminate amateur UI slop, enforce vector icons, and deliver Linear/Stripe-caliber aesthetics.
- **`superpowers`**: Power up Phase 4 & 5 with Test-Driven Development (TDD) and Systematic Debugging.
- **`github-mcp-server`**: Execute Phase 6 & 7 by automatically opening structured Pull Requests with requirement traceability.
- **`claude-mem` / `context-mode`**: Persist architectural choices across multi-session sprints without context bloat.

---

## 📄 License

Distributed under the **MIT License**. See [LICENSE](LICENSE) for more information.

Developed with ❤️ by [Tanathon Chanapha (ZillerDX)](https://github.com/ZillerDX).