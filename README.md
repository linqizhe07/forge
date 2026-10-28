# FORGE: Fine-Tuning Over Reward Generations through Evolution

Project page for **FORGE**, a method that reframes LLM-driven reward search around the upstream–downstream factorization of modern reinforcement learning. Linqi Zhe, GRASP Laboratory, University of Pennsylvania. Preprint, 2026.

🌐 **Live page:** https://linqizhe07.github.io/forge/
📄 **Paper:** [paper.pdf](paper.pdf)
💻 **Code:** https://github.com/linqizhe07/zeroshotRevolve

## TL;DR

State-of-the-art LLM reward search trains and **discards** a policy for *every* reward candidate, ignoring policy initialization and reward ordering. FORGE restores that factorization: it pretrains a **task-agnostic skill prior once**, then lets an LLM evolve task rewards while each policy adapts through **closed-form skill projection** and inherits weights across generations. Fitness is measured over the *ordered reward–policy trajectory* rather than each reward in isolation.

## Highlights

- **10× less compute** per reward candidate than the prior automated state of the art, while exceeding it on Humanoid Locomotion, Humanoid Standup and Adroit Hand.
- **0.88 fitness on Adroit Hand door opening with zero demonstrations** and zero per-generation human feedback, above the published human-in-the-loop peak of 0.875, from an unsupervised exploration buffer that contains no success states at all.
- Performance is **threshold-like in precursor-state coverage** of the pretraining buffer, which motivates **coverage bootstrapping**: a rescue loop that writes the evolving policy's frontier back into the buffer and re-pretrains the prior.
- **No single best reward** matches the co-evolved peak, and replaying the discovered rewards out of order or skipping steps underperforms: the ordered trajectory is the load-bearing object.

## How it works

1. **Task-agnostic skill prior** — a feature map `φ`, prior policy `π₀`, and offline buffer are pretrained once per embodiment via temporal-distance successor features.
2. **Closed-form reward-to-skill projection** — each LLM-generated reward `R` is mapped to a skill vector `z* = (ΦᵀΦ)⁻¹Φᵀr`, giving the child policy a reward-directed initialization.
3. **Cross-generation inheritance** — each child fine-tunes from its parent checkpoint instead of restarting, so fitness reflects cumulative progress along the reward trajectory.
4. **Coverage bootstrapping** — when a generation fails, frontier transitions from accepted-lineage checkpoints are harvested back into the offline buffer and the prior is re-pretrained under an anchoring objective.

## Repository contents

```
.
├── index.html          # the project page
├── paper.pdf           # the paper (preprint)
└── assets/figures/     # figures: pipeline, fitness curves, buffer ablation, component ablation, reward replay
```

## Citation

```bibtex
@misc{zhe2026forge,
  title        = {FORGE: Fine-Tuning Over Reward Generations through Evolution},
  author       = {Zhe, Linqi},
  year         = {2026},
  howpublished = {\url{https://linqizhe07.github.io/forge/}},
  note         = {Preprint}
}
```
