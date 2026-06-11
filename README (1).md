---
language:
  - en
  - kik
pretty_name: "High-Quality English–Gĩkũyũ Parallel Corpus"
tags:
  - translation
  - low-resource-languages
  - african-languages
  - kikuyu
  - gikuyu
  - machine-translation
  - nlp
  - parallel-corpus
  - human-translated
  - kenya
license: cc-by-4.0
task_categories:
  - translation
size_categories:
  - n<1K
annotations_creators:
  - expert-generated
language_creators:
  - expert-generated
multilinguality:
  - translation
source_datasets:
  - original
---

# English–Gĩkũyũ Parallel Corpus (Human-Curated)

## Dataset summary

This dataset addresses critical gaps in existing Gĩkũyũ (Kikuyu) NLP resources. Gĩkũyũ is the most widely spoken indigenous language in Kenya (approximately 8 million native speakers), yet it is absent from major African NLP benchmarks such as MasakhaNER and MasakhaPOS, and scores poorly in Meta's NLLB/FLORES-200 evaluation (3–9 BLEU).

The corpus was created by a native Gĩkũyũ speaker with clinical and NLP annotation expertise. Special attention was given to linguistic features that consistently cause errors in current models: diacritic accuracy (ĩ, ũ, â), the `Nĩ` vs `Ndĩ` copula distinction, affirmative and negative verb forms, tonal constructions, future and continuous tense prefixes, and natural modern register.

---

## Key features

- 100+ human-verified parallel sentences (English ↔ Gĩkũyũ)
- Expert-authored: no machine translation, no AI assistance
- Correct orthography with full diacritic coverage
- 10 thematic domains: greetings, agriculture, health, education, family, technology, government, environment, emotions, complex syntax
- Explicit notes on common model errors and culturally-bound expressions
- Contributed to improving Grok (xAI) Gĩkũyũ language capabilities

---

## Example data

| English | Gĩkũyũ | Notes |
|---------|--------|-------|
| I will listen attentively. | Nî nîngûgûthikîrîria wega. | Future prefix `nîngû-` |
| I will not listen. | Ndi gûthikîrîria. | Negative future; `Ndi` ≠ `Ndĩ` (copula) |
| You are a good student. | Wî mûrutwo mwega. | `Wî` = 2sg copula |
| I am here. | Niî ndî haha. | `Ndî` = 1sg copula; `Niî` = emphatic pronoun |
| Take this medicine twice a day. | Oya dawa ĩno hĩndĩ igĩrĩ kĩa mũthenya. | Medical domain |
| The rains came early this year. | Mũngu ũkĩũka nambere mwaka ũyũ. | Agricultural domain |

---

## Linguistic notes

### The `Nĩ` / `Ndĩ` distinction

This is one of the most common sources of model error in Gĩkũyũ:

| Form | Function | Example |
|------|----------|---------|
| `Nĩ` | Copula (3rd person / equative) | *Nĩ mwarimu* — He/she is a teacher |
| `Ndĩ` | Copula (1st person singular) | *Ndĩ mwarimu* — I am a teacher |
| `Wî` | Copula (2nd person singular) | *Wî mwarimu* — You are a teacher |

### Diacritics

Gĩkũyũ uses circumflex and tilde diacritics that encode phonemic distinctions. Omitting them changes meaning. This corpus uses the standard orthography endorsed by the Gĩkũyũ Literacy Committee:

- `ĩ` — nasalised /i/
- `ũ` — nasalised /u/
- `â`, `î`, `û` — long vowels in certain dialects

---

## Dataset structure

```
gikuyu-english-parallel/
├── README.md                  ← this file
├── data/
│   ├── train.jsonl            ← main parallel data (JSONL format)
│   ├── train.csv              ← same data in CSV format
│   └── test.csv               ← held-out evaluation split (if available)
└── configs/
    └── label_studio_ner.xml   ← Label Studio annotation config
```

### Column schema

| Column | Type | Description |
|--------|------|-------------|
| `id` | int | Unique sentence identifier |
| `english` | string | English source sentence |
| `gikuyu` | string | Gĩkũyũ target translation |
| `domain` | string | Thematic domain (health, greetings, etc.) |
| `notes` | string | Optional translator notes or correction flags |

