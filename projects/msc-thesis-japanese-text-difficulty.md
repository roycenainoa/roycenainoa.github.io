---
layout: project
type: project
image: img/difficulty/degree_difficulty.jpg
title: "Japanese Text-Difficulty Prediction (M.Sc. Thesis)"
date: 2026
published: false
labels:
  - Machine Learning
  - NLP
  - Transformers
  - Python
  - Research
summary: "M.Sc. thesis — a cross-domain comparison of feature-based and transformer-based approaches to predicting the reading difficulty of Japanese text."
---

<img class="img-fluid" src="../img/difficulty/degree_difficulty.jpg" style="width:100%; max-width:620px; border:1px solid #e5e7eb; border-radius:6px;">

## About

My M.Sc. thesis studies **how well Japanese text-difficulty prediction generalizes across domains.** Text-difficulty (readability) prediction estimates how hard a passage is to read — useful, for example, for grading learning material by JLPT level. The question I focus on is what happens when a model trained on one kind of text is asked to score a *different* kind.

## What it compares

- **Feature-based (classical) models** — linguistic features (lexical, syntactic, and script-based signals) with traditional machine-learning classifiers.
- **Transformer-based models** — fine-tuned language models.

Both are evaluated **in-domain and cross-domain** (for example, trained on general text and tested on exam-style text) to measure how much accuracy each approach loses when the domain shifts, using an ordinal agreement metric suited to graded difficulty labels.

_This project is not yet public — the thesis is still in progress, so this entry is kept hidden (`published: false`) until release._
