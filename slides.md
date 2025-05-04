---
# theme: seriph
background: https://cover.sli.dev
title: Exam \#2 Review
info: |
  ## CST 205
class: text-center
drawings:
  persist: false
mdc: true
---

# Exam \#2 Review

CST 205

---

## Overview

* **Exam on Canvas** (closed-note)
* **Allowed:** 4 sheets (8 sides) of handwritten/typewritten notes
* **Not allowed:** running Python code, internet/course material search, ChatGPT

---

# General Python (Part 1)

* **Immutable vs. mutable** (lists, dicts, tuples)

  * `lst = [3,1,2]; lst.sort()` → `[1,2,3]`
  * `tpl = (3,1,2);` no `tpl.sort()` (tuples immutable)
* **Running Python**

  * Interactive REPL vs. `.py` files
  * Virtual environments (`python -m venv venv`)


---

# General Python (Part 2)

* **Modules & imports**

  ```python
  import math
  from math import sqrt, pi
  ```
* **f‑strings**

  ```python
  name = "Yoshi"
  print(f"Hello, {name}! \u2606")
  ```


---

# General Python (Part 3)

* **Built‑ins**: `len()`, `range()`, `split()`, `sort()`

  * Example: split RGB list by 'X'

    ```python
    s = "(24,78,99)X(207,99,230)X(100,230,200)X(123,99,78)"
    parts = s.split('X')
    ```
* **Serialization & pickle**

  ```python
  import pickle
  with open('data.pkl','wb') as f:
      pickle.dump(obj, f)
  # 'wb' = write in binary mode
  ```

---


# Python OOP

* **Define classes & objects**

  ```python
  class Point:
      def __init__(self, x, y):
          self.x = x
          self.y = y
      def __str__(self):
          return f"Point({self.x},{self.y})"
      def __eq__(self, other):
          return isinstance(other, Point) and self.x==other.x and self.y==other.y
  ```
* Special methods: `__init__`, `__str__`, `__eq__`, use of `self`


---

# Digital Images

* **Temporal median filter**: median per-pixel across frames → remove moving objects
* **Color transforms**

  ```python
  from PIL import Image, ImageOps
  gray = img.convert('L')   # grayscale
  neg  = ImageOps.invert(img) # negative
  ```
* **Chroma key / blending** (mask regions)
* **Pillow APIs**: `getpixel()`, `putpixel()`, `getdata()`, `putdata()`
* **Image modes**: 1-bit (B/W), 8-bit (palette), RGB


---

# Desktop GUI (Qt / PySide6)

* **QApplication**: initialize GUI
* **Main event loop**: `app.exec_()`
* **Signal–slot**

  ```python
  button.clicked.connect(on_click)
  ```
* **Layouts**: `QVBoxLayout`, `QHBoxLayout`

  * Adding widget after setLayout still appears


---

# Digital Audio

* **Sine wave**: time vs amplitude

  ```python
  import numpy as np
  t = np.linspace(0,1,44100)
  y = np.sin(2*np.pi*440*t)
  ```
* **Pitch**: freq (Hz)
* **Sampling rate**: e.g., 44100 Hz (samples/sec)
* **Quantization**: bit depth (e.g., 16‑bit)
* **Human hearing**: up to \~20 kHz → CD uses 44.1 kHz


---

# Web Programming (Flask)

* **Route decorator**

  ```python
  @app.route('/')
  def home():
      return render_template('index.html')
  ```
* **render\_template()**: pass variables
* **url\_for()**: `url_for('home', page=2)`
* **Bootstrap**: CSS framework for layout/styles
* **Flask-WTF**: form classes subclass `FlaskForm`

  ```python
  class MyForm(FlaskForm):
      name = StringField('Name')
  ```



---

# APIs & Web Scraping

* **Requests**: HTTP client

  ```python
  import requests
  resp = requests.get(url)
  ```
* **JSON**: `resp.json()` returns dict
* **Parse HTML**: Beautiful Soup

  ```python
  from bs4 import BeautifulSoup
  soup = BeautifulSoup(resp.text, 'html.parser')
  ```




---

# NumPy

* **ndarray** creation: `np.array([1,2,3])`
* **Vectorized ops**: `arr*2`, `arr+arr2`
* **np.arange()**: ranges of values

  ```python
  np.arange(0,10,2)  # [0,2,4,6,8]
  ```


---

# Computer Vision (OpenCV)

* **imread() / imshow()** ↔ NumPy arrays

  ```python
  img = cv2.imread('img.jpg')
  cv2.imshow('win', img)
  ```
* **highgui**: window display, key events
* **Classifier** (Viola–Jones face detector)
* **Preprocessing**: convert to grayscale, equalize histogram, resize



---

# Version Control & CLI

* **Shell**: `mkdir`, `cd`, `ls`, `mv`
* **Git vs. GitHub**: local vs remote
* **Basic Git**: `git init`, `git add .`, `git commit -m` , `git push`
* **Staging**: files in index before commit
* **Branching**: `git checkout -b feature`
* **Pull request**: propose changes for review



