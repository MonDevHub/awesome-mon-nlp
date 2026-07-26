# Awesome Mon NLP [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of NLP resources, tools, datasets, and models for the Mon language (ISO 639-3: `mnw`).

[Mon](https://en.wikipedia.org/wiki/Mon_language) is spoken by roughly one million people across Myanmar and Thailand, and [UNESCO classifies it as vulnerable](https://en.wikipedia.org/wiki/Atlas_of_the_World%27s_Languages_in_Danger). Open tooling for it has been scarce. This list collects the software, models, and data that exist for working with Mon (ISO 639-3: `mnw`) — starting with the open-source MonOCR ecosystem and growing to cover the wider field. Contributions are welcome.

## Contents

- [OCR & Text Recognition](#ocr--text-recognition)
  - [Applications](#applications)
  - [Models & Weights](#models--weights)
  - [SDKs & Libraries](#sdks--libraries)
  - [Training & Research](#training--research)
- [Language Models & Tools](#language-models--tools)
- [Corpora & Datasets](#corpora--datasets)
- [Dictionaries & Lexical Resources](#dictionaries--lexical-resources)
- [Data Collection Tools](#data-collection-tools)
- [Language Resources](#language-resources)
- [Research & Papers](#research--papers)
- [Related Projects & Community](#related-projects--community)

## OCR & Text Recognition

Tools for turning images of Mon script into text. The projects below form a single open pipeline: mon_OCR trains the model, monocrhf distributes the weights, monocr-onnx and monocr run inference, and the MonOCR apps ship it to end users.

### Applications

- [MonOCR](https://github.com/MonDevHub/monocr) - Web, Android, and iOS apps that recognize Mon script fully on-device, with no data leaving the device. Try it at [ocr.mondevhub.com](https://ocr.mondevhub.com) or on [Google Play](https://play.google.com/store/apps/details?id=dev.janakhpon.monocr); an iOS build is in App Store review.

### Models & Weights

- [monocr (Hugging Face)](https://huggingface.co/janakhpon/monocr) - Pretrained MonOCR weights published in ONNX, Core ML, and PyTorch formats, trained on roughly 3M samples (CER 0.025, WER 0.211).

### SDKs & Libraries

- [monocr-onnx](https://github.com/MonDevHub/monocr-onnx) - Privacy-first, on-device OCR engine powered by ONNX Runtime, with unified cross-platform SDKs for Python (`monocr-onnx`), JavaScript/Node.js (`monocr`), Go, and Rust.
- [monocr](https://github.com/janakhpon/monocr) - Lightweight Python OCR package and `monocr` CLI for Mon text, with on-device inference and weights pulled from the Hugging Face Hub. Install with `pip install monocr`.

### Training & Research

- [mon_OCR](https://github.com/janakhpon/mon_OCR) - Production training pipeline for Mon OCR using a MobileNetV3-Large backbone, 2-layer BiLSTM, and CTC head over a 315-character charset, with ONNX and TFLite export.

## Language Models & Tools

Generative models, language identification, and other NLP building blocks for Mon.

- [mon-language-detector](https://github.com/janakhpon/mon-language-detector) - Python library that classifies text as Mon, Burmese, or English using a fastText model, for server-side filtering or on-device use.
- [mon-gpt-playground](https://github.com/janakhpon/mon-gpt-playground) - Streamlit app for testing and comparing the Mon-LM language models (0.5B, 1.5B, and 3B) fine-tuned for Mon.

## Corpora & Datasets

Text and image datasets for training and evaluating Mon models. Open Mon corpora are scarce; if you maintain or know of one, please see [Contributing](#contributing).

- [MonCorpusCollection](https://github.com/MonDevHub/MonCorpusCollection) - Mon-language text corpus of around one million lines gathered from Wikipedia, news agencies, and social media for NLP research and model training.
- [Mon Wikipedia](https://mnw.wikipedia.org/) - Mon-language edition of Wikipedia with several thousand articles, a widely used source of running Mon text for corpus building.
- [mon.monnews.org](https://mon.monnews.org/) - Mon-language news site that serves as a primary source of running Mon text; harvestable with the tools in [Data Collection Tools](#data-collection-tools).
- [Mon e-book library](https://fliphtml5.com/bookcase/yywzh) - Collection of a few hundred digitized Mon-language books, mostly Buddhist and Pali texts, readable online as flipbooks.

## Dictionaries & Lexical Resources

Dictionaries and structured lexical data for Mon.

- [MonMonDictOCR](https://github.com/MonDevHub/MonMonDictOCR) - Web app that pairs OCR with a Gemini LLM to build a Mon dictionary, extracting text from images and generating word etymology and meanings in Mon, built with React, TypeScript, and Vite.
- [MonDictDB](https://github.com/Barnista/MonDictDB) - Open-source SQL dictionary database for Mon with translations across Mon, Thai, Burmese, and English plus IPA notation, synonyms, and word relationships, backed by MySQL with Python services and a web interface.

## Data Collection Tools

- [mon-corpus-scraper](https://github.com/janakhpon/mon-corpus-scraper) - Web scraping toolkit that collects Mon-language text from [mon.monnews.org](https://mon.monnews.org/) and other sources for corpus and NLP work, built on Playwright, BeautifulSoup, and Polars.

## Language Resources

Scripts, fonts, encoding, and input tooling needed to handle Mon text correctly.

- [Unicode Myanmar block (U+1000–U+109F)](https://www.unicode.org/charts/PDF/U1000.pdf) - Unicode chart for the Myanmar script, which encodes Mon along with its language-specific characters.

## Research & Papers

Academic and technical work on Mon NLP.

- [Mon language (ISO 639-3: mnw)](https://iso639-3.sil.org/code/mnw) - ISO 639-3 reference entry for Mon, a useful starting point for language metadata.

## Related Projects & Community

- [MonDevHub](https://github.com/MonDevHub) - Organization building open tools for the Mon language, including the MonOCR ecosystem.
- [Mon Buddhist Foundation](https://www.monbuddhistfoundation.co.uk/) - UK-based charity promoting Mon Buddhist culture and preserving the Mon language through educational programs, courses, and cultural events.

## Contributing

Contributions are welcome! Read the [contribution guidelines](CONTRIBUTING.md) first, and please follow the [Code of Conduct](CODE_OF_CONDUCT.md).
