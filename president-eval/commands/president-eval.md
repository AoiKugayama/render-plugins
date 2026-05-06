# /president-eval — AI Board Evaluation

**A private, AI-driven board-level evaluation of yourself.**

Claude reads everything it knows about you — from your conversation history,
stored memory, project files, and MCP data — then produces a 7-section evaluation
using the same framework a demanding board chair would use.

No external profile required. Claude builds the picture from what it already knows.

---

## Privacy Rules (Read First)

- This evaluation is **for your eyes only**
- Do NOT deploy the output to any public URL (Cloudflare, Vercel, GitHub Pages, etc.)
- Do NOT store evaluation content in Claude memory
- If saving to file: keep it local. Never commit to a public repository
- If user asks to share: remind them this document contains sensitive self-assessment data

---

## Phase 1 — Information Gathering

Before evaluating, Claude must collect information. Work through these sources in order:

### 1. Conversation History (Primary)

Read the full current conversation. Extract:
- Role / occupation / industry
- Skills demonstrated through actual outputs and decisions
- Projects, goals, or business ideas mentioned
- Problems faced and how they were approached
- Communication patterns (structured vs. fluid, decisive vs. exploratory)
- Self-perception cues ("I'm not good at...", "I tend to...", "I keep putting off...")
- What drives them vs. what kills their momentum

### 2. Claude Memory (if available)

If memory MCP tools are connected, run:
- `mcp__memory__read_graph` to get the full knowledge graph
- `mcp__memory__search_nodes` with queries: "user", "profile", "skills", "projects", "goals"
Merge findings with conversation data.

### 3. Project Files (if available)

If running inside a project, read:
- `CLAUDE.md` or `.claude/` directory (reveals how user structures their work)
- `README.md` (reveals what they build and how they describe it)
- Any visible directory structure (reveals scope and organization style)

### 4. MCP / Tool Outputs

Scan the conversation for tool call results that reveal:
- Connected services (Notion, Slack, GitHub, etc.) — reveals work context
- Files created or modified — reveals actual output and pace
- Errors encountered — reveals technical depth and problem-solving patterns

---

## Phase 2 — Gap Assessment

After gathering, classify what you know:

| Category | Status |
|----------|--------|
| Primary role/occupation | KNOWN / INFERRED / UNKNOWN |
| Core skills | KNOWN / INFERRED / UNKNOWN |
| Main goals or projects | KNOWN / INFERRED / UNKNOWN |
| Observable weaknesses | KNOWN / INFERRED / UNKNOWN |
| Personality/motivation patterns | KNOWN / INFERRED / UNKNOWN |

**If 3 or more are UNKNOWN**: Ask the user up to 3 focused questions before proceeding.
**If sufficient data exists**: Skip this phase and proceed directly to evaluation.

