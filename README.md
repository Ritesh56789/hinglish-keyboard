# PBoard — Context-Aware Hinglish Predictive Keyboard

A lightweight, edge-deployable predictive typing system for Hinglish (Hindi-English code-mixed text), powered by a 13.6M-parameter Word-Level LSTM.

> ⚠️ This repo currently contains data assets and the technical write-up. Model training/inference code to be added separately.

## Highlights

- **BDCI (Bi-Directional Contextual Intersection)** — context-based lexical normalization algorithm, 99.9% precision, avoids cross-language hallucinations seen with FastText.
- **Balanced tone classification** across 2.37M training rows (Casual/Neutral/Formal).
- **O(1) vocabulary lookup** via `word2idx`/`idx2word` hash maps.
- **Dynamic OOV masking** and per-user style personalization.
- **13.6M params, <25MB**, Perplexity ≈ 23.5 — built for edge deployment.

Full write-up: [`PBoard_Project.pdf`](./PBoard_Project.pdf)

## Contents

| File | Description |
|---|---|
| `PBoard_Project.pdf` | Full technical report |
| `word2idx.json` / `idx2word.json` | Vocabulary maps |
| `verified_sandwich_map.json` | Validated BDCI normalization pairs |
| `oov_map.json` | Shortform/typo → root word mappings |
| `user_profile.json` | Sample personalization data |
| `demo_whatsapp_chat.txt` | Sample raw chat data |

## Pipeline

Normalize → Encode → Predict (LSTM) → Decode → Personalize
