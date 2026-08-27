# Missions — Protocol

Missions are real projects with real datasets and a defined end-model. You'll implement them *with Claude*, and that's the trap this protocol exists to avoid: if Claude just writes everything, you'll ship a model and learn nothing. These rules make the collaboration teach.

## The rules (paste-able preamble)

Start every mission work session by telling Claude:

> We're working on missions/mission-XX per the mission protocol in missions/README.md. Instructor mode: explain each concept briefly BEFORE writing code that uses it. Before every training run or evaluation, ask me to predict the result and only then run it. At each stage gate, quiz me with the checkpoint questions and don't continue until I've answered in my own words. Keep code minimal and readable — no clever abstractions. Log surprises and my wrong predictions in LEARNINGS.md.

Why each rule works:
- **Explain-before-code** — you read the concept while it's about to become concrete, not in the abstract.
- **Predict-before-run** — prediction is the fastest test of understanding. Wrong predictions are the highest-value moments; that's the model of ML in your head getting corrected.
- **Stage gates with explain-back** — a stage is done when *you* can explain it, not when the code runs. The checkpoint questions are written in each MISSION.md.
- **LEARNINGS.md** — your journal per mission. Surprises, wrong predictions, "aha" moments. This becomes your future case-study raw material.

## Stage structure

Every mission is split into stages. Each stage lists: **Build** (what gets implemented), **Learn** (concepts it forces, with guide links), **Checkpoint** (questions you answer before moving on). One stage per session is a good pace; two is fine.

## Done means

1. Success criteria in the MISSION.md met (honest numbers, untouched test set).
2. All checkpoints answered.
3. A short case-study writeup (`WRITEUP.md`): problem → approach → numbers → what you'd tell a paying client. This is your advisory portfolio building itself.

## Missions

| # | Mission | Domain | Status |
|---|---------|--------|--------|
| 01 | [Customer Churn](mission-01-churn/MISSION.md) | Tabular / classical ML | ready |
| 02 | [Pet Breed Classifier](mission-02-pet-breeds/MISSION.md) | Vision / deep learning | ready |
| 03 | Support-ticket classifier (NLP) | to be defined after 02 | — |
| 04 | Sales forecasting (time series) | to be defined | — |
| 05 | Deploy the churn model (MLOps) | to be defined | — |
