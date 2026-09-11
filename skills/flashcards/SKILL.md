---
name: flashcards
description: Create Obsidian Spaced Repetition flashcards from a completed or ongoing lesson. Use when the user asks for flashcards, spaced-repetition material, or invokes /skill:flashcards with a lesson file.
---

# Flashcards

Turn a lesson into a small, high-quality Obsidian flashcard note. Distill; do not transcribe.

## Input

The user should provide a lesson Markdown path, for example:

```text
/skill:flashcards @learning stochastic processes.md
```

If no source is identifiable, ask for exactly one lesson file with `ask_user_question`. Read the complete file, continuing in chunks when needed.

## Select knowledge

Create cards only for correct concepts that were established in the lesson. Learner mistakes and “I don't know” answers indicate what to prioritize, but are not themselves source material.

Prefer knowledge that is:

- needed to derive other ideas;
- easy to confuse with a nearby concept;
- useful outside the original example;
- likely to decay without retrieval practice.

Exclude lesson logistics, duplicated explanations, trivia, uncorrected claims, and material the lesson has not yet established.

## Write cards

- Test active production, not recognition: no multiple-choice, true/false, or yes/no cards.
- Keep one retrievable idea per card.
- Make each front understandable without the lesson open.
- Keep answers concise, but include the reasoning needed to reconstruct the fact.
- Prefer prompts such as “Why…?”, “Derive…”, “Predict…”, or “What distinguishes…?” when appropriate.
- Do not create reverse cards unless the user explicitly asks for them.
- Use the smallest useful set; do not chase a card count.

## Output

Write `flashcards/<lesson-stem>.md`, creating `flashcards/` if needed. If that file already exists, ask before replacing it.

Use the Obsidian Spaced Repetition plugin's multi-line basic format for every card:

```markdown
# Flashcards: <lesson title>

Source: [[<lesson-stem>]]

#flashcards/<lesson-slug>

<front>
?
<back>

<next front>
?
<next back>
```

The line containing `?` separates front from back; a blank line ends the card. Do not put blank lines inside a card. Keep ordinary Obsidian Markdown, including `$...$` and `$$...$$` math, unchanged so it renders natively. Use fenced code only when it fits without internal blank lines; otherwise prefer a short inline-code example.

Use only forward cards. Bidirectional cards (`:::` or `??`) create siblings and should be added only if the user explicitly asks for them.

After writing, report the path and card count only.
