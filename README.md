# BanglaTuring Corpus

**Status:** Anonymized supplementary material for a paper currently under double-blind review at ICEEICT 2027. This repository exists solely to allow reviewers to verify dataset-level claims made in the manuscript. It is not the final public release.

## Overview

BanglaTuring is a contamination-aware benchmark for Bengali AI-generated text detection. It contains 20,000 documents — 10,000 human-written and 10,000 AI-generated — balanced across five generators and 45 academic and literary disciplines, with length and stylistic controls documented in the accompanying paper.

| Property | Value |
|---|---|
| Total documents | 20,000 |
| Human documents | 10,000 (web text, 2010–Nov 2022, pre-ChatGPT) |
| AI documents | 10,000 (2,000 per generator) |
| Generators | ChatGPT (GPT-5.6 Luna), Claude (Sonnet 5), DeepSeek (DeepSeek-V4), Google (Gemini 3.1 Pro), Grok (Grok 4.5) |
| Disciplines | 45 |
| Total words | ~2,605,322 (whitespace-delimited) |
| Mean document length | Human 130.55 words · AI 129.98 words |
| Language | Bengali (Bangla) |

## File

- `BanglaTuring Human vs AI Dataset.xlsx` — the full corpus, one row per document.

## Column Schema

| Column | Type | Description |
|---|---|---|
| `id` | integer | Row index (0–19999) |
| `text` | string | Document content (Bengali) |
| `label` | integer | `0` = human, `1` = AI |
| `source_type` | string | `Human` or `AI` |
| `generator_model` | string | `Human` for human documents; otherwise the generating model label (`ChatGPT`, `Gemini`, `Claude`, `Deepseek`, `Grok`) corresponding to the five evaluated LLM engines |
| `topic` | string | Discipline label (one of 45; see below) |
| `original_id` | string | Zero-padded source identifier from the original construction pipeline |

## Class / Generator Distribution

| `generator_model` | Generator Model & Version | Count |
|---|---|---|
| Human | Human-authored web texts (2010–2022) | 10,000 |
| ChatGPT | ChatGPT (GPT-5.6 Luna) | 2,000 |
| Claude | Claude (Sonnet 5) | 2,000 |
| Deepseek | DeepSeek (DeepSeek-V4) | 2,000 |
| Gemini | Google (Gemini 3.1 Pro) | 2,000 |
| Grok | Grok (Grok 4.5) | 2,000 |

## Disciplines (45)

Agriculture, Archaeology, Architecture, Artificial Intelligence, Astronomy, Biography, Biology, Chemistry, Climate, Communication, Computer Science, Culture, Cybersecurity, E-governance, Economics, Education, Energy, Environment, Ethics, Fiction, Freelancing, Geography, Health, History, Journalism, Language, Literature, Mathematics, Media, Philosophy, Physics, Psychology, Public health, Robotics, Science, Sociology, Space exploration, Technology, Textile industry, Transportation, Travel, Urban farming, Urbanization, Water resources, Wildlife

Every discipline appears in both the human and AI classes (no topic is exclusive to either label).

## Construction Notes

- **Temporal boundary:** Human documents were retrieved from openly accessible Bengali web sources dated between 2010 and November 2022, preceding the public release of ChatGPT. Bengali Wikipedia was excluded due to its continuously editable nature.
- **Generator selection:** AI documents were generated using five frontier engines selected via a usage survey (N = 1,466 respondents):
  - **ChatGPT (GPT-5.6 Luna)**
  - **Claude (Sonnet 5)**
  - **DeepSeek (DeepSeek-V4)**
  - **Google (Gemini 3.1 Pro)**
  - **Grok (Grok 4.5)**
  
  Document counts were fixed at 2,000 per engine regardless of survey share. Usage-weighted metrics can be recovered by reweighting with the survey percentages reported in the paper.
- **Length matching:** Mean document length is closely matched between classes (130.55 vs. 129.98 words); full distributional and stylometric audit details, including confounder controls (register, grammatical person, dash usage, digit ratio, etc.), are reported in the paper rather than as separate columns in this file.

## Known Limitations

- `text` values are drawn from openly accessible web sources for the human class; redistribution rights vary by original source. This review copy is provided strictly for evaluation purposes and is not a final licensing determination.
- A small number of human documents (embedded within otherwise topic-relevant content, e.g. institutional contact information cited within an article) retain incidental contact details from the original source material. These are unrelated to the authorship of this dataset or paper and will be reviewed for redaction before public release.
- This repository does not include prompt templates or evaluation/audit code; those are described in the manuscript and will accompany the full public release.
- A datasheet documenting per-document provenance, generation parameters, and licensing notes will be included with the camera-ready release.

## License

Licensing (CC BY 4.0) will be finalized and applied upon paper acceptance. No license is granted for reuse of this review copy beyond the purposes of peer review.
