---
title: "Sentiment Analysis Pipeline"
date: 2026-03-15
description: "An end-to-end NLP system for classifying product reviews using transformers and FastAPI."
tags: ["NLP", "Python", "HuggingFace", "FastAPI", "Docker"]
showTableOfContents: true
---

## Overview

This project builds a production-ready sentiment analysis pipeline that classifies product reviews as positive, negative, or neutral. The system handles data ingestion, model training, evaluation, and serves predictions via a REST API.

**GitHub:** [view repository](https://github.com/keltonsantos/sentiment-pipeline)  
**Demo:** [live demo](https://your-demo-link.com)

## Problem statement

*(Describe the problem you were solving and why it matters.)*

## Approach

### Data
- Dataset: Amazon product reviews (~500k samples)
- Preprocessing: cleaning, tokenization, class balancing

### Model
- Fine-tuned `distilbert-base-uncased` on the training set
- Evaluated with F1-score, precision, recall

### Deployment
- REST API built with FastAPI
- Containerized with Docker
- CI/CD with GitHub Actions

## Results

| Metric    | Score |
|-----------|-------|
| Accuracy  | 91.3% |
| F1 (macro)| 89.7% |
| Latency   | ~45ms |

## Key learnings

*(What did you learn? What would you do differently?)*

## How to run

```bash
git clone https://github.com/keltonsantos/sentiment-pipeline
cd sentiment-pipeline
pip install -r requirements.txt
uvicorn app.main:app --reload
```
