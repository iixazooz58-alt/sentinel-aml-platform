# Sentinel — AML & Fraud Detection Compliance Platform (Showcase)

**Live demo:** https://claude.ai/artifact/JN8zMkpAkWRBxRhHqo5ksn
**Languages:** English / العربية (full bilingual UI, RTL-aware)

A single-page, interactive showcase of **Sentinel**, a conceptual anti-money-laundering (AML) and fraud-detection compliance platform. It was built as a portfolio/demo piece for a *Software/AI Engineer, Compliance Technology* role, to communicate how an ML-driven AML system, its model pipeline, its governance process, and its LLM-assisted investigation layer fit together — end to end, with real numbers and clearly-labeled illustrative examples.

## What's inside

- **Dashboards** for the AML and fraud-detection engines, with working filters (click a filter and the KPI tiles re-animate / re-aggregate — no fabricated "live" data, just real numbers recomputed and re-rendered).
- **Eight detailed, animated system flowcharts** (SVG, hand-built, bilingual labels), each with a concrete "live example" walkthrough, covering:
  1. System architecture overview
  2. AML detection flow
  3. Fraud detection flow
  4. Model training & ablation flow
  5. AI governance flow (capability → verification → risk tiering → sign-off → monitoring)
  6. SAMA regulatory-compliance mapping (crosswalk from SAMA AML/CTF rulebook pillars to concrete engineering controls)
  7. End-to-end data pipeline (`schema_gate.py` → AS-OF feature building → stacked model → evidence/decision)
  8. RAG + LLM investigator agent + API architecture (retrieval-augmented case investigation, grounded in the SAMA rulebook, internal policy, and prior case narratives)
- **Model internals**: an interactive XGBoost split-gain / leaf-weight calculator, and an explanation of the stacked (XGBoost + graph + statistical features) ensemble.
- **AI governance register**: every AI-assisted capability in the system is tagged with its verification status (real evaluation run vs. code-review-only vs. prototype/unverified), so the showcase never overstates what has actually been measured.

## Honesty / data disclaimers

This is a **demonstration project**, not a production system and not a regulated financial product:

- The AML detection threshold (0.1319) is a genuinely calibrated operating point from model runs on labeled data; the accept/escalate/freeze triage bands (0.30 / 0.65) are **illustrative**, not derived from a regulatory or statistical process.
- Training data referenced: IBM's **HI-Small** AML dataset (fully synthetic transaction graph, not real individuals) and the **ULB `creditcard.csv`** dataset (real, anonymized European card transactions, Sept. 2013, 492 frauds / 284,807 rows).
- Every "live example" box on the flowcharts is explicitly labeled as either an **illustrative scenario** (hypothetical, for explanatory purposes) or a **real result** (restates an actual measured figure) — the two are never blended.
- The SAMA compliance flowchart is an **engineering mapping** of Sentinel's controls against publicly available SAMA AML/CTF rulebook requirements. It is not a certification, audit, or legal compliance opinion.

## Running it

This is a single self-contained `index.html` (no build step, no dependencies) plus one video asset.

**Locally:**
```bash
git clone <this-repo-url>
cd sentinel-aml-platform
# just open index.html in a browser, or serve it:
python3 -m http.server 8000
# then visit http://localhost:8000
```

**On GitHub Pages:**
1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under "Build and deployment", set **Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Save — GitHub will publish it at `https://<your-username>.github.io/<repo-name>/`.

(The included `.nojekyll` file disables Jekyll processing, which is unnecessary here and can interfere with files/folders starting with `_`.)

## Structure

```
.
├── index.html           # the entire application (markup, CSS, JS, inline SVG diagrams)
├── hero_animation.mp4   # looping hero background video
├── .nojekyll             # tells GitHub Pages to serve files as-is
└── README.md
```

## License

MIT — see [LICENSE](LICENSE). Feel free to fork/adapt for your own portfolio, but please don't present it as a real, certified, or production AML system — it isn't one.
