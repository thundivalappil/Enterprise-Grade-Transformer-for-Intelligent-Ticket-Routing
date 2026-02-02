# Grading rubric (suggested)

## 1) Data (25%)
- Generator produces >= 5k examples
- Includes realistic identifiers (order, invoice, tracking, payment)
- Noise/typos controlled by parameters
- Stratified train/valid/test splits

## 2) Model (35%)
- Correct Transformer encoder block
- Mask-aware pooling
- Training runs end-to-end with config
- Saves best model and metadata

## 3) Evaluation (25%)
- Classification report (per-class precision/recall/F1)
- Confusion matrix image
- Hard examples exported for review

## 4) Engineering quality (15%)
- Clean modular structure
- Reproducibility (seed + deterministic pipeline)
- Clear README + commands
