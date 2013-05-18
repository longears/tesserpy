tesserpy
========

A Python API for Tesseract

Building
--------
It's the usual distutils dance -- run `python setup.py` for more details.

If your Tesseract installation's files are not in the standard system paths, you may need to create a `setup.cfg` with the following contents:

```ini
[build_ext]
include-dirs=/path/to/tesseract/include
library-dirs=/path/to/tesseract/lib
```

Example
-------
Here's a simple example that requires OpenCV:

```python
import cv2
import tesserpy

tess = tesserpy.Tesseract("/path/to/tessdata/prefix", language="eng")
tess.tessedit_char_whitelist = """'"!@#$%^&*()_+-=[]{};,.<>/?`~abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"""
image = cv2.imread('/path/to/image.png')
tess.set_image(image)
print(tess.get_utf8_text())
```
