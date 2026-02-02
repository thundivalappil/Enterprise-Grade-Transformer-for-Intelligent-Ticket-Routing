# Transformer Ticket Router (TensorFlow) — End‑to‑End NLP Assignment

## Title
Transformer Ticket Router (TensorFlow) — End‑to‑End NLP Assignment

## GitHub 350-character summary
Build a production‑style Transformer text classifier in TensorFlow to auto‑route customer tickets (Billing, Technical, Account, Shipping, Returns). Includes realistic ticket generator, clean train/eval pipeline, metrics + confusion matrix, and an inference CLI. Modular, reproducible, GitHub‑ready.

## What you must submit
- The full repo structure as provided
- Generated dataset CSVs (optional to commit; recommended to regenerate)
- Model artifacts (optional)
- A short write-up: what worked, what failed, what you would improve

## Minimum commands to prove it works
```bash
pip install -r requirements.txt
python -m src.data.generate_tickets --n_samples 12000 --out_dir data
python -m src.train --config configs/base.json
python -m src.evaluate --config configs/base.json
python -m src.infer --text "Refund not received for return RMA-10231"
```
