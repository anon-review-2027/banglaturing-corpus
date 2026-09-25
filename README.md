# BanglaTuring Corpus

**Status:**  Anonymized supplementary material for a manuscript currently under double-blind peer review. This repository exists solely to allow reviewers to verify dataset-level claims made in the manuscript. It is not the final public release.

## Overview

BanglaTuring is a contamination-sensitive benchmark of AI-generated Bengali text detection. It consists of 20,000 documents, 10,000 written by humans and 10,000 AI generated, equally distributed across 5 generators and 45 academic and literary fields, the length and stylistic controls are outlined in the accompanying paper.


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
  
The documents we retrieved were human documents that appeared open on the Bengali web pages from the year 2010 to November 2022, before the ChatGPT was released openly. The continuously editable Bengali Wikipedia was not included.
- **Length matching:** 
The number of documents was set at 2000 per engine irrespective of survey share. The usage weighted metrics can be computed by reweighting the survey percentages reported in the paper.
Length matching: mean length of documents per class is very close (130.55 vs. 129.98) words; full length distributional and stylometric audit data are reported in the paper but not as separate columns in this file, any confounder controls used in length are reported as such (e.g., register, grammatical person, dash usage, digit ratio, etc.)

## Known Limitations

- `text` The human class values are obtained from freely available web sources and may be redistributed depending on the rights of the original source. This is a review copy for evaluation purposes only, does not form a final determination of licensure.
- A small number of human documents (embedded in otherwise topic-relevant content, such as institutional contact details mentioned within an article) have incidental contact details from the original source material. These are not related to the Data and Paper authors and will be reviewed for redaction prior to public release.
- Prompt templates and evaluation/audit code are not included in this repository, but are detailed in the manuscript and will be released with the full public version.
- The camera-ready release will include a datasheet of per-document provenance, generation parameters and licensing notes.

## License

Licensing (CC BY 4.0) will be completed and applied at paper acceptance. This is a review copy and it may not be used for anything other than peer review.
