Modeling Human Reading Time with Transformer-Based Surprisal

## Overview
This project investigates how well modern language models predict human reading behavior. Specifically, we test whether **word surprisal** derived from transformer models explains **self-paced reading times (RTs)** in the Natural Stories Corpus.

We compare:
- **GPT-2 (unidirectional)** — models incremental, left-to-right processing
- **BERT (bidirectional)** — models full-context processing

The goal is to evaluate which model better aligns with human sentence processing.

---

## Dataset
We use the **Natural Stories Corpus**, which contains:
- Naturalistic English texts with complex syntax
- Word-by-word self-paced reading times
- Multiple participants per story

Each word is aligned with:
- Reading time (RT)
- Subject ID
- Model-based surprisal

---

## Methodology

### Data Processing
- Parsed `words.tsv` to extract word-level tokens
- Merged with behavioral RT data
- Constructed unique word sequences per story

### Surprisal Computation
- **GPT-2**: next-token surprisal (incremental)
- **BERT**: masked surprisal (full-context)
- Chunking used to respect model input limits
- Subword probabilities aggregated to word level

### Alignment
- Surprisal computed once per word
- Merged back to all subject-level observations

---

## Statistical Analysis

Mixed-effects regression:
