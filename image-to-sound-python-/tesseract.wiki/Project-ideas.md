## Ideas for further development of Tesseract

### Conversion of neural networks for text recognition to and from Tesseract

As long as the networks are compatible with the features implemented in Tesseract, it should be possible to convert models made for Keras or Tensorflow to Tesseract and vice versa.

Maybe ONXX can be used as a common exchange format:

- https://github.com/onnx/onnx/blob/master/docs/ImplementingAnOnnxBackend.md

Related issues:

- [Use Tesseract models for Kraken](https://github.com/mittagessen/kraken/issues/152) (requires conversion from Tesseract to Keras)