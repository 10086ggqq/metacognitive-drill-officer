# Metacognitive Drill Officer (Universal)

> A quiz skill that never teaches you new material — it only exposes the "illusion of competence".
> The user does exactly two things: **type a knowledge point**, and **(optionally) upload screenshots or files of original questions**.

[中文版 README](./README.md)

## Why it exists

The most dangerous illusion in learning: **"I understood it" = "I master it"**. Recognizing the right answer ≠ deriving it independently; reading a definition ≠ explaining it to someone else. This skill is built on four principles from cognitive science:

| Principle | Mechanism in this skill |
|-----------|-------------------------|
| Familiar ≠ Mastered | No multiple choice anywhere — independent derivation is mandatory |
| Recognition ≠ Recall | Active-recall check (STAGE 1) + Feynman output (STAGE 6) |
| Working memory is limited | Complex problems are split into ≤3 cognitive chunks (STAGE 2) |
| Metacognitive calibration | Every answer is preceded by a correctness prediction, compared against actual result |

## Workflow

```
User provides a knowledge point + question screenshots/files
        │
        ▼
 Transcription & confirmation list (asks when unclear, never guesses)
        ▼
STAGE 0  Confidence rating (0%–100%)
STAGE 1  Active-recall check ── fail → re-learn, then retest from this stage
STAGE 2  Chunked questions (≤3 steps, every step justified)
STAGE 3  10 original questions Q1–Q10 (per question: output / correctness prediction /
         predicted failure point / feedback)
STAGE 4  Variant attack questions Qx-Vn (NOT counted toward the 10; ≥2 per round)
STAGE 5  Blind-spot locator (predict the failure point before answering)
STAGE 6  Feynman output (explain it to a total beginner)
STAGE 7  [Mandatory reflection gate] per-question review + reflection +
         reusable techniques (≥3) + re-rated confidence
STAGE 8  100-point anti-luck judgment
         ├── ≥70 → STAGE 9
         └── <70 → one more set of 10 (user-supplied / new variants, or mixed), redo 7–8
STAGE 9  Summary document (.md + .pdf): full timeline table,
         first-output vs last-output comparison, improvement list
```

### Scoring (100 points total)

| Component | Points |
|-----------|--------|
| Independent accuracy on the 10 original questions | 40 |
| Independent accuracy on variant questions | 20 (if <2 variants used, merges into original-question score → 60) |
| Reflection quality (honest / specific / reusable techniques) | 20 |
| Metacognitive calibration (prediction vs actual) | 10 |
| Feynman output quality | 10 |

## Installation & usage

Drop the whole `metacognitive-drill-officer/` folder into your agent's skills directory.

From the **user** side, one sentence is enough, e.g.:

> "检测我是否掌握了三角函数诱导公式" (with a screenshot of your workbook)
> "quiz me on Python list comprehensions"

Supported uploads: image screenshots/photos, PDF, Word, txt/md.
- Blurry or incomplete screenshots → the officer asks, it never guesses;
- Question count ≠ 10 → you pick 10, or it fills in and labels the extras;
- Knowledge point only → it authors 10 questions itself and states the topic distribution.

## Repository structure

```
metacognitive-drill-officer/
├── SKILL.md                      # Main file: role, iron rules, 9-stage workflow, prohibitions
└── references/
    └── report-templates.md       # Per-question report / reflection script / timeline table / doc skeleton
```

## Subject coverage

- **STEM**: independent derivation/calculation, every step justified
- **Languages / humanities**: dictation, sentence-making, examples, near-synonym discrimination
- **Programming**: hand-written code, output prediction, complexity justification
- **Medicine / law** and other memory-heavy fields: same active-recall + variant + Feynman combo

## FAQ

**Q: What happens if I score below 70?**
It tells you plainly that "below 70 means you may have just been lucky", then assigns one more set of 10 questions (supplied by you or re-authored as new variants), repeating until you pass or quit.

**Q: What if PDF generation fails?**
It outputs the full Markdown and tells you to export it as PDF manually — no content is ever omitted.

**Q: Will it give me the answers?**
No. Its job is to expose your blind spots, not to teach.

## License

[MIT](./LICENSE)
