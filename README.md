<p align="center">
  <img src="./header.svg" width="100%" />
</p>

i build autonomous systems that think, negotiate, and act. multi-agent orchestration, on-device SLMs, and tools that actually replace manual work. half my job is prompt engineering. the other half is arguing with a model that's confidently wrong and won't back down. it's like pair programming with someone who read every book but wrote zero code.

<br>


**[heft](https://github.com/0xSaiNova/heft)** · disk space auditor that actually understands dev toolchains. one command to see where your gigabytes went. it knows the difference between a 4GB cargo target dir and a 4GB photo library. tracks snapshots over time so you can see what grew back after you cleaned up. also rust.

**[keyheat](https://github.com/0xSaiNova/keyheat)** · terminal tool that tracks your keystrokes, WPM, typing trends, and shortcuts in real-time. built in rust. your keyboard has a story, this reads it. yes i built a keylogger on myself. no i will not elaborate.


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
║  200K in ≠ 200K understood. CLI overhead eats 10-12%.                  ║
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


<p align="center">
  <a href="mailto:sai.saranu1@gmail.com"><img src="https://img.shields.io/badge/email-sai.saranu1%40gmail.com-c9d1d9?style=flat-square&logo=gmail&logoColor=white&labelColor=0d1117" /></a>
  <a href="https://www.linkedin.com/in/saisaranu/"><img src="https://img.shields.io/badge/linkedin-saisaranu-f0883e?style=flat-square&logo=linkedin&logoColor=white&labelColor=0d1117" /></a>
  <a href="https://intentia.ai"><img src="https://img.shields.io/badge/intentia.ai-3fb950?style=flat-square&logo=safari&logoColor=white&labelColor=0d1117" /></a>
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=0xSaiNova&style=flat-square&color=f0883e&label=profile+views" />
</p>
