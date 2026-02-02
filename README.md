# Transformer Ticket Router (TensorFlow) — End‑to‑End NLP Assignment

**GitHub summary (≤350 chars):** Build a production‑style Transformer text classifier in TensorFlow to auto‑route customer tickets (Billing, Technical, Account, Shipping, Returns). Includes realistic ticket generator, clean train/eval pipeline, metrics + confusion matrix, and an inference CLI. Modular, reproducible, GitHub‑ready.

---

## What this repo contains
A complete Transformer **text classification** assignment in **TensorFlow/Keras** that routes customer tickets into operational queues:
Billing • Technical • Account • Shipping • Returns

✅ Realistic ticket generator (orders, invoices, tracking, payment refs)  
✅ Modular `src/` codebase (train/eval/infer)  
✅ Custom Transformer encoder (no external transformer libs needed)  
✅ Metrics + confusion matrix output  
✅ Saved model artifacts + vocabulary + metadata  

---


## Production upgrades included

- Warmup + cosine learning rate schedule (config-driven)
- Class weights for imbalanced labels
- Mixed precision training (toggle in config)

## Quickstart

### 1) Install
```bash
pip install -r requirements.txt
```

### 2) Generate dataset
```bash
python -m src.data.generate_tickets --n_samples 12000 --out_dir data
```

### 3) Train
```bash
python -m src.train --config configs/base.json
```

### 4) Evaluate
```bash
python -m src.evaluate --config configs/base.json
```

### 5) Inference
```bash
python -m src.infer --text "My package says delivered but I didn't receive it"
```

---

## Repo structure

```
transformer-assignment-ticket-routing/
  configs/
    base.json
  data/
    (generated)
  artifacts/
    (generated)
  src/
    data/
      generate_tickets.py
      io.py
      splits.py
    models/
      transformer.py
    utils/
      seed.py
      text.py
      metrics.py
    train.py
    evaluate.py
    infer.py
  requirements.txt
  PUBLISH_NARRATIVE.md
```

---

## Assignment brief
See **PUBLISH_NARRATIVE.md** for the full narrative, tasks, and acceptance criteria.
