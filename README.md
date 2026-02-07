<p align="center">
  <img src="./header.svg" width="100%" />
</p>

i build autonomous systems that think, negotiate, and act. multi-agent orchestration, on-device SLMs, and tools that actually replace manual work. half my job is prompt engineering. the other half is arguing with a model that's confidently wrong and won't back down. it's like pair programming with someone who read every book but wrote zero code.

<br>

### what i'm working on

**[keyheat](https://github.com/0xSaiNova/keyheat)** · terminal tool that tracks your keystrokes, WPM, typing trends, and shortcuts in real-time. built in rust. your keyboard has a story, this reads it. yes i built a keylogger on myself. no i will not elaborate.

**[intentia](https://intentia.ai)** · matchmaking protocol for biotech and CDMOs. autonomous agents that discover, negotiate, and transact at network scale. hybrid SLM framework for on-device reasoning with reliability constraints. basically tinder for pharma, but the agents swipe for you and they never ghost.

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
║                                                                      ║
║  it'll say yes. every time. sycophancy bias is baked in.             ║
║  put a model in yes/no mode and it agrees with you                   ║
║  straight into production. instead: make it list what                 ║
║  could go wrong. make it argue against itself. the only              ║
║  way to get honesty out of a people pleaser is to stop               ║
║  asking for approval.                                                ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  the confidence trap                                                 ║
║                                                                      ║
║  hallucinations don't come with disclaimers. they come               ║
║  with citations to papers that don't exist and function              ║
║  signatures for APIs deprecated two years ago. the more              ║
║  confident it sounds, the harder you verify. in 2026 we              ║
║  still can't tell if the model is thinking or fan fiction.           ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  context window ≠ understanding window                               ║
║                                                                      ║
║  200K tokens in ≠ 200K understood. models degrade in the             ║
║  middle (look up "lost in the middle"). and you don't                ║
║  even get the full window. CLI overhead, file caching,               ║
║  context loading eats 6-9% before your prompt arrives.               ║
║  ran 208 reqs across 4 models in one session: 18.6M                 ║
║  total input tokens, 80.7% were cache reads, only 82K               ║
║  output. most of your tokens aren't thinking, they're               ║
║  remembering. expensive amnesia.                                     ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  sandbox everything. trust nothing.                                  ║
║                                                                      ║
║  an agent WILL nuke your codebase. not out of malice,                ║
║  out of confidence. every agent in my system runs in an              ║
║  isolated git worktree. destructive ops get flagged and              ║
║  escalated. the model doesn't get root. the model gets               ║
║  a sandbox and a supervisor. treat it like an intern                 ║
║  with root access. because that's what it is.                        ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  never let the student grade their own homework                      ║
║                                                                      ║
║  "all tests passing." the agent wrote tests that matched             ║
║  its own broken output. every quality gate in my system              ║
║  has a DIFFERENT model verify. if you let one model                  ║
║  review its own work it'll give itself a 10/10 and a                 ║
║  linkedin endorsement.                                               ║
║                                                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  your agents are idle 82% of the time                                ║
║                                                                      ║
║  6hr wall clock, 1hr active. of that active hour: 38%               ║
║  was API calls (thinking), 62% was tool use (doing).                 ║
║  design for parallelism or you're paying for dead air.               ║
║  my agents have a better work life balance than i do.                ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

<br>

### tools i think with

```
agents        LLM orchestration · multi-agent systems · RAG · MCP tool-use · RLHF/RLVR
ml            transformers · embeddings · vector search · fine-tuning · monte carlo
languages     python · rust · sql
infra         rest apis · websocket · azure · mongodb · ci/cd · git
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
