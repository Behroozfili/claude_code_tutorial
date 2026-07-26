# Claude Code Tutorial — Learn from Scratch

<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-CLI-412991?style=for-the-badge&logo=anthropic&logoColor=white"/>
  <img src="https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Apache_Airflow-Pipeline-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white"/>
</p>

> A hands-on, full-course repository for mastering **Claude Code** — Anthropic's AI-powered CLI for software development. Covers everything from basic LLM calls to production-grade agents, custom skills, MCP integrations, and automated Airflow pipelines.

**Watch the full tutorial on YouTube:** [Claude Code Full Course](https://youtu.be/lkc-F5I8gFE?si=MFLyX0RVkcHrM2nr)

---

## What You'll Learn

| Module | Topics Covered |
|---|---|
| LLM Basics | Direct Claude API calls, prompt engineering |
| `.claude` Folder | CLAUDE.md conventions, settings, MCP config |
| Custom Skills | Building reusable skill scripts (fetchAPI, migrate, visualize) |
| Agents | Creating specialized sub-agents (code_reviewer, orchestrator) |
| Hooks | Pre/post script automation with `pre_script.py` / `post_script.py` |
| Data Pipelines | ETL with CSV/Parquet, Apache Airflow DAGs |
| MCP Integration | Connecting external tools via Model Context Protocol |

---

## Repository Structure

```
claude_code_tutorial/
└── Claude_Code_Full_Course/
    ├── .claude/
    │   ├── CLAUDE.md                  # Project rules & conventions
    │   ├── settings.json              # Claude Code configuration
    │   ├── .mcp.json                  # MCP server definitions
    │   ├── hooks/
    │   │   ├── pre_script.py          # Runs before each Claude action
    │   │   └── post_script.py         # Runs after each Claude action
    │   ├── skills/
    │   │   ├── fetchAPI/              # Skill: fetch and store API data
    │   │   │   └── SKILL.md
    │   │   ├── migrate/               # Skill: convert CSV → Parquet
    │   │   │   └── SKILL.md
    │   │   └── visualize/             # Skill: generate charts from data
    │   │       └── SKILL.md
    │   └── agents/
    │       ├── code_reviewer/         # Specialized code review agent
    │       └── orchestrator/          # Multi-agent orchestrator
    ├── Airflow_Project/
    │   ├── dags/
    │   │   ├── data_fetch.py          # DAG: fetch external data
    │   │   └── data_report.py         # DAG: generate reports
    │   └── README.md
    ├── Data/                          # Sample datasets (CSV)
    ├── 1_llm_call.ipynb               # Notebook: first LLM API call
    ├── create_dataframe.py            # Utility scripts
    ├── fetch_api_data.py
    ├── generate_dataframe.py
    └── pyproject.toml
```

---

## The `.claude` Folder — Command Center

The `.claude` folder is how you configure Claude Code's behavior for your project:

```
.claude/
├── CLAUDE.md          ← Project rules: code style, do's and don'ts
├── settings.json      ← Tool permissions, hooks, model settings
├── .mcp.json          ← MCP server connections (external tools)
├── hooks/             ← Shell/Python scripts triggered on events
├── skills/            ← Reusable task scripts Claude can invoke
└── agents/            ← Specialized sub-agents with focused roles
```

### Skills Included

| Skill | What It Does |
|---|---|
| `fetchAPI` | Fetches data from an external API and saves timestamped CSV snapshots |
| `migrate` | Converts CSV data to Parquet format for efficient downstream processing |
| `visualize` | Generates matplotlib charts (sales trends, returns by product/store) |

### Agents Included

| Agent | Role |
|---|---|
| `code_reviewer` | Reviews code for quality, patterns, and duplication |
| `orchestrator` | Coordinates multi-step tasks across skills and agents |

---

## Quick Start

### Prerequisites

- [Claude Code CLI](https://claude.ai/code) installed
- Python 3.11+ with `uv` or `pip`
- Anthropic API key

### Setup

```bash
git clone https://github.com/Behroozfili/claude_code_tutorial.git
cd claude_code_tutorial/Claude_Code_Full_Course

# Install dependencies
pip install -r requirements.txt
# or with uv:
uv sync
```

### Run the first notebook

```bash
jupyter notebook 1_llm_call.ipynb
```

### Try a Skill

```bash
# Inside the project directory with Claude Code running:
claude   # opens interactive session

# Then invoke a skill:
/fetchAPI
```

### Airflow Pipeline

```bash
cd Airflow_Project
# Set AIRFLOW_HOME and initialize DB, then trigger:
airflow dags trigger data_fetch
```

---

## Key Concepts

### Hooks
Hooks run automatically around Claude actions:
- `pre_script.py` — runs before Claude executes a tool (e.g., validate state)
- `post_script.py` — runs after a tool completes (e.g., log results, notify)

### MCP (Model Context Protocol)
MCP lets Claude Code connect to external tools (databases, APIs, browsers) via a standardized JSON-RPC protocol. Configured in `.mcp.json`.

---

## Resources

- [Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)
- [Anthropic API Reference](https://docs.anthropic.com/en/api)
- [MCP Specification](https://modelcontextprotocol.io)
- [Full YouTube Course](https://youtu.be/lkc-F5I8gFE?si=MFLyX0RVkcHrM2nr)

---

## License

MIT
