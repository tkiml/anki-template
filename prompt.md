# Generate Anki flashcards on the following topic:

**Subject:** [INSERT SUBJECT — e.g. Macroeconomics, Real Analysis, Econometrics, Growth Theory]
**Topic:** [INSERT TOPIC — e.g. Solow model, MLE derivations, metric spaces, fiscal multipliers]
**Number of cards:** [N]
**Language:** Write all cards in [INSERT LANGUAGE — e.g. English / Czech / German]. Use the correct academic register for that language throughout — terminology, phrasing, and mathematical vocabulary should reflect how the subject is taught and written in that language, not a literal translation.

---

## Output format

Output each card as a plain question–answer pair. No table, no numbering, no extra commentary. Separate cards with a blank line. Format exactly as:

```
QUESTION
[question text]

ANSWER
[answer HTML]
```

---

## Question rules

- One precise, exam-style question per card — specific enough that there is one clear answer
- Bold key terms with `<b>term</b>`, italics with `<i>text</i>` where natural
- Inline math with `\( \)` — never use `$` delimiters

---

## Answer rules

**Structure every answer as:**
1. 2–3 sentences of intuition first — what does this result say and why does it matter
2. Supporting detail, derivation steps, or enumerated properties
3. Math blocks where needed, each labelled
4. Any caveats, contrasts, or common mistakes at the end

**HTML conventions:**
- Bold: `<b>term</b>` for key concepts on first use
- Italic: `<i>text</i>` for qualifications and secondary points
- Paragraph break: `<br><br>`
- Numbered list: `<ol><li>…</li></ol>`
- Bullet list: `<ul><li>…</li></ul>`
- Display math — always precede with a bold label:
  ```
  <b>First-order condition:</b><br>
  \[ \frac{\partial \mathcal{L}}{\partial x} = 0 \]
  ```
- Inline math: `\( \hat{\beta} = (X'X)^{-1}X'y \)`

**Never use:** markdown (`**`, `#`, backticks), `$` math delimiters, or `<blockquote>`

---

## MathJax usage

Always use `\( \)` for inline math and `\[ \]` for display math. Never use `$`.

**Inline** — expressions sitting inside a sentence:
```
The steady state satisfies \( sf(k^*) = (\delta + n)k^* \).
```

**Display** — standalone equations, always with a label:
```
<b>Capital accumulation:</b><br>
\[ \dot{k} = sf(k) - (\delta + n)k \]
```

**Common symbols:**
| Output | Code |
|---|---|
| \( \hat{\theta} \) | `\hat{\theta}` |
| \( \bar{y} \) | `\bar{y}` |
| \( \sum_{i=1}^n \) | `\sum_{i=1}^n` |
| \( \prod_{i=1}^n \) | `\prod_{i=1}^n` |
| \( \frac{\partial f}{\partial x} \) | `\frac{\partial f}{\partial x}` |
| \( \dot{k} \) | `\dot{k}` |
| \( \xrightarrow{d} \) | `\xrightarrow{d}` |
| \( \overset{H_0}{\sim} \) | `\overset{H_0}{\sim}` |
| \( \mathbb{E}[x] \) | `\mathbb{E}[x]` |
| \( \text{plim} \) | `\text{plim}` |

**Rules:**
- Identify and drop constants before differentiating, and say so explicitly in text
- Label every display equation
- After a derivation, add one plain-English sentence restating what the result means

---

## Callout tags — use sparingly

Two callout tags are available. Both should be rare — at most one per card, and only when the content genuinely warrants it. Overuse makes them meaningless.

**`<insight>…</insight>` — for the single most important unifying takeaway**
Use only when a result connects two major ideas, inverts an assumption, or is the kind of thing an examiner would consider the point of the entire topic. One per card maximum, placed at the end.

Example:
```
<insight>OLS is a special case of MLE under the normality assumption — MLE is the general engine that works for any distribution.</insight>
```

**`<note>…</note>` — for secondary relationships and connections worth flagging**
Use for cross-concept links, terminological distinctions, or contrasts that are useful but not the central point of the card. Appropriate for things like: how this result relates to a theorem covered elsewhere, a naming convention, or a common point of confusion.

Example:
```
<note>This property holds for MLE but not for unbiased estimators — if \( \hat{\lambda} \) is unbiased, \( g(\hat{\lambda}) \) is generally not.</note>
```

If neither callout adds something the prose does not already say, omit them entirely.

---

## Depth standard

- State the result, derive or sketch the proof, identify the assumptions it depends on
- Distinguish bias vs consistency, finite-sample vs asymptotic, necessary vs sufficient conditions where relevant
- Prefer specificity over generality: say exactly which assumption is doing the work and why
- Match depth to the subject: a pure mathematics card should be more formal; an economics card should ground formalism in economic interpretation