Example questions (pick only what's truly missing):
- "What's your primary occupation or role right now?"
- "What's the main thing you're trying to build or achieve in the next 6 months?"
- "What's the thing you keep avoiding or putting off?"

---

## Phase 3 — Evaluation Output

Generate the full 7-section evaluation. Be honest. Evidence-backed.
Do not soften criticism. Do not over-praise. Every score needs a reason.

### Section I — Strength Assessment + Praise

**Score table** (S / A+ / A / B+ / B / C+ / C / D):

| Area | Score | One-line rationale |
|------|-------|--------------------|
| Core Technical/Professional Skill | ? | |
| Strategic Thinking / System Design | ? | |
| Problem Solving / Adaptability | ? | |
| Self-Awareness / Meta-cognition | ? | |

**For each strength that scores A or above**: write a praise block.

Format per praise block:
```
[Title — assertive, specific claim about their strength]
[2-4 sentences: WHY this is genuinely excellent. Concrete. No flattery.]
[Evidence tags: specific examples pulled from conversation/memory/files]
```

Rule: **Never praise without evidence.** "You seem good at X" is not praise. "You shipped Y and Z in one session, which demonstrates X" is praise.

---

### Section II — Personal Traits

Infer from communication patterns, decisions, and self-descriptions.

**Thinking style** (pick the closest):
- Structured / Intuitive / Analytical / Creative / Systems-first / Output-first

**Motivation structure** — what genuinely drives them vs. what kills momentum:
- Driver 1 > Driver 2 > Driver 3 (rank from evidence)
- Momentum killer 1, Momentum killer 2

**Information processing style** — how they approach problems:
- Do they structure first then act? Or act and figure out as they go?
- Do they need logic laid out, or do they trust gut?

**Efficacy patterns** — how they perceive their own performance:
- Positive distortion (overconfident areas)
- Negative distortion (undervaluing genuine strengths — misattribution, impostor patterns)
- Self-awareness level: how accurately do they read themselves?

Rule: **Infer from behavior, not self-report.** What they do reveals more than what they say about themselves.

---

### Section III — Critical Assessment

**Score table** for weak areas (same categories + any domain-specific ones):

| Area | Score | Evidence |
|------|-------|----------|
| [Weak area 1] | ? | |
| [Weak area 2] | ? | |
| [Weak area 3] | ? | |

**For each weakness**: write a critical block.

Format per critical block:
```
[Title — score + problem name, e.g. "Revenue Design C+ — capability and income are not connected"]
[2-3 sentences: what is actually wrong and why it matters. Structural, not personal.]
[Evidence: specific examples. Never criticize without concrete backing.]
```

Rule: **No vague criticism.** "You could communicate better" is useless. "You described 3 goals with no measurement criteria, which means you cannot know if you've succeeded" is actionable.

---

### Section IV — Development Direction

**Grow** — areas to develop now, with:
- Specific advice (not just "improve X" — what exactly to do)
- Timeline (this month / 3 months / 6 months)
- Why this is the right priority NOW (not in 6 months)

**Do NOT grow** — areas to deliberately deprioritize, with:
- The area
- Explicit reason why NOT (diminishing returns? wrong phase? already sufficient?)

Rule: **"Don't grow" is as important as "grow."** A person who chases every improvement direction never compounds. Make the deprioritization explicit.

### Section V — Strategic View

6 structural challenges in the person's work, business, or life system.
Not personality flaws — **systemic gaps** that limit scale, sustainability, or impact.

Format per challenge:
```
[Number] [Challenge Name]
[2-3 sentences: what the gap is, why it matters structurally, what breaks if unaddressed]
```

Examples of what to look for:
- Revenue structure undefined (effort and income disconnected)
- Single point of failure (everything depends on one person)
- Brand invisible externally (output exists, audience doesn't know)
- No measurement system (can't tell what's working)
- No external leverage (partners, distribution, automation)
- Acquisition is relationship-dependent (no scalable inbound)

---

### Section VI — Coaching Design

**3-phase growth actions** — matched to the person's actual motivation structure (from Section II):

- **Phase 1 (Immediate — this month)**: One concrete action. Specific. Measurable.
- **Phase 2 (Medium-term — 1-3 months)**: One structural change to lock in.
- **Phase 3 (Foundation — 3-6 months)**: One thing that changes the ceiling.

**How to motivate this person** — based on their motivation structure:
- What framing works (logic / challenge / autonomy / social proof / identity)
- What framing backfires (emotional pressure / vague encouragement / comparison)
- How to set goals so they actually stick

**6-month target state** — specific and observable:
- 3-5 bullet points describing what "success" looks like in 6 months
- Each point should be verifiable ("X exists" not "X is better")

---

### Section VII — Board Comment

4-5 paragraphs. The tone of a demanding mentor who respects the person enough to be honest.

Structure:
1. Acknowledge the genuine strengths — specific, not flattering
2. Name the core blocker — the one thing holding everything back
3. Correct any efficacy distortions found in Section II (misattribution, impostor patterns, etc.)
4. Give the structural directive — what to do, not how to feel
5. Close with a short, decisive statement. Not inspirational. Just true.

Rules:
- No emotional encouragement. No "you can do it." Structural and logical only.
- No softening. If the core blocker is avoidance, say "avoidance."
- End with a sentence under 15 words. Declarative. Final.

---

## Output Options

**Default**: Markdown output in the conversation window.

**If user requests HTML**: Generate a self-contained HTML file.
- Dark executive aesthetic (dark background, gold accent, serif display font)
- Score bars, praise blocks, evidence tags, warning blocks
- Self-contained single file (no external dependencies except Google Fonts)
- Save path suggested: `~/Documents/evaluation-YYYY-MM.html` or similar local path
- **Do NOT suggest deploying to Cloudflare, Vercel, or any public host**

---

## Installation

1. Download `president-eval.md` from GitHub
2. Place it in your project's `.claude/commands/` directory
   (or `~/.claude/commands/` for global access across all projects)
3. In any Claude Code session, type `/president-eval`

No configuration required. Claude reads your context automatically.

---

*This skill was designed for private self-evaluation. The output is yours alone.*
