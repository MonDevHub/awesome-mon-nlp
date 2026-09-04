# Awesome Mon NLP [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of NLP resources, tools, datasets, and models for the Mon language (ISO 639-3: `mnw`).

[Mon](https://en.wikipedia.org/wiki/Mon_language) is spoken by roughly one million people across Myanmar and Thailand, and [UNESCO classifies it as vulnerable](https://en.wikipedia.org/wiki/Atlas_of_the_World%27s_Languages_in_Danger). Open tooling for it has been scarce. This list collects the software, models, and data that exist for working with Mon (ISO 639-3: `mnw`) — starting with the open-source MonOCR ecosystem and growing to cover the wider field. Contributions are welcome.

## Contents

- [OCR & Text Recognition](#ocr--text-recognition)
  - [Applications](#applications)
  - [Models & Weights](#models--weights)
  - [SDKs & Libraries](#sdks--libraries)
- [Language Models & Tools](#language-models--tools)
- [Corpora & Datasets](#corpora--datasets)
- [Dictionaries & Lexical Resources](#dictionaries--lexical-resources)
- [Language Resources](#language-resources)
- [Research & Papers](#research--papers)
- [Related Projects & Community](#related-projects--community)

## OCR & Text Recognition

Tools for turning images of Mon script into text. The projects below form a single pipeline: the Hugging Face repository distributes the weights, monocr-onnx and monocr run inference, and the MonOCR apps ship it to end users.

### Applications

- [monocr-cli](https://crates.io/crates/monocr-cli) - Batch OCR over books, PDFs and images from the command line, on-device. `cargo install monocr-cli`.
- [MonOCR](https://github.com/MonDevHub/monocr) - Web, Android, and iOS apps that recognize Mon script fully on-device, with no data leaving the device. Try it at [ocr.mondevhub.com](https://ocr.mondevhub.com).

### Models & Weights

- [monocr (Hugging Face)](https://huggingface.co/janakhpon/monocr) - Pretrained MonOCR weights published in ONNX, Core ML, and PyTorch formats, trained on roughly 3M synthetic samples. The card's CER 0.025 and WER 0.211 are validation figures, measured on 30,000 lines rendered by the same generator as the training data — so they bound the renderer as much as the model. No evaluation on photographed pages has been published.

### SDKs & Libraries

- [monocr-onnx](https://github.com/MonDevHub/monocr-onnx) - On-device OCR engine powered by ONNX Runtime, with four bindings against one pinned model: Python ([`monocr-onnx`](https://pypi.org/project/monocr-onnx/)), Node.js ([`monocr`](https://www.npmjs.com/package/monocr)), [Go](https://pkg.go.dev/github.com/MonDevHub/monocr-onnx/go) and Rust ([`monocr`](https://crates.io/crates/monocr)). The bindings are checked against each other and do not fully agree; the repository publishes the measurement.
- [monocr](https://github.com/janakhpon/monocr) - Lightweight Python OCR package and `monocr` CLI for Mon text, with on-device inference and weights pulled from the Hugging Face Hub. Install with `pip install monocr`.

## Language Models & Tools

Generative models, language identification, and other NLP building blocks for Mon.

- [mon_tokenizer](https://github.com/Code-Yay-Mal/mon_tokenizer) - Unigram tokenizer for Mon, Burmese and English with full byte fallback, so unseen characters round-trip instead of being deleted. Vocabulary 64,256; the normalizer is serialized inside the artifact. Install with `pip install mon-tokenizer`; weights on the [Hugging Face Hub](https://huggingface.co/janakhpon/mon_tokenizer).
- [mon-language-detector](https://github.com/janakhpon/mon-language-detector) - Classifies text as Mon, Burmese or English with a fastText model, and answers `unknown` rather than guessing when a line is in another Myanmar-script language. The model ships inside the wheel. Install with `pip install mon-language-detector`.

## Corpora & Datasets

Text and image datasets for training and evaluating Mon models. Open Mon corpora are scarce; if you maintain or know of one, please see [Contributing](#contributing).

- [MonCorpusCollection](https://github.com/MonDevHub/MonCorpusCollection) - Mon-language text corpus of around one million lines gathered from Wikipedia, news agencies, and social media for NLP research and model training.
- [Mon Wikipedia](https://mnw.wikipedia.org/) - Mon-language edition of Wikipedia with several thousand articles, a widely used source of running Mon text for corpus building.
- [mon.monnews.org](https://mon.monnews.org/) - Mon-language news site that serves as a primary source of running Mon text.
- [Mon e-book library](https://fliphtml5.com/bookcase/yywzh) - Collection of a few hundred digitized Mon-language books, mostly Buddhist and Pali texts, readable online as flipbooks.

## Dictionaries & Lexical Resources

Dictionaries and structured lexical data for Mon.

- [MonMonDictOCR](https://github.com/MonDevHub/MonMonDictOCR) - Web app that pairs OCR with a Gemini LLM to build a Mon dictionary, extracting text from images and generating word etymology and meanings in Mon, built with React, TypeScript, and Vite.
- [MonDictDB](https://github.com/Barnista/MonDictDB) - Open-source SQL dictionary database for Mon with translations across Mon, Thai, Burmese, and English plus IPA notation, synonyms, and word relationships, backed by MySQL with Python services and a web interface.

## Language Resources

Scripts, fonts, encoding, and input tooling needed to handle Mon text correctly.

- [Unicode Myanmar block (U+1000–U+109F)](https://www.unicode.org/charts/PDF/U1000.pdf) - Unicode chart for the Myanmar script, which encodes Mon along with its language-specific characters at U+1028, U+1033–U+1034 and U+105A–U+1060.
- [Myanmar Unicode Fonts](https://github.com/AungMyoKyaw/Myanmar-Unicode-Fonts) - Collection of 82 Myanmar Unicode font files, including Padauk, Pyidaungsu, Noto Sans Myanmar, and MON3 Anonta; those four are the Mon-relevant ones and each declares SIL OFL or Apache 2.0 in its own embedded metadata. Coverage of the Mon-specific codepoints varies by family. Check the licence of any font you take from it before redistributing: the repository states none of its own, and the other files are mixed, including a vendor-EULA font and a paid-licence family.

## Research & Papers

Academic and technical work on Mon NLP.

- [Mon language (ISO 639-3: mnw)](https://iso639-3.sil.org/code/mnw) - ISO 639-3 reference entry for Mon, a useful starting point for language metadata.
- [Journal of the Siam Society open archive](https://thesiamsociety.org/journal-of-the-siam-society/) - Back issues are free to read and carry a long run of scholarship on the Mon. Five are directly on Mon language, history and community:
  - Halliday, *The Funeral Customs of the Mons* (vol. 16)
  - Gordon H. Luce, *Dvaravati and Old Burma* (vol. 53) - on the Mon polity that preceded and shaped early Burma
  - Michael Smithies, *Village Mons of Bangkok* (vol. 60)
  - Brian L. Foster, *Ethnic Identity of the Mons in Thailand* (vol. 61)
  - Nai Pan Hla, *The Major Role of the Mons in Southeast Asia* (vol. 79)

## Related Projects & Community

- [MonDevHub](https://github.com/MonDevHub) - Organization building open tools for the Mon language, including the MonOCR ecosystem.
- [Mon Buddhist Foundation](https://www.monbuddhistfoundation.co.uk/) - UK-based charity promoting Mon Buddhist culture and preserving the Mon language through educational programs, courses, and cultural events.

## Contributing

Contributions are welcome! Read the [contribution guidelines](CONTRIBUTING.md) first, and please follow the [Code of Conduct](CODE_OF_CONDUCT.md).
