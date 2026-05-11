# /council-quick — Quick Council Decision Analysis

Convene a three-member rapid Council to analyse the following decision:

**Question:** $ARGUMENTS

Use this command for lower-stakes or time-sensitive decisions. For major decisions, use `/council` (full seven-member panel).

---

## Step 1 — Initialise the shared reasoning file

Create `shared_reasoning.md` in the current directory (overwrite if it exists) with this exact header:

```markdown
# Council Decision Analysis (Quick)

**Question:** $ARGUMENTS

**Date:** [today's date]

**Council:** Quick (3 agents) — Optimist · Devil's Advocate · Realist

---

*Each council member's analysis appears below. Synthesis follows at the end.*

---
```

## Step 2 — Launch 3 council agents in parallel

Use the Task tool to launch three agents simultaneously. Pass each agent:
1. The question: `$ARGUMENTS`
2. The instruction to read `shared_reasoning.md` and append their section to it (using the output format defined in their agent file)
3. A reminder not to overwrite or delete content already in the file

Agents to launch (all in parallel):
- **council-optimist** — "Analyse this question from your optimistic perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-devils-advocate** — "Analyse this question from your devil's advocate perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-realist** — "Analyse this question from your realist perspective and append your section to shared_reasoning.md: $ARGUMENTS"

Wait for all agents to complete before proceeding.

## Step 3 — Synthesise the council's findings

Read `shared_reasoning.md` in full. Then append a synthesis section:

```markdown
---

## Council Synthesis

### Votes at a glance

| Agent | Vote | Confidence | Key point |
|---|---|---|---|
| 🟢 Optimist | [vote] | [confidence] | [one-line key point] |
| 🔴 Devil's Advocate | [vote] | [confidence] | [one-line key point] |
| 🟡 Realist | [vote] | [confidence] | [one-line key point] |

**Tally:** PROCEED: [n] · PROCEED WITH CONDITIONS: [n] · DO NOT PROCEED: [n]

### Key tensions

- [main point of agreement or disagreement between the three agents]
- [second tension or consensus point]

### Open questions

- [question 1 — things that would need to be resolved before deciding]
- [question 2]

---

## Final Recommendation

**[PROCEED / PROCEED WITH CONDITIONS / DO NOT PROCEED]**

[2–3 sentences explaining the recommendation. If PROCEED WITH CONDITIONS, list the conditions clearly.]

---

*For a deeper analysis involving strategic, stakeholder, historical, and first-principles perspectives, run `/council` with the same question.*
```

## Step 4 — Present to the user

After appending the synthesis, tell the user:
1. The final recommendation in bold
2. The vote tally
3. The 2 most important points from the council
4. That the full analysis is in `shared_reasoning.md`
5. That they can run `/council` for a fuller seven-agent analysis if needed
