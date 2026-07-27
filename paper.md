---
title: 'Aira-AI: An Educational, From-Scratch Small Language Model for Custom Data Training'
tags:
  - machine learning
  - natural language processing
  - transformers
  - education
  - deep learning
authors:
  - name: Adam Ehan
    affiliation: 1
    corresponding: true
affiliations:
 - name: Independent Researcher / Engineer
   index: 1
date: 27 July 2026
bibliography: paper.bib
---

# Summary

Aira-AI is an open-source educational software package that implements a Small Language Model (SLM) from first principles, including tokenization, embedding layers, multi-head self-attention, and a full training loop. Unlike many public repositories that distribute pre-trained weights or wrap proprietary APIs, Adam-AI is deliberately designed to be trained from an untrained (randomly initialized) state on user-supplied text. This design choice allows learners, educators, and researchers to observe the complete lifecycle of a language model — from random weights to coherent text generation — using only a small, custom text corpus and consumer-grade hardware. The project targets students and practitioners who wish to understand transformer internals experientially rather than through abstraction, and it explicitly supports multilingual corpora, including low-resource languages such as Malayalam.

# Statement of Need

Modern natural language processing education is dominated by two extremes: high-level API usage (e.g., calling a hosted large language model) and dense academic papers describing architectures without accompanying, runnable code. Between these extremes lies a gap for learners who want hands-on experience training a model themselves, on their own data, without requiring institutional-scale compute resources [@vaswani2017attention].

Existing minimal transformer implementations exist in scattered tutorial form, but few are packaged as a maintained, documented, community-extensible repository with clear instructions for custom dataset ingestion. Adam-AI addresses this need by providing:

1. A readable, minimal implementation of the transformer architecture [@vaswani2017attention] suitable for study rather than production deployment.
2. A straightforward data-loading interface (`data/data.txt`) that lowers the barrier to experimenting with custom corpora.
3. Configurable model scale (layers, heads, embedding dimension) so the same codebase can run on a laptop CPU for small experiments or a single consumer GPU for larger runs.
4. Explicit support for non-English and low-resource language training, addressing a common gap in beginner-oriented NLP tooling.

The software is intended for classroom use, self-directed learning, and small-scale research prototyping, rather than as a production-grade language model.

# Functionality

Aira-AI provides the following core components:

- **Tokenizer** (`model/tokenizer.py`): a configurable character- or subword-level tokenizer for converting raw text into model inputs.
- **Transformer core** (`model/transformer.py`, `model/attention.py`): an implementation of multi-head self-attention and feed-forward transformer blocks, following the architecture described by Vaswani et al. [@vaswani2017attention].
- **Training loop** (`train.py`): handles batching, optimization, checkpointing, and loss logging.
- **Inference script** (`generate.py`): generates text samples from a trained checkpoint given a prompt.

Users supply their own training corpus, adjust hyperparameters through a single configuration file, and train a model entirely on their own hardware, retaining full control over the resulting weights and data.

# Acknowledgements

The author thanks the broader open-source machine learning community whose tutorials, implementations, and discussions informed the educational design of this project.

# References
