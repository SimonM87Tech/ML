# MLOps (models in production)

Everything between "the notebook works" and "the client's business runs on it." This is where you already have an unfair advantage — it's mostly software engineering, which you do daily.

## Keywords decoded

- **Model serialization** — saving trained weights to a file (`joblib` for sklearn, `torch.save` / **ONNX** for portability). The model becomes an artifact like any build output.
- **Serving / inference endpoint** — wrapping the model in an API. FastAPI + a `/predict` route covers most client needs. **Batch inference** (nightly scoring of all customers) is often better than a live endpoint — cheaper, simpler, and usually what the business flow actually needs.
- **Latency vs throughput** — one prediction fast vs millions per hour. Different architectures; ask which one the client means.
- **Model registry / versioning** — which model version is live, what data trained it, can we roll back. **MLflow** is the standard tool; a disciplined folder + metadata file gets small clients 80% of the way.
- **Experiment tracking** — logging every training run's params and scores (MLflow, Weights & Biases). Replaces "which notebook cell produced the good model?"
- **Data drift** — production inputs drifting from training data (new customer segment, price changes). **Concept drift** — the world's rules changed (post-COVID demand). Both silently rot accuracy.
- **Monitoring** — track prediction distributions and, where ground truth arrives later (churn: you find out in 3 months), actual accuracy over time. Alert on drift.
- **Retraining pipeline** — scheduled or drift-triggered re-run of training on fresh data. Cron + script beats a fancy platform for most clients.
- **Feature store** — centralized, consistent feature computation for training and serving. Enterprise concern; know the term, don't build one for an SMB.

## What to master

Mission 05: serve the churn model via FastAPI in Docker, log inputs, add a drift check, write the retraining script. That end-to-end loop, once, teaches 90% of this.

## Advisor lens

This is your differentiator against data scientists: you can actually ship. Pitch accordingly — "I build models *and* the production system around them." Also the honest warning every client needs: a model is not a one-time deliverable; without monitoring and retraining, it quietly degrades. That maintenance need is a real cost for them — and a retainer opportunity for you.
