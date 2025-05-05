---
# theme: seriph
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

## Administrivia

<br>

<v-clicks>

- **Exam on Canvas** (closed-note)
- **Allowed:** 4 sheets (8 sides) of handwritten and/or typed notes
- **Not allowed:** running Python code, internet/course material search, ChatGPT

</v-clicks>


---

## Overview

This review will be organized into the following sections:

<v-clicks>

- General Python
- Version Control / Command Line
- Digital Images
- Desktop GUI Programming (PySide/Qt)
- Web Programming (Flask)
- Digital Audio
- APIs / Web Scraping
- Computer Vision

</v-clicks>


---



## General Python


**Running Python**

  * Interactive REPL vs. `.py` files
  * Virtual environments (`python -m venv venv`)

<br>

**Immutable vs. mutable** (lists, dicts, tuples)

```python
my_list = [3,1,2]
my_list.sort()
print(my_list)
```


<v-click>

```python
my_tuple = (3,1,2)
my_tuple.sort()
````
</v-click>


---

## General Python (cont.)

<br>

- **Modules & imports**

  ```python
  from image_info import image_info
  from random import choice
  
  my_item = choice(image_info)
  ```
  
  <br>

<v-click>
  
- **f‑strings**

  ```python
  name1 = "polar"
  name2 = "cartesian"
  name3 = "coordinates"
  print(f'Hello, I love {name1} {name3}!')
  ```
  
</v-click>

---

## General Python (cont.)

<br>

- **Built‑ins**: `len()`, `range()`, `split()`, `sort()`

  * Example: split RGB list by 'X'

    ```python
    s = "(24,78,99)X(207,99,230)X(100,230,200)X(123,99,78)"
    parts = s.split('X')
    ```

<v-click>

    
- **Serialization & pickle**

  ```python
  import pickle
  with open('data.pkl','wb') as f: # 'wb' = write in binary mode
      pickle.dump(obj, f)
  ```

</v-click>


---


## Python OOP

```python
class MediaLibrary:
    def __init__(self, name):
        self.name = name  # Name of the library
        self.library = []  # An attribute to store all media files

    def add_media(self, title, file_format):
        media = {
            "title": title, "file_format": file_format,
        }
        self.library.append(media)

    def filter_by_format(self, file_format):
        filtered_files = []  # Initialize an empty list to store the results
        for media in self.library:
            if media["file_format"] == file_format:
                filtered_files.append(media)  # Add matching media to the list
        return filtered_files

    def __str__(self):
        result = f"Media Library: {self.name}\n"
        for media in self.library:
            result += f"{media['title']} ({media['file_format']})\n"
        return result
```


---

## Python OOP (cont.)

<br>

<v-clicks depth=2>

- Special methods: `__init__`, `__str__`, `__eq__`, use of `self`

- Object creation

- Important classes we've used:
    - Pillow's `Image`
    - `Flask`
    - `QApplication`, `QWidget` (w/ inheritance)
    - etc.
    
</v-clicks>

---

## Digital Images

<br>

<v-clicks>

- **Temporal median filter**: median per-pixel across frames → remove moving objects
- Know how various image manipulations work (grayscale, chroma key, blending, negative)
- **Chroma key / blending** (mask regions)
- Pillow’s `getpixel()`, `putpixel()`, `getdata()`, `putdata()`
- **Image modes**: 1-bit, 8-bit, RGB

</v-clicks>

---

## Desktop GUI (Qt / PySide6)

<v-clicks>


- **QApplication**: initialize GUI
- **Main event loop**: `app.exec()`
- **Signal–slot**

  ```python
  button.clicked.connect(on_click)
  ```
- **Layouts**: `QVBoxLayout`, `QHBoxLayout`

</v-clicks>


---

## Digital Audio

<v-clicks depth="2">


- **Sine wave**: 
    - simplest waveform
    - x-axis represents time
    - y-axis represents amplitude

- **Pitch**: freq (Hz)
    - High pitch waveforms go through more cycles per second.

- **Sampling rate**: e.g., 44100 Hz (samples/sec)

- **Quantization**: bit depth (e.g., 16‑bit)

- **Human hearing**: up to \~20 kHz → CD uses 44.1 kHz

</v-clicks>



---

## Web Programming (Flask)


<v-clicks depth="2">

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

</v-clicks>


---

## APIs & Web Scraping


<v-clicks>


- **Requests**: preferred HTTP client (not part of standard library)

  ```python
  import requests
  resp = requests.get(url)
  ```
- **JSON**: `resp.json()` returns dictionary
- **Parse HTML**: Beautiful Soup

  ```python
  from bs4 import BeautifulSoup
  soup = BeautifulSoup(resp.text, 'lxml')
  ```

</v-clicks>



---

## NumPy

<v-clicks>


* **ndarray** creation: `np.array([1,2,3])`
* **Vectorized ops**: `arr*2`, `arr+arr2`
* **np.arange()**: ranges of values

  ```python
  np.arange(0,10,2)  # [0,2,4,6,8]
  ```

</v-clicks>


---

## Computer Vision (OpenCV)

<v-clicks>


* **imread() / imshow()** ↔ NumPy arrays

  ```python
  img = cv2.imread('img.jpg')
  cv2.imshow('win', img)
  ```
* **highgui**: window display, key events
* **Classifier** (e.g., Viola–Jones face detector)
* **Preprocessing**: convert to grayscale, resize, etc.

</v-clicks>


---

## Version Control & CLI

<v-clicks>


* **Shell**: `mkdir`, `cd`, `ls`, `mv`
* **Git vs. GitHub**: local vs remote
* **Basic Git**: `git init`, `git add .`, `git commit -m` , `git push`
* **Staging**: files in index before commit
* **Branching**: `git checkout -b feature`
* **Pull request**: propose changes for review

</v-clicks>



