# ML Workspace

Practice-first path from "built a cats-vs-dogs model once" to "can advise companies and build custom models as a service."

## How this works

You learn by shipping **missions** (real projects with real datasets), not by reading first. The numbered topic folders exist so that every keyword you hit during a mission has a short, plain-language guide waiting. Read a guide when a mission sends you there, not before.

## Structure

```
ML/
├── ROADMAP.md            The path: which mission when, and what each unlocks
├── datacenter/           Shared dataset storage (one place, all missions) — see its README
├── 00-foundations/       The vocabulary everything else uses (train/test, loss, metrics, overfitting)
├── 01-classical-ml/      Tabular data: regression, trees, gradient boosting — most business problems live here
├── 02-deep-learning/     Neural nets and PyTorch: layers, backprop, training loops
├── 03-computer-vision/   CNNs, transfer learning, image models
├── 04-nlp/               Text: embeddings, transformers, fine-tuning vs prompting
├── 05-time-series/       Forecasting: demand, prices, traffic
├── 06-mlops/             Getting models into production: serving, monitoring, drift
├── 07-advisory/          The consulting layer: scoping, when NOT to build a model, pricing
└── missions/             The actual projects. Start here.
```

Each topic folder has a `GUIDE.md`: what it is, the keywords decoded, what to actually master, and what an advisor needs to know about it.

## Environment setup (once)

```bash
cd /Users/symwn/Desktop/M87.nosync/ML
python3 -m venv .venv
source .venv/bin/activate
pip install pandas numpy scikit-learn matplotlib jupyter torch torchvision xgboost
```

Activate with `source .venv/bin/activate` at the start of every session.

## Where to start

Open `missions/README.md`, read the mission protocol (2 minutes), then start `missions/mission-01-churn/MISSION.md`.
