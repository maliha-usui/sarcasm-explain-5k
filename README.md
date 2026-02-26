# SarcasmExplain-5K: Multi-Perspective Sarcasm Explanation Dataset

[![HuggingFace](https://img.shields.io/badge/🤗_Dataset-HuggingFace-yellow)](https://huggingface.co/datasets/maliha/sarcasm-explain-5k)
[![License: MIT](https://img.shields.io/badge/Code-MIT-blue)](LICENSE)
[![License: CC BY 4.0](https://img.shields.io/badge/Dataset-CC_BY_4.0-lightgrey)](https://creativecommons.org/licenses/by/4.0/)
[![Status](https://img.shields.io/badge/Status-Active-green)]()

> Created by **Maliha Binte Mamun** · Independent Research · 2025  
> 📄 Code: [MIT License](LICENSE) · Dataset: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

## 📌 Overview

**SarcasmExplain-5K** is a balanced dataset of **5,000 Reddit sarcasm instances** annotated with **five complementary natural language explanation types**, generated via a systematic GPT-4 pipeline and validated through crowd-sourced human evaluation.

Unlike existing sarcasm datasets that provide only binary labels, this dataset provides rich, multi-perspective explanations — enabling research in explainable AI, pragmatic language understanding, and human-AI communication.

| Statistic | Value |
|---|---|
| Total instances | 5,000 |
| Sarcastic | 2,500 |
| Non-sarcastic | 2,500 |
| Explanation types | 5 |
| Evaluation forms | 50 per type (COG + INT) |
| Source | Reddit conversations |
| Generation model | OpenAI GPT-4 |

---

## 📥 Accessing the Full Dataset

The full 5,000-instance dataset is hosted on **HuggingFace with gated access**.

Access is free — you contribute a small amount of annotation work in exchange.

### How to get access

| Step | Action |
|---|---|
| **1. Annotate** | Visit **[annotate.html](https://maliha-usui.github.io/sarcasm-explain-5k/annotate.html)** and choose any open Cognitive (COG) or Intent-based (INT) form |
| **2. Rate** | Rate 10 sarcasm explanations for clarity (1–5) and optionally suggest improvements (~8 min) |
| **3. Get your code** | After submitting, enter your Form ID (e.g. `COG014`) at the annotate page to receive your unique completion code (e.g. `SE5K-COG014-1EBAD543`) |
| **4. Request access** | Visit **[access.html](https://maliha-usui.github.io/sarcasm-explain-5k/access.html)**, verify your code, then paste it into the [HuggingFace access request form](https://huggingface.co/datasets/maliha/sarcasm-explain-5k) |

Access is approved within **24–48 hours** after submission.

> 💡 **Preview available:** A 100-instance sample is freely available without registration: [`data/sample_100.csv`](data/sample_100.csv)

### Why contribute-to-access?

This model supports ongoing, community-driven quality validation of the dataset at no cost to anyone — your annotations directly improve the evaluation study for our EMNLP 2026 submission.

---

## 🔍 Explanation Types

Each sarcastic instance includes five complementary explanations:

| Type | Description | Human Evaluated |
|---|---|---|
| **Cognitive** | Why the mind recognises sarcasm — the belief or knowledge the speaker invokes | ✅ Active (COG001–COG050) |
| **Intent-Based** | Speaker's communicative goal — what they are trying to achieve socially or emotionally | ✅ Active (INT001–INT050) |
| **Contrastive** | Sarcastic vs. sincere comparison — what a genuine version would look like | 🔜 Planned |
| **Textual** | Linguistic features that signal sarcasm — word choice, tone, exaggeration | — |
| **Rule-Based** | Formal linguistic markers — punctuation, register shift, hyperbole | — |

---

## 📂 Repository Structure

```
sarcasm-explain-5k/
├── README.md
├── LICENSE
├── index.html                        ← dataset landing page (GitHub Pages)
├── annotate.html                     ← annotation forms + completion code lookup
├── access.html                       ← code verification + HuggingFace access guide
├── data/
│   └── sample_100.csv                ← 100-instance preview (freely available)
└── code/
    └── ParaphraseSarcasm.ipynb       ← full data generation pipeline
```

### CSV Columns

| Column | Description |
|---|---|
| `label` | 0 = non-sarcastic, 1 = sarcastic |
| `label_name` | "sarcastic" or "non_sarcastic" |
| `comment` | The original Reddit comment |
| `parent_comment` | Conversational context |
| `rephrased_comment` | Non-sarcastic paraphrase of the comment |
| `cognitive_explanation` | Mental reasoning perspective |
| `intent_based_explanation` | Speaker's communicative goal |
| `contrastive_explanation` | Sarcastic vs. sincere comparison |
| `textual_explanation` | Linguistic analysis perspective |
| `rule_based_explanation` | Linguistic markers identified |

---

## 💡 Sample Entry

**Comment:** *"Yeah, like the president is a big deal!"*  
**Parent Comment:** *And even a prominent democrat defended him.*  
**Label:** Sarcastic

| Explanation Type | Content |
|---|---|
| **Cognitive** | The speaker invokes the common knowledge that the presidency is a position of immense power — using that as a foil to mock someone who downplays the president's importance. |
| **Intent-Based** | The speaker is mocking whoever minimizes the president's significance. Social goal: highlight the absurdity of the counterpart's position. |
| **Contrastive** | A sincere version: *"The president is indeed a significant figure."* The sarcastic comment inverts this through dismissive phrasing. |
| **Textual** | The word *"like"* and the exclamation mark signal insincerity. Downplaying an obviously powerful position creates the ironic gap. |
| **Rule-Based** | Linguistic markers: informal minimiser ("like"), exclamatory punctuation, contradiction with common knowledge. |

---

## 👥 Human Evaluation Framework

Human evaluation focuses on **Cognitive** and **Intent-Based** explanation types, with **50 evaluation forms per type** (10 instances per form).

### Evaluation task per form

1. **Rate clarity** of each explanation (1–5 Likert scale)
2. **Agree or disagree** with the generated explanation  
3. **Write a correction** if the explanation is unclear or inaccurate (optional)

### Evaluation form pools

| Pool | Form IDs | Forms | Instances |
|---|---|---|---|
| Cognitive | COG001 – COG050 | 50 | 500 |
| Intent-Based | INT001 – INT050 | 50 | 500 |

Forms are available at [annotate.html](https://maliha-usui.github.io/sarcasm-explain-5k/annotate.html). Each completed form earns one completion code for dataset access.

### Completion code format

Codes follow the format `SE5K-[FORMID]-[HASH]`, for example:

```
SE5K-COG014-1EBAD543
SE5K-INT031-3200CCCB
```

Enter your Form ID at the [annotate page](https://maliha-usui.github.io/sarcasm-explain-5k/annotate.html) to retrieve your code at any time.

---

## 🔬 Dataset Creation Pipeline

Explanations were generated using OpenAI GPT-4 with carefully engineered prompts for each explanation type. The pipeline:

1. Source sarcastic comments from Reddit (r/sarcasm corpus)
2. Balance dataset: 2,500 sarcastic + 2,500 non-sarcastic
3. For each sarcastic instance, generate 5 explanation types via GPT-4
4. Post-process for consistency and quality
5. Create human evaluation forms for validation

See [`code/ParaphraseSarcasm.ipynb`](code/ParaphraseSarcasm.ipynb) for the full pipeline.

> **Note:** To run the notebook, set your OpenAI API key as an environment variable:
> ```bash
> export OPENAI_API_KEY="your-key-here"
> ```

---

## 🎯 Applications

This dataset supports research in:

- **Explainable AI (XAI):** Multi-perspective explanation generation for NLP models
- **Sarcasm Detection:** Training models with richer contextual understanding
- **Pragmatic NLP:** Computational approaches to non-literal language
- **Cognitive Modelling:** Understanding how humans recognise irony and sarcasm
- **Human-AI Interaction:** Improving model awareness of speaker intent

---

## 🗺️ Roadmap

- [x] Generate 5,000-instance dataset with 5 explanation types
- [x] Publish sample (100 instances) to GitHub
- [x] Host full dataset on HuggingFace (gated)
- [x] Create contribute-to-access annotation system (COG + INT forms)
- [x] Launch annotate.html + access.html on GitHub Pages
- [ ] Collect 100–200 human evaluations per type
- [ ] Publish inter-annotator agreement analysis
- [ ] Baseline experiments: do explanations improve sarcasm detection?
- [ ] Submit to EMNLP 2026
- [ ] Cross-lingual extension (Japanese, multilingual)

---

## 📖 Citation

If you use this dataset or pipeline in your research, please cite:

```bibtex
@misc{mamun2025sarcasmexplain,
  author    = {Mamun, Maliha Binte},
  title     = {SarcasmExplain-5K: A Multi-Perspective Sarcasm Explanation Dataset},
  year      = {2025},
  publisher = {GitHub / HuggingFace},
  url       = {https://huggingface.co/datasets/maliha/sarcasm-explain-5k},
  note      = {Independent research. Contact: bintemaliha19@gmail.com}
}
```

---

## 📧 Contact

**Maliha Binte Mamun**  
PhD, Computer and Information Science — Shizuoka University (2024)  
Product Development Engineer — Pi Photonics, Hamamatsu, Japan

- 📮 Email: [bintemaliha19@gmail.com](mailto:bintemaliha19@gmail.com)
- 🐙 GitHub: [@maliha-usui](https://github.com/maliha-usui)
- 💼 LinkedIn: [Maliha Binte Mamun](https://www.linkedin.com/in/maliha-binte-mamun-8a5708161)
- 🤗 HuggingFace: [maliha](https://huggingface.co/maliha)

---

*Independent research project, 2025. Builds on publicly available Reddit data.*
