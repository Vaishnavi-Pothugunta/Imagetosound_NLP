When you want to install additional language and script models there are two options.

A) Either you can start the installation again and choose the additional language and script models to install.

B) Or, you can install them manually:
1. Choose the additional language and script models from e.g. one of the places linked from https://github.com/tesseract-ocr/tesseract/wiki/Data-Files .
2. Download the `traineddata` file to the `tessdata` folder of tesseract on your PC, e.g. `C:\Program Files\Tesseract-OCR\tessdata`. It is also possible to create new subfolders within that folder to distinguish for example the best and fast models.
3. Check that the new languages are recognized by
```
tesseract --list-langs
```
