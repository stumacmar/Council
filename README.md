# Council — Multi-Agent Decision Framework for Claude Code

A structured decision-making system using 7 specialist sub-agents that each analyse a question from a distinct perspective, write to a shared file, and are synthesised by the main session.

## Setup

Copy the `.claude/` folder into your project root (or `~/.claude/` for global use):

```
your-project/
└── .claude/
    ├── agents/
    │   ├── council-optimist.md
    │   ├── council-devils-advocate.md
    │   ├── council-realist.md
    │   ├── council-strategist.md
    │   ├── council-stakeholder-advocate.md
    │   ├── council-first-principles.md
    │   └── council-historian.md
    └── commands/
        ├── council.md
        └── council-quick.md
```

## Usage

### Full council (all 7 agents)

```
/council Should we restructure the finance function before the audit?
/council Is this the right time to make an offer on the Hexham property?
/council Should we proceed with the France motorhome trip in July given the budget position?
```

### Quick council (3 agents — faster, for lower-stakes decisions)

```
/council-quick Should I upgrade the Bürstner's bike rack before the trip?
/council-quick Which campervan insurance provider should I renew with?
```

## The Agents

| Agent | Colour | Core question |
|---|---|---|
| Optimist | 🟢 | What could go RIGHT? |
| Devil's Advocate | 🔴 | What could go WRONG? |
| Realist | 🟡 | Is this actually FEASIBLE? |
| Strategist | 🔵 | Is this the right move NOW? |
| Stakeholder Advocate | 🟣 | Who is AFFECTED and how? |
| First Principles | ⚪ | Are we asking the RIGHT QUESTION? |
| Historian | 📚 | Has this been tried BEFORE? |

## Output

Each run produces a `shared_reasoning.md` file in the current directory containing:

- Each agent's full analysis
- A synthesis table showing how each agent voted
- Where the council agrees and disagrees
- Open questions to resolve
- A final recommendation: **PROCEED** / **PROCEED WITH CONDITIONS** / **DO NOT PROCEED**

## Tips

- For important decisions, run `/council` and review `shared_reasoning.md` in full before deciding
- The Strategist and First Principles agents are particularly valuable for board-level decisions
- The Stakeholder Advocate is critical for anything involving organisational change
- You can invoke individual agents directly via Claude Code's Task tool if you only need one perspective
- Store `shared_reasoning.md` files in a `/decisions/` folder as an audit trail over time
