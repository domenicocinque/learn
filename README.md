# learn

[![video](assets/thumbnail.png)](https://www.youtube.com/watch?v=kzcI5F4tGiU)

My AI learning system from this video: [How I Use AI to Learn Things](https://www.youtube.com/watch?v=kzcI5F4tGiU).

This is a personal system I built for myself, shared as-is. Built as a pi configuration: the teaching philosophy encoded in a skill, a few small extensions, and agent definitions.

## What's in it

- `skills/teach/` — the philosophy and the process
- `skills/visualize/` — adds a correct, minimal diagram to a lesson when an idea is clearer as a picture
- `skills/flashcards/` — distills a lesson into an Obsidian Spaced Repetition note
- `skills/assessment/` — tests understanding through a creative, artifact-producing task
- `extensions/ask-user-question.ts` — the agent asks you questions through a UI popup
- `extensions/quiz.ts` — graded questions with instant feedback (✓/✗, correct answer, explanation)
- `extensions/md-log.ts` — creates or links a markdown lesson and mirrors the session into it
- `extensions/visual-tools/` — tools for visualization subagents
- `agents/` — `researcher`, `svg-maker`, `mermaid-maker`: the subagents the system delegates to

## Install

This repo **is** a `.pi` directory. From your learning project's root:

```bash
git clone https://github.com/amosblomqvist/learn .pi
```

Then open pi in that directory. (Or copy the pieces you want into your existing project config.)

## Workflow

Start a lesson with one command:

```text
/lesson learning stochastic processes
```

This creates `learning stochastic processes.md`, links the live transcript, and names the Pi session. Then tell Pi what you want to learn.

Resume later with `/resume` inside Pi or `pi -r` at startup and select the named lesson. The markdown link is restored with the session; do not put session IDs in lesson files. Pi automatically compacts long contexts while preserving the full session history.

Create retrieval-practice cards from the lesson:

```text
/skill:flashcards learning stochastic processes.md
```

This writes an Obsidian Markdown deck under `flashcards/`, using the Spaced Repetition plugin's question-and-answer format and native Obsidian math.

After a meaningful learning arc, the teacher offers a creative assessment. You can also request one directly:

```text
/skill:assessment learning stochastic processes.md
```

The assessment is written under `assessments/` and asks you to create an artifact that demonstrates synthesis and transfer. Submit the completed artifact to the same skill for evaluation.

Use `/md-log <filepath>` when you only want to link an existing empty note, and `/md-unlog` to stop logging.

## Requirements

- [pi](https://github.com/earendil-works/pi)
- A subagent implementation, so the system can spawn the researcher and the visual makers. Recommended: [pi-interactive-subagents](https://github.com/amosblomqvist/pi-interactive-subagents) (tmux only). With it, everything works out of the box. Any other implementation works too, but expect to adapt the agent definitions, e.g. `agents/researcher.md` lists `safe_bash` in its tools, which is specific to that extension.
- `ask-user-question` — use the copy bundled here. If your setup already has an `ask-user-question` extension, use **this** one in its place. Popups from different extensions serialize through a shared UI lock, which only works when it's the same implementation.

## Notes

You can run the system without subagents. The main session does the teaching. You just lose the researcher (truth verification) and the generated visuals.

The teaching skill is written for one learner (me). Edit the skill to fit how you learn best.
