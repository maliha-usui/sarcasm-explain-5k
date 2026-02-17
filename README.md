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
| Evaluation forms | 255 per type |
| Source | Reddit conversations |
| Generation model | OpenAI GPT-4 |

---

## 🔍 Explanation Types

Each sarcastic instance includes five complementary explanations:

| Type | Description | Human Evaluated |
|---|---|---|
| **Cognitive** | Why the mind recognises sarcasm — the belief or knowledge the speaker invokes | ✅ Yes |
| **Intent-Based** | Speaker's communicative goal — what they are trying to achieve socially or emotionally | ✅ Yes |
| **Contrastive** | Sarcastic vs. sincere comparison — what a genuine version would look like | ✅ (XAI research) |
| **Textual** | Linguistic features that signal sarcasm — word choice, tone, exaggeration | — |
| **Rule-Based** | Formal linguistic markers — punctuation, register shift, hyperbole | — |

---

## 📂 Dataset Structure

```
sarcasm-explain-5k/
├── README.md
├── LICENSE
├── index.html                        ← dataset landing page (GitHub Pages)
├── data/
│   └── sample_100.csv                ← 100-instance preview (50 sarcastic + 50 non-sarcastic)
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

## 📥 Download the Full Dataset

The full 5,000-instance dataset is hosted on HuggingFace with a contribute-to-access model.

👉 **[Get access at the dataset page](https://maliha-usui.github.io/sarcasm-explain-5k)**

To access the dataset, you complete **3 annotation forms** (≈10 minutes) from the Cognitive or Intent-Based evaluation pool. This enables ongoing crowd-sourced quality validation.

A **100-instance preview** is available directly in this repository: [`data/sample_100.csv`](data/sample_100.csv)

---

## 👥 Human Evaluation Framework

Each explanation type has **255 evaluation forms**, with each form covering 10 unique instances. Evaluators:

1. **Rate clarity** of each explanation (1–5 scale)
2. **Agree or disagree** with the generated explanation
3. **Write a correction** if they disagree

This *contribute-to-access* model ensures ongoing community-driven quality validation — a key methodological contribution of this work.

Human evaluation focuses on **Cognitive** and **Intent-Based** explanations, with **Contrastive** forms used for Cognitive XAI research directions.

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

## 🗺️ Future Work

- [ ] Complete human evaluation across all 255 forms per type
- [ ] Publish quality analysis and inter-annotator agreement
- [ ] Baseline experiments: does adding explanations improve sarcasm detection?
- [ ] Cross-lingual extension (Japanese, multilingual)
- [ ] Integration with Cognitive XAI frameworks
- [ ] Multi-agent reasoning for pragmatic understanding

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
- 💼 LinkedIn: [malihabintemamun](https://linkedin.com/in/malihabintemamun)
- 🤗 HuggingFace: [maliha](https://huggingface.co/maliha)

---

*This is an independent research project developed in 2025. The dataset builds on publicly available Reddit data.*
