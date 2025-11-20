# graphprompt-vkg-jailbreak
Code and resources for GraphPrompt, a Visual Knowledge Graph (VKG)–based jailbreak and safety evaluation framework for multimodal large language models (MLLMs).

# GraphPrompt: Jailbreaking Multimodal LLMs via Visual Knowledge Graphs

> 🚧 This repository is under active construction.  
> We are cleaning up the research code and will gradually release more components.

This repo hosts the implementation and resources for **GraphPrompt**, a VKG-based jailbreak framework for **Multimodal Large Language Models (MLLMs)**.

GraphPrompt systematically embeds obfuscated harmful intent into **Visual Knowledge Graphs (VKGs)** and leverages the **parse-then-execute** reasoning pathway of MLLMs to evaluate their safety alignment under structured visual inputs.  
The framework is designed **for red-teaming, safety evaluation, and defense research**, not for real-world misuse.

---

## Project Status

This repo is currently in a **pre-release** state:

- ✅ Paper draft and experimental protocol are stable.
- ✅ Directory skeleton and documentation are being prepared.
- 🧩 Core code (generation & evaluation pipelines) is being refactored and will be uploaded later.
- 🧪 A subset of prompts / configs / VKG examples will be released first, followed by full code and scripts.

If something is missing, it is likely still being cleaned up for release.

---

## Overview

GraphPrompt consists of two main components:

- **GraphPrompt-Synth**  
  A generation pipeline that:
  - rewrites harmful queries into benign-looking descriptions,
  - encodes them into visual knowledge graphs (VKGs),
  - renders VKG images via tools like Mermaid CLI under different visual configs.

- **GraphPrompt-Eval**  
  An evaluation pipeline that:
  - sends VKG images to target MLLMs (black-box setting),
  - collects model responses,
  - uses an automatic judge model to decide whether the attack succeeded,
  - supports standardized metrics (e.g., attack success rate, refusal rate).

We also include **defense experiments** (e.g., intent-first safety prompting) and analysis scripts for **layer-wise safety behavior** on selected models.

---

## Planned Repository Structure

The exact structure may change slightly as we release code, but the high-level layout will be:

```text
graphprompt-vkg-jailbreak/
├── src/
│   ├── graphprompt_synth/      # VKG generation pipeline (rewrite, graph build, rendering)
│   └── graphprompt_eval/       # Attack & evaluation scripts for target MLLMs
├── configs/                    # Model & experiment configuration files
├── data/
│   ├── base_prompts/           # Harmful base questions (red-teaming benchmark)
│   ├── rewrite_templates/      # Role-play / obfuscation templates
│   └── vkg_samples/            # Example VKG images & graph JSONs (subset)
├── scripts/                    # Helper scripts (rendering, log processing, plotting)
├── figures/                    # Diagrams used in the paper (optional)
├── README.md
└── LICENSE                     # To be added
