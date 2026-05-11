# /council — Full Council Decision Analysis

Convene the full seven-member Council to analyse the following decision:

**Question:** $ARGUMENTS

---

## Step 1 — Initialise the shared reasoning file

Create `shared_reasoning.md` in the current directory (overwrite if it exists) with this exact header:

```markdown
# Council Decision Analysis

**Question:** $ARGUMENTS

**Date:** [today's date]

**Council:** Full (7 agents) — Optimist · Devil's Advocate · Realist · Strategist · Stakeholder Advocate · First Principles · Historian

---

*Each council member's analysis appears below. Synthesis follows at the end.*

---
```

## Step 2 — Launch all 7 council agents in parallel

Use the Task tool to launch all seven agents simultaneously. Pass each agent:
1. The question: `$ARGUMENTS`
2. The instruction to read `shared_reasoning.md` and append their section to it (using the output format defined in their agent file)
3. A reminder not to overwrite or delete content already in the file

Agents to launch (all in parallel):
- **council-optimist** — "Analyse this question from your optimistic perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-devils-advocate** — "Analyse this question from your devil's advocate perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-realist** — "Analyse this question from your realist perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-strategist** — "Analyse this question from your strategist perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-stakeholder-advocate** — "Analyse this question from your stakeholder advocate perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-first-principles** — "Analyse this question from your first-principles perspective and append your section to shared_reasoning.md: $ARGUMENTS"
- **council-historian** — "Analyse this question from your historian perspective and append your section to shared_reasoning.md: $ARGUMENTS"

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
| 🔵 Strategist | [vote] | [confidence] | [one-line key point] |
| 🟣 Stakeholder Advocate | [vote] | [confidence] | [one-line key point] |
| ⚪ First Principles | [vote] | [confidence] | [one-line key point] |
| 📚 Historian | [vote] | [confidence] | [one-line key point] |

**Tally:** PROCEED: [n] · PROCEED WITH CONDITIONS: [n] · DO NOT PROCEED: [n]

### Where the council agrees

- [point of consensus 1]
- [point of consensus 2]

### Where the council disagrees

- [point of divergence 1 — which agents are on each side]
- [point of divergence 2]

### Open questions to resolve before deciding

- [question 1]
- [question 2]

### Conditions that would change the verdict

- [condition 1 — what would need to be true to shift from current recommendation]
- [condition 2]

---

## Final Recommendation

**[PROCEED / PROCEED WITH CONDITIONS / DO NOT PROCEED]**

[2–3 sentences explaining the recommendation, integrating the strongest arguments from across the council. If PROCEED WITH CONDITIONS, list the conditions clearly.]
```

## Step 4 — Present to the user

After appending the synthesis, tell the user:
1. The final recommendation in bold
2. The vote tally
3. The 2–3 most important points from the council
4. That the full analysis is in `shared_reasoning.md`
