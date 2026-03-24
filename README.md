# @sero-ai/plugin-research

Multi-agent research orchestrator for Sero — decompose any question into
parallel workstreams, monitor progress, handle stuck agents, and synthesize
results into a unified document.

## Features

- **Multi-agent research** — `/research [question]` decomposes topics into 2-4
  parallel agent workstreams that run simultaneously
- **Article analysis** — `/analyze [urls]` analyses articles for commercial
  opportunities and actionable insights
- **Live progress tracking** — web UI shows real-time agent activity, tool
  calls, and line counts
- **Stuck agent detection** — monitors agents at escalating intervals and
  flags those that stop making progress
- **Auto-synthesis** — when all agents complete, a synthesis agent
  automatically produces a unified document with cross-cutting insights

## Sero Plugin Install

Install in **Sero → Admin → Plugins** with:

```text
git:https://github.com/monobyte/sero-research-plugin.git
```

Sero clones the source repo, installs its dependencies locally, builds the UI,
and then hot-loads the plugin into the sidebar.

## Pi CLI Usage

Install as a Pi package:

```bash
pi install npm:@sero-ai/plugin-research
```

The agent gains a `research` tool (plan, approve, status, cancel, analyze) and
`/research` + `/analyze` commands. A `research` skill is also registered for
prompt-based orchestration.

## Commands

| Command | Description |
|---------|-------------|
| `/research [question]` | Start a multi-agent research session |
| `/analyze [urls] [context]` | Analyse articles for commercial opportunities |

## Tool Actions

| Action | Description |
|--------|-------------|
| `plan` | Decompose a question into research workstreams |
| `analyze` | Set up article analysis workstreams |
| `approve` | Launch the planned agents |
| `status` | Check progress and detect stuck agents |
| `cancel` | Cancel active research |

## State File

```
workspace-root/
└── .sero/
    └── apps/
        └── research/
            └── state.json
```

## Skills

This plugin includes a `research` skill at `skills/research/SKILL.md` that
provides the agent with detailed orchestration instructions for both research
and article analysis modes.

## Development

```bash
npm install
npm run dev        # Start dev server on port 5191
npm run build      # Build for production
npm run typecheck  # Typecheck UI
```
