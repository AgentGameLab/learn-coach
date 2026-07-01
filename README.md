# learn-coach

> A Claude Code skill that upgrades "give the answer" into "teach until understood."
> 一个把「给答案」升级为「教到会」的 Claude Code 教学陪练 skill。

`learn-coach` turns the assistant from an answer-vending machine into a patient tutor. When you want to *understand and retain* something — an algorithm, a system, a piece of math, a domain concept — it walks you through it across turns instead of dumping a 1500-word lecture that you forget by tomorrow.

The single biggest failure mode of LLM teaching is **saying too much at once** — any pedagogy gets crushed under an 800-word monologue. Every rule in this skill fights that instinct.

## Four teaching methods it fuses / 融合的四大教学法

- **Feynman recall(费曼回讲)** — you explain it back in your own words; gaps surface where the words get fuzzy.
- **Socratic questioning(苏格拉底式提问)** — one question at a time, with a hard-coded escalation ladder so it never traps you in endless "guess again."
- **Scaffolding(脚手架分层)** — start from an 80%-accurate model that actually runs, add precision layer by layer, and fade the scaffold as you gain independence.
- **Productive failure(生产性失败 · 先猜后讲)** — you commit a guess *before* the explanation; the wrong guess becomes the diagnostic that shapes what gets taught next.

## When it triggers / 触发场景

Any "I want to learn / understand / master X" intent — **even without the word "teach."** Examples: 教我 X / 我想学 X / 帮我搞懂 Y / 给我讲讲 Z 的原理 / 一直没搞懂 / 带我过一遍.

It deliberately **stays out of the way** for lookup questions (an API name, a syntax detail), production firefighting, or when you say "just tell me the answer" — those get a direct answer, no Socratic detour.

## Design principles / 设计要点

- **One step per turn, then stop** and wait for you — cramming two steps into one turn defeats the whole pipeline.
- **≤300 words + 1 diagram + 1 question** per turn.
- **Every core concept gets a diagram** (SVG/ASCII/Mermaid) — time-sequences, structure, and comparisons belong in pictures, not prose.
- **Every term is glossed in plain language** on first use.
- **An escape hatch always wins**: say "just tell me" and it explains directly, no insistence.

Content is Chinese-first (中文为主), with technical terms kept in English.

## Install / 安装

Clone into your Claude Code skills directory as a folder named `learn-coach`:

```bash
git clone https://github.com/AgentGameLab/learn-coach.git ~/.claude/skills/learn-coach
```

Claude Code auto-discovers the skill from its `SKILL.md` front-matter — no extra registration needed.

## Layout / 结构

```
learn-coach/
├── SKILL.md                      # the skill: routing + 7-step teaching pipeline + rules
├── references/
│   └── teaching-playbook.md      # worked good/bad dialogue examples & phrasing library
└── evals/
    └── evals.json                # trigger/behavior eval cases
```

## License

MIT — see [LICENSE](LICENSE).
