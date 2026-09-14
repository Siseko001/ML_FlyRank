# Demo outline — "Which page should you fix first?"

A ~5-minute walkthrough of the capstone project. Built to follow the same tension-and-resolution
thread as the paper itself: a real question, an honest comparison, a result that isn't what you'd
expect, and what to actually do with it.

## 1. The hook (30 sec)
Open with the scenario, not the pipeline: a content lead has forty visible pages and time to
review three or four this week. Which ones? State the twist immediately — a one-sentence rule
beat a trained machine learning model at answering that question, and the reason why is more
useful than the win itself.

## 2. The data and the rule (60 sec)
- One line on the dataset: 30,000 anonymized pages, 12,023 visible enough to judge (≥500
  impressions/90d, ranked top 20).
- Show the rule out loud: `score = (tier median CTR − page CTR) × impressions`. Emphasize it's
  readable in one breath — no fitted weights, no black box.
- Mention the reason codes briefly — every flagged page comes with a plain-English "why."

## 3. The honest comparison (90 sec) — the centerpiece
- Show the precision@K chart (`docs/img/precision_at_k.png`).
- State the result plainly: the rule wins at every K; both models score at or below random.
- Give the actual reason, not just the number: both models' top picks were pages with exactly
  zero recorded engagement — precisely what the evaluation check treats as "unmeasured," not
  "confirmed weak." A model chasing its training label found that pattern efficiently; the
  metric was built to distrust it.
- One sentence on why this matters beyond this project: a good AUC on the training label doesn't
  guarantee a good ranking on the metric that actually matters to the business.

## 4. The twist — turning the audit around (45 sec)
Briefly mention the same leakage/validation checks were run against two findings in FlyRank's own
published research paper — and one held up worse than expected (a "top predictor" turned out to
be a literal component of the label it was predicting). Keep this to one or two sentences; it's a
supporting beat, not the main act.

## 5. The close — what to actually do (45 sec)
- The recommendation: ship the rule, not the model, plus why (readable, auditable, and it wins).
- One caveat that matters: this is decision-support for review order, not a click guarantee, and
  never a way to judge who wrote a page.
- End on reproducibility: every number in the demo comes from a runnable notebook, same seed,
  same split, linked from the paper.

## If there's time for questions
Likely ones to have an answer ready for:
- "Why not just use the model anyway, since it's more sophisticated?" → sophistication that loses
  the actual metric isn't sophistication, it's overfitting to the wrong target.
- "What would make the model version viable?" → a fix to how zero-engagement rows are treated,
  and probably a different evaluation label than the CTR-gap proxy.
- "Does this generalize past the starter dataset?" → not validated at warehouse scale (57 brands,
  341,701 pages) — flagged explicitly as a limitation, not glossed over.
