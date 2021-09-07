# Frequently asked questions

## Which models can be used for historic European texts?

Old European texts often use [Fraktur](https://en.wikipedia.org/wiki/Fraktur) or historic [Antiqua](https://en.wikipedia.org/wiki/Antiqua_(typeface_class)) fonts with [long s](https://en.wikipedia.org/wiki/Long_s) and [ligatures](https://en.wikipedia.org/wiki/Orthographic_ligature). Those texts require special Tesseract models as the standard models like `eng`, `deu` or `script/Latin` don't recognize them good.

Several models are available for such old texts. `deu_frak` is a model which was trained for Tesseract 3. The current standard models are `frk` and `script/Fraktur`. In addition, there exist models trained by UB Mannheim which often give better results.

### deu_frak

This user contributed model only supports the legacy (pattern based) OCR engine, so does not work with a LSTM neural network which typically can achieve better OCR results. The legacy engine has one advantage: it can detect character attributes like cursive or fat.

### frk

This is the standard model for German Fraktur texts. It includes a German dictionary. The model has some restrictions regarding the character set which it can recognize. It also has problems especially with `ch` and `ck` ligatures.

### script/Fraktur

This is the standard model for European Fraktur and historic Antiqua texts. It supports a wider character set than `frk`, but has similar problems with `ch` and `ck`.

### Fraktur models from UB Mannheim

Those models typically give the best results. They eliminate the problems of `frk` and `script/Fraktur` and know different variants of the German umlauts. These variants are available:

- [models](https://ub-backup.bib.uni-mannheim.de/~stweil/ocrd-train/data/Fraktur_5000000/tessdata_fast/) based on `script/Fraktur`
- [models](https://ub-backup.bib.uni-mannheim.de/~stweil/ocrd-train/data/GT4HistOCR_5000000/tessdata_fast/) trained from scratch
- [models](https://ub-backup.bib.uni-mannheim.de/~stweil/ocrd-train/data/ONB/tessdata_fast/) trained from Austrian newspapers with Fraktur

All those models work without any dictionary. The current Tesseract versions therefore show a warning which can simply be ignored.
