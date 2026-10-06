# Sámi NLP Data Audit

A reproducible audit of open Sámi-language NLP resources, conducted as groundwork for a proposed PhD direction on evaluation and data governance for Sámi language AI (connected to the [Sámi AI Lab](https://uit.no), UiT / Sámi allaskuvla).

## Findings (full writeup in `paper/`)

1. **Resource imbalance.** Across the six Sámi languages represented in [`tartuNLP/smugri4-data`](https://huggingface.co/datasets/tartuNLP/smugri4-data) — the most comprehensive open multi-Sámi text collection identified — Northern Sámi has **15,623×** more tokens than Kildin Sámi. Skolt Sámi and Pite Sámi are entirely absent.
2. **Label reliability.** Running language identification ([GlotLID](https://github.com/cisnlp/GlotLID)) over a corpus explicitly titled the "Northern Sami Subtitle Corpus" ([Zenodo record 14176353](https://zenodo.org/records/14176353)) shows only **88.0%** of its 913 sentences are confirmed North Sámi; 8.3% are Inari Sámi and 1.5% are Finnish, undisclosed in the corpus metadata.
3. **Pilot evaluation.** A small balanced experiment (n=42) testing whether a general-purpose LLM can distinguish North Sámi, Inari Sámi, and Finnish sentences from one another, using the verified labels above as gold truth. *(Results pending — see `notebook/`, Section 4e.)*

## Repository structure

```
notebook/   Full, reproducible Jupyter notebook (run on Kaggle with internet enabled)
results/    sami_nlp_audit_results.json — every verified number in the paper, machine-readable
figures/    Figure-generation code (make_figures.py) + all 4 rendered PNGs
paper/      Full paper draft, PDF and DOCX
```

## Reproducing this work

1. Upload `notebook/sami_nlp_research_starter.ipynb` to a new Kaggle notebook.
2. Enable internet access (Settings → Internet → On).
3. To run the pilot evaluation (Section 4e), add your `ANTHROPIC_API_KEY` under Add-ons → Secrets.
4. Run all cells top to bottom. This regenerates `sami_nlp_audit_results.json` and all four figures from source.

## Data sources audited

- [`tartuNLP/smugri4-data`](https://huggingface.co/datasets/tartuNLP/smugri4-data) (Hugging Face)
- [`ltg/saami-web`](https://huggingface.co/datasets/ltg/saami-web) (Hugging Face, University of Oslo Language Technology Group)
- [Zenodo record 14176353](https://zenodo.org/records/14176353) — Northern Sami Subtitle Corpus

## Status

Working draft. Not yet peer-reviewed. Intended next steps: complete the pilot evaluation, verify all bibliographic references, submit to arXiv (cs.CL), and pursue ComputEL-11 / NoDaLiDa 2027 as peer-reviewed venues.

## Ethical note

This audit uses only openly licensed, previously published datasets; no new data was collected from Sámi speakers or communities. The authors are not Sámi, and this work is presented as a technical data statement meant to inform — not substitute for — community-led decisions about Sámi language data governance, following the [CARE Principles for Indigenous Data Governance](https://www.gida-global.org/care) and the work of the GIDA-Sápmi network. See the paper's Limitations and Ethical Considerations sections for full discussion.

## License

Code: MIT (see `LICENSE`). Paper text and figures: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) unless noted otherwise. Audited third-party datasets retain their own original licenses — see each source above.
