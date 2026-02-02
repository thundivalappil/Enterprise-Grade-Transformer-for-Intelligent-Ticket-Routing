## Overview

This assignment walks you through building a **Transformer-based text classifier** that automatically routes incoming customer support tickets to the correct queue:

- **Billing**
- **Technical Support**
- **Account / Access**
- **Shipping & Delivery**
- **Returns & Refunds**

The deliverable is a complete, modular project that looks and behaves like a real internal ML/NLP repo:
- data generation (realistic, diverse ticket language),
- deterministic splits,
- Transformer model implementation in **TensorFlow / Keras** (no external transformer libraries required),
- training with callbacks, logging, and artifact outputs,
- evaluation with a confusion matrix and per-class metrics,
- a simple inference CLI for “predict label for this ticket”.

---

## What you will learn

1. **How Transformers work in practice (encoder-style for classification)**  
   Token embedding → positional embedding → multi-head self-attention → feed-forward → pooling → dense classifier.

2. **How to build reproducible NLP pipelines**  
   Fixed seeds, deterministic splits, consistent preprocessing, saved model + metadata.

3. **How to structure ML code like a professional repo**  
   `src/` layout, config-driven experiments, clear entry points (`train.py`, `infer.py`).

4. **How to evaluate NLP models beyond accuracy**  
   Precision/recall/F1 per label, confusion matrix, error sampling.

---

## Assignment Tasks

### Task 1 — Data: Realistic Ticket Generator
You will generate a dataset of customer tickets that resemble real-world messages:
- order IDs, invoice IDs, payment references, tracking numbers,
- common typos, abbreviations, punctuation variance,
- mixed intent patterns (e.g., “refund” + “shipping delay”),
- different writing styles: short, long, angry, polite, corporate.

You will produce:
- `data/raw/tickets.csv` (text + label)
- `data/splits/train.csv`, `valid.csv`, `test.csv`

**Acceptance criteria**
- At least **5 classes**
- At least **5,000 examples** (default generator is larger; configurable)
- Class distribution report printed by the generator

---

### Task 2 — Model: Transformer Encoder Classifier (TensorFlow)
Implement a Transformer encoder block with:
- multi-head self-attention,
- residual connections + layer norm,
- feed-forward network,
- dropout for regularization.

Train it using:
- `TextVectorization` for tokenization,
- embedding + positional encoding,
- global pooling,
- a dense classification head.

**Acceptance criteria**
- Model trains end-to-end with `python -m src.train ...`
- Saves best model to `artifacts/model/`
- Saves vectorizer vocabulary and metadata to `artifacts/`

---

### Task 3 — Evaluation: Metrics and Confusion Matrix
Evaluate on the test set and output:
- accuracy,
- precision/recall/F1 per class,
- confusion matrix image (`artifacts/metrics/confusion_matrix.png`),
- a small set of “hard examples” for manual review.

---

### Task 4 — Inference CLI
Create a CLI script to classify new tickets:

```bash
python -m src.infer --text "My package says delivered but I didn't receive it"
```

Outputs:
- predicted label,
- probability table for all labels.

---

## Deliverables Checklist

- [x] Modular project with `src/` package layout
- [x] Realistic ticket generator + deterministic splits
- [x] Transformer encoder model in TensorFlow/Keras
- [x] Training + evaluation pipeline
- [x] Confusion matrix + per-class metrics
- [x] Inference CLI
- [x] Reproducible configuration & seeds
- [x] README (copy-ready for GitHub)

---

## How to run

### 1) Create environment and install
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
python -m src.infer --text "Card was charged twice for invoice INV-22091"
```

---

## Suggested extensions (optional)

- Add a “multi-label” head for mixed-intent tickets
- Use label smoothing, cosine LR schedule
- Add SHAP-like interpretability (token importance proxies)
- Add lightweight “distilled” model for fast inference
