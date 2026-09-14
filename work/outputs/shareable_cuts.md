# Shareable cuts

Two repurposed cuts of the same capstone project, for different audiences. Paper:
https://siseko001.github.io/ML_FlyRank/

## Social post

I built a CTR-opportunity scorer for an SEO dataset — then tried to beat it with real ML. A
transparent rule (CTR gap × impression volume, compared within position tier) won at every
cutoff against a logistic regression and random forest, trained on the same 25 features. Both
models scored *below* random chance on the held-out metric — their top picks turned out to be
pages with zero recorded engagement, exactly what the evaluation check is built to exclude.

Full writeup + reproducible notebooks: https://siseko001.github.io/ML_FlyRank/

*(pair with docs/img/precision_at_k.png)*

## Employer 3-sentencer

Built and honestly evaluated a CTR-opportunity ranking system on a 30,000-page SEO dataset
(12,023 eligible pages, real client-grouped holdout). A transparent scoring rule outperformed a
logistic regression and random forest at the actual task, and I diagnosed *why* the models lost
rather than just reporting it. The project also includes a leakage audit of the source research
paper's own published findings and a fully reproducible, publicly deployed paper.
