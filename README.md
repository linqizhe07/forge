# FORGE: Fine-Tuning Over Reward Generations through Evolution

Project page for **FORGE**, a method that reframes LLM-driven reward search around the upstream–downstream factorization of modern reinforcement learning.

🌐 **Live page:** https://linqizhe07.github.io/forge/
📄 **Paper:** [paper.pdf](paper.pdf)

## TL;DR

State-of-the-art LLM reward search trains and **discards** a fresh policy for *every* reward candidate — ignoring policy initialization and reward ordering. FORGE restores that factorization: it pretrains a **task-agnostic skill prior once**, then lets an LLM evolve task rewards while each policy adapts through **closed-form skill projection** and inherits weights across generations. Fitness is measured over the *ordered reward–policy trajectory* rather than each reward in isolation.

## Highlights

- **10× less compute** per reward candidate than the prior automated state of the art, while exceeding it on Humanoid Locomotion and Standup.
- **89.1%** of REvolve's published human-in-the-loop peak on Adroit Hand — fully automated, no per-generation human feedback.
- Just **100 expert episodes** at pretraining inject the missing capability when unsupervised exploration never reaches success states.

## How it works

1. **Task-agnostic skill prior** — a feature map `φ`, prior policy `π₀`, and offline buffer are pretrained once per embodiment via temporal-distance successor features.
2. **Closed-form reward-to-skill projection** — each LLM-generated reward `R` is mapped to a skill vector `z* = (ΦᵀΦ)⁻¹Φᵀr`, giving the child policy a reward-directed initialization.
3. **Cross-generation inheritance** — each child fine-tunes from its parent checkpoint instead of restarting, so fitness reflects cumulative progress along the reward trajectory.

## Repository contents

```
.
├── index.html          # the project page
├── paper.pdf           # full paper
└── assets/figures/     # figures (pipeline, results, ablations)
```

## Citation

```bibtex
@inproceedings{forge2026,
  title     = {FORGE: Fine-Tuning Over Reward Generations through Evolution},
  author    = {Anonymous Author(s)},
  booktitle = {Advances in Neural Information Processing Systems (NeurIPS)},
  year      = {2026},
  note      = {Under review}
}
```

> Author and affiliation are intentionally anonymous for double-blind review. Update this section and the `#` link placeholders in `index.html` (arXiv, Code) once de-anonymized.