### JSONL format (train.jsonl)

```json
{"id": 1, "english": "Good morning, how did you sleep?", "gikuyu": "...", "domain": "greetings", "notes": ""}
{"id": 21, "english": "Take this medicine twice a day after eating.", "gikuyu": "...", "domain": "health", "notes": ""}
```

---

## Domain coverage

| Domain | Sentence IDs | NLP gap addressed |
|--------|-------------|-------------------|
| Greetings & Social | 1–10 | Core pragmatic patterns |
| Agriculture & Food | 11–20 | Rural subsistence vocabulary |
| Health & Medicine | 21–32 | Clinical NLP; zero prior Gĩkũyũ medical corpora |
| Education | 33–42 | School-domain vocabulary |
| Family & Relationships | 43–52 | Kinship terminology |
| Technology & Digital | 53–62 | Entirely absent from all prior Gĩkũyũ NLP data |
| Government & Civic | 63–70 | Civic literacy language |
| Environment & Nature | 71–78 | Ecological and geographic vocabulary |
| Emotions & Mental States | 79–86 | Sentiment and affect data |
| Complex Syntax | 87–100 | Conditionals, interrogatives, subordinate clauses |

---

## Intended uses

**Recommended:**
- Machine translation training and evaluation (English ↔ Gĩkũyũ)
- Fine-tuning multilingual LLMs (mBART, NLLB, M2M-100) for Gĩkũyũ
- Spelling and diacritic correction tools
- Speech synthesis and ASR alignment for Gĩkũyũ
- Cultural preservation and language education

**Not recommended:**
- High-stakes automated decision-making without human review
- Standalone production MT without additional training data

---

## Languages

| Language | BCP-47 | ISO 639-3 | Notes |
|----------|--------|-----------|-------|
| English | en | eng | Standard written English |
| Gĩkũyũ | kik | kik | Central Kenya dialect; modern register |

---

## Comparison with existing resources

| Resource | Type | Gĩkũyũ quality | Domain coverage |
|----------|------|----------------|-----------------|
| Meta NLLB (FLORES-200) | Machine translation | BLEU 3–9 (poor) | General |
| MasakhaNER | NER benchmark | **Not included** | News |
| Khaya AI | MT model | BLEU ~16 | General |
| **This dataset** | Human parallel corpus | Native speaker | 10 domains |

---

## Creator

**Shadrack Mwangi**  
Pharmacist & NLP Data Specialist · KC Children's Hospital, Nairobi, Kenya  
Native Gĩkũyũ speaker · AI/NLP annotator (medical and African languages)

> Contributed to Grok (xAI) Gĩkũyũ language training data

- HuggingFace: Mwangi86
- GitHub:   
- LinkedIn / linkedin.com/shadrack-mwangi-243a66349

---

## License

This dataset is released under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to share and adapt the material for any purpose, including commercially, provided you give appropriate credit.

---

## Citation

```bibtex
@misc{mwangi2026_gikuyu_parallel,
  title     = {High-Quality {E}nglish--{G}{\~{i}}k{\~{u}}y{\~{u}} Parallel Corpus},
  author    = {Mwangi, Shadrack},
  year      = {2026},
  publisher = {HuggingFace},
  url       = {https://huggingface.co/datasets/mwangi86/gikuyu-english-parallel},
  note      = {Human-curated parallel corpus for low-resource Gĩkũyũ NLP.
               Native speaker translations covering 10 thematic domains.}
}
```

---

## Related datasets

- [SwahiliMed](https://huggingface.co/datasets/) — Swahili–English medical parallel corpus by the same author
- [FLORES-200](https://huggingface.co/datasets/facebook/flores) — Meta multilingual benchmark (includes kik, low quality)
- [CGIAR/KikuyuEnglish_translation](https://huggingface.co/datasets/CGIAR/KikuyuEnglish_translation) — Agriculture-domain Gĩkũyũ data

---

## Changelog

| Version | Date | Notes |
|---------|------|-------|
| v1.0 | June 2026 | Initial release — 100 sentences, 10 domains |
