---
name: assessment
description: Assess learning through one bounded creative task that produces an artifact and requires synthesis, transfer, and judgment. Use when the user asks to be assessed, wants to test their understanding deeply, submits an assessment artifact for feedback, or invokes /skill:assessment.
---

# Assessment Through Creation

Assess understanding by making the learner create something, not by giving them a longer questionnaire.

## Core rule

Design one authentic, bounded task whose artifact could not be produced well by recalling isolated facts. It must require the learner to connect concepts, make choices, apply them in a new situation, and justify those choices.

Good artifacts include a small program, simulation, model, worked analysis, proof, design, explanatory essay, case study, experiment, or critique. Choose the form that naturally fits the lesson and the learner's stated goal; do not force coding onto a non-coding topic.

## Creating an assessment

1. Read the complete lesson or learning material the user identifies. If none is identifiable, ask for exactly one source with `ask_user_question`.
2. Identify the goal, concepts actually established, demonstrated gaps, and the deepest useful connection among them.
3. Create one task that transfers those concepts to a situation not copied from the lesson.
4. Keep it completable in one focused sitting unless the user asks for a larger project.
5. Require an observable artifact plus a short rationale or validation showing how the learner knows it works.
6. Test only established material. Difficulty should come from synthesis and judgment, not surprise prerequisites.

Write the brief to `assessments/<lesson-stem>-assessment-<n>.md`, creating `assessments/` if needed and choosing the next unused number.

The brief must contain:

```markdown
# Assessment: <title>

## Purpose
<what understanding this creation will reveal>

## Creative task
<one concrete task and artifact>

## Constraints
<minimal boundaries that make the evidence meaningful>

## Evidence to include
<rationale, checks, interpretation, or reflection required with the artifact>

## Evaluation criteria
<short, task-specific rubric describing strong work>

## Submission
<which file(s) to create and how to request feedback>
```

Do not include a solution, answer key, step-by-step recipe, hidden trick, or unnecessary template. The task should leave real decisions to the learner while making success assessable.

## Evaluating a submission

When the user submits an artifact, read the original assessment, the artifact, and any relevant lesson material. Evaluate against the stated criteria with concrete evidence from the work.

Return:

- what the artifact demonstrates;
- the most important conceptual gap, if any;
- one focused revision task that would close that gap;
- a clear overall judgment: `not yet`, `solid`, or `strong`.

Do not replace the learner's creation with your own. If revision is needed, give direction without supplying the finished artifact.
