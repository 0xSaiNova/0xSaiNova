<p align="center">
  <img src="./header.svg" width="100%" />
</p>

i build autonomous systems that think, negotiate, and act. multi-agent orchestration, on-device SLMs, and tools that actually replace manual work. half my job is prompt engineering. the other half is arguing with a model that's confidently wrong and won't back down. it's like pair programming with someone who read every book but wrote zero code.

<br>

### what i'm working on

**[intentia](https://intentia.ai)** · matchmaking protocol for biotech and CDMOs. autonomous agents that discover, negotiate, and transact at network scale. hybrid SLM framework for on-device reasoning with reliability constraints. basically tinder for pharma, but the agents swipe for you and they never ghost.

**[Intent](https://github.com/IntentAi)** . privacy-first communication platform for everyone who values their privacy and system resources. Built with gamers as the priority, but designed for any community that refuses to trade data for features. Nexus is a Discord alternative where privacy isn't a promise, it's the architecture. The system literally cannot see your private conversations. No facial recognition. No government ID uploads. No surveillance disguised as safety. One you can verify, fork, and control

**[heft](https://github.com/0xSaiNova/heft)** · disk space auditor that actually understands dev toolchains. one command to see where your gigabytes went. it knows the difference between a 4GB cargo target dir and a 4GB photo library. tracks snapshots over time so you can see what grew back after you cleaned up. also rust.

**[keyheat](https://github.com/0xSaiNova/keyheat)** · terminal tool that tracks your keystrokes, WPM, typing trends, and shortcuts in real-time. built in rust. your keyboard has a story, this reads it. yes i built a keylogger on myself. no i will not elaborate.

**multi-agent orchestration** · hierarchical system where agents don't just execute, they plan, delegate, consult each other, and self-correct. three tiers of *trust but verify* with human-supervised quality gates because i've seen what an unsupervised agent does with `sudo` privileges and i don't want to talk about it.

```mermaid
flowchart TB
    USER["task in"] --> BRAIN["orchestrator"]

    BRAIN --> L_UI["lead: ui"]
    BRAIN --> L_BE["lead: backend"]
    BRAIN --> L_DATA["lead: data"]
    BRAIN --> L_TEST["lead: testing"]

    L_UI --> W1["worker 1"]
    L_BE --> W2["worker 2"]
    L_BE --> W3["worker 3"]
    L_DATA --> W4["worker 4"]
    L_TEST --> W5["worker 5"]
    L_TEST --> W6["worker 6"]

    subgraph CONSUL["agents talk to each other"]
        W1 & W2 & W3 & W4
    end

    W1 & W2 & W3 & W4 & W5 & W6 --> GATE["quality gates: 25% · 50% · 75%"]
    GATE --> REVIEW["review + merge"]
    REVIEW --> OUT["shipped"]

    style BRAIN fill:#1a1a2e,stroke:#f0883e,color:#c9d1d9
    style GATE fill:#1a1a2e,stroke:#e3b341,color:#c9d1d9
    style REVIEW fill:#1a1a2e,stroke:#3fb950,color:#c9d1d9
    style USER fill:#0d1117,stroke:#f0883e,color:#c9d1d9
    style OUT fill:#0d1117,stroke:#3fb950,color:#c9d1d9
    style L_UI fill:#161b22,stroke:#30363d,color:#c9d1d9
    style L_BE fill:#161b22,stroke:#30363d,color:#c9d1d9
    style L_DATA fill:#161b22,stroke:#30363d,color:#c9d1d9
    style L_TEST fill:#161b22,stroke:#30363d,color:#c9d1d9
    style W1 fill:#0d1117,stroke:#30363d,color:#8b949e
    style W2 fill:#0d1117,stroke:#30363d,color:#8b949e
    style W3 fill:#0d1117,stroke:#30363d,color:#8b949e
    style W4 fill:#0d1117,stroke:#30363d,color:#8b949e
    style W5 fill:#0d1117,stroke:#30363d,color:#8b949e
    style W6 fill:#0d1117,stroke:#30363d,color:#8b949e
    style CONSUL fill:#0d111700,stroke:#30363d,stroke-dasharray: 5 5,color:#484f58
```

automated model selection (claude / gemini / codex) per task, token budgets with hard caps, parallel execution across isolated git worktrees, and dangerous-op detection that escalates to a human before anything destructive runs. because `rm -rf /` shouldn't be a creative decision made by a model at 3am.

<br>

### things i learned building with LLMs that no docs will tell you

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║  never ask an LLM "are you sure?"                                    ║
║  it'll say yes. every time. make it argue against itself.            ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  context window ≠ understanding window                               ║
║  200K in ≠ 200K understood. CLI overhead eats 6-9%.                  ║
║  ran 208 reqs, 18.6M tokens, 80.7% were cache reads.                ║
║  most tokens aren't thinking, they're remembering.                   ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  sandbox everything. trust nothing.                                  ║
║  an agent will nuke your codebase out of confidence.                 ║
║  isolated worktrees. destructive ops get escalated.                  ║
║  treat it like an intern with root access.                           ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  never let the student grade their own homework                      ║
║  every quality gate uses a different model to verify.                ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

<br>

### tools i think with

```
languages     python · rust · typescript · javascript · sql
frontend      astro · react · html · css · tailwind
ml            pytorch · transformers · scikit-learn · langchain · embeddings · RAG
agents        multi-agent orchestration · MCP tool-use · prompt engineering · RLVR
infra         docker · azure · postgresql · mongodb · redis · anthropic sdk
```

<br>

### the tldr

- **[intentia](https://intentia.ai)** · co-founder. matchmaking protocol for biotech/CDMOs. agents that discover and transact autonomously.
- **6 AI agents** orchestrated across UI, backend, data, and testing with automated quality gates
- **automation engineering** · turned a $500/4-week manual process into $30/24hrs
- **autonomous trading system** · transformer + RLHF + real P&L as reward signal. self-funded tuition from profits.

<br>

if any of this sounds interesting or you want to argue about agent architectures, [dm me on linkedin](https://www.linkedin.com/in/saisaranu/). i respond faster than my agents. lower hallucination rate too.

<p align="center">
  <a href="mailto:sai.saranu1@gmail.com"><img src="https://img.shields.io/badge/email-sai.saranu1%40gmail.com-c9d1d9?style=flat-square&logo=gmail&logoColor=white&labelColor=0d1117" /></a>
  <a href="https://www.linkedin.com/in/saisaranu/"><img src="https://img.shields.io/badge/linkedin-saisaranu-f0883e?style=flat-square&logo=linkedin&logoColor=white&labelColor=0d1117" /></a>
  <a href="https://intentia.ai"><img src="https://img.shields.io/badge/intentia.ai-3fb950?style=flat-square&logo=safari&logoColor=white&labelColor=0d1117" /></a>
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=0xSaiNova&style=flat-square&color=f0883e&label=profile+views" />
</p>
