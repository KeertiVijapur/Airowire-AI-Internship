# Transforming Images (https://www.youtube.com/watch?v=6Qs3wObeWwc)

Image processing is a common task in data pipelines, machine learning workflows, and automation systems. Python and command-line tools provide powerful ways to manipulate images programmatically.

In this section we explore:

* **Python Pillow (PIL)** for image manipulation in Python
* **ImageMagick** for command-line image processing (https://www.youtube.com/watch?v=wjcBOoReYc0)
* Techniques for resizing, cropping, filtering, and batch processing images

---

# Image Processing with Pillow (PIL) (https://www.youtube.com/watch?v=dkp4wUhCwR4)

**Pillow** is the modern Python imaging library derived from PIL (Python Imaging Library). It provides powerful tools for:

* Loading and saving images
* Resizing and cropping
* Applying filters and effects
* Color adjustments
* Drawing text and overlays
* Batch processing large image datasets

Supported formats include:

```
PNG
JPEG
GIF
BMP
TIFF
WebP
```

Install Pillow:

```bash
pip install pillow
```

---

# Loading and Displaying Images

```python
from PIL import Image

img = Image.open("image.jpg")
img.show()
```

Basic image properties:

```python
print(img.size)     # (width, height)
print(img.format)   # JPEG / PNG
print(img.mode)     # RGB / L / HSV
```

---

# Saving Images in Different Formats

```python
img = Image.open("image.jpg")
img.save("image.png")
```

Pillow automatically converts formats when saving.

---

# Batch Converting Images

Convert all JPEG images in a directory to PNG.

```python
import os
from PIL import Image

for file in os.listdir("."):
    if file.endswith(".jpg"):
        img = Image.open(file)

        filename, ext = os.path.splitext(file)

        img.save(f"pngs/{filename}.png")
```

Useful for:

* dataset preparation
* web image pipelines
* automated file processing

---

# Resizing Images (Thumbnail Generation)

```python
from PIL import Image

size = (300, 300)

img = Image.open("image.jpg")
img.thumbnail(size)

img.save("thumbnail.jpg")
```

The `thumbnail()` method preserves the **aspect ratio** automatically.

---

# Batch Resize Example

```python
import os
from PIL import Image

size = (300, 300)

for file in os.listdir("."):
    if file.endswith(".jpg"):

        img = Image.open(file)
        img.thumbnail(size)

        filename, ext = os.path.splitext(file)

        img.save(f"300/{filename}_300{ext}")
```

Use cases:

* generating thumbnails
* creating responsive images
* dataset preprocessing

---

# Rotating Images

```python
img = Image.open("image.jpg")

rotated = img.rotate(90)

rotated.save("rotated.jpg")
```

Rotate any angle:

```python
img.rotate(45)
```

---

# Convert to Black & White

```python
img = Image.open("image.jpg")

bw = img.convert("L")

bw.save("bw.jpg")
```

`L` represents grayscale mode.

---

# Applying Filters

Import image filters:

```python
from PIL import ImageFilter
```

Blur image:

```python
img = img.filter(ImageFilter.GaussianBlur(radius=5))
```

Other filters:

```
ImageFilter.BLUR
ImageFilter.SHARPEN
ImageFilter.EDGE_ENHANCE
ImageFilter.EMBOSS
```

---

# Cropping Images

Cropping requires coordinates:

```
(left, top, right, bottom)
```

Example:

```python
img = Image.open("image.jpg")

crop = img.crop((50, 120, 250, 230))

crop.save("crop.jpg")
```

---

# Flipping and Transposing

```python
img.transpose(Image.FLIP_LEFT_RIGHT)
img.transpose(Image.FLIP_TOP_BOTTOM)
img.transpose(Image.ROTATE_90)
```

---

# Resizing Algorithms

Pillow supports multiple interpolation techniques:

| Method   | Quality              |
| -------- | -------------------- |
| NEAREST  | Fast but low quality |
| BILINEAR | Balanced             |
| BICUBIC  | High quality         |
| LANCZOS  | Best quality         |

Example:

```python
img.resize((300,300), Image.LANCZOS)
```

---

# Adding Text Watermarks

```python
from PIL import ImageDraw, ImageFont

img = Image.open("image.jpg")

draw = ImageDraw.Draw(img)

font = ImageFont.truetype("arial.ttf", 40)

draw.text((10,10), "Sample Text", fill=(255,255,255), font=font)

img.save("watermarked.jpg")
```

---

# Image Enhancement

Enhance brightness, contrast, color, and sharpness.

```python
from PIL import ImageEnhance

img = Image.open("image.jpg")

enhancer = ImageEnhance.Brightness(img)
img = enhancer.enhance(1.5)
```

Enhancement types:

```
ImageEnhance.Color
ImageEnhance.Contrast
ImageEnhance.Brightness
ImageEnhance.Sharpness
```

Values:

```
1.0 → original
>1  → stronger
<1  → weaker
```

---

# Alpha Blending (Combining Images)

Blend two images:

```python
from PIL import Image

img1 = Image.open("image1.jpg")
img2 = Image.open("image2.jpg")

img2 = img2.resize(img1.size)

blend = Image.blend(img1, img2, alpha=0.5)

blend.show()
```

Alpha values:

```
0 → only first image
1 → only second image
0.5 → mix of both
```

---

# Convert Images to NumPy Arrays

Useful for machine learning and computer vision.

```python
import numpy as np

array = np.array(img)
```

Convert back:

```python
Image.fromarray(array)
```

---

# Image Processing with ImageMagick

**ImageMagick** is a powerful command-line tool for image manipulation.

It is widely used for:

* batch image processing
* resizing large image collections
* converting formats
* creating thumbnails
* adding watermarks
* image analysis

Install:

```bash
sudo apt install imagemagick
```

or

```bash
brew install imagemagick
```

---

# Basic ImageMagick Commands

### Convert Format

```bash
convert input.jpg output.png
```

---

### Resize Image

```bash
convert input.jpg -resize 1000x1000 output.jpg
```

Maintain aspect ratio automatically.

Force exact size:

```bash
convert input.jpg -resize 1000x1000! output.jpg
```

---

### Resize by Percentage

```bash
convert input.jpg -resize 50% output.jpg
```

---

# Extract Image Metadata

```bash
identify image.jpg
```

Detailed info:

```bash
identify -verbose image.jpg
```

Shows:

* resolution
* color space
* file size
* histogram
* metadata

---

# Create Thumbnails

```bash
convert image.jpg -thumbnail 200x200 thumb.jpg
```

---

# Batch Processing Images

Resize all images in a folder:

```bash
mogrify -resize 1024x1024 *.jpg
```

Output to another folder:

```bash
mogrify -path output -resize 1024x1024 *.jpg
```

---

# Add Watermarks

```bash
convert image.jpg \
-gravity southeast \
-draw "text 10,10 'Copyright'" \
watermarked.jpg
```

---

# Advanced Image Effects

### Blur

```bash
convert input.jpg -blur 0x5 blur.jpg
```

### Sharpen

```bash
convert input.jpg -sharpen 0x3 sharp.jpg
```

### Edge Detection

```bash
convert input.jpg -edge 1 edges.jpg
```

---

# Batch Watermark Script

```bash
for f in *.jpg
do
convert "$f" \
-gravity southeast \
-draw "text 10,10 'Copyright'" \
"watermarked/$f"
done
```

---

# When to Use Each Tool

| Tool        | Best For                      |
| ----------- | ----------------------------- |
| Pillow      | Python automation pipelines   |
| ImageMagick | command-line batch processing |
| OpenCV      | computer vision & ML          |
| FFmpeg      | video/image frame extraction  |

---

# Summary

Image processing can be automated easily using Python and command-line tools.

Key workflows include:

* resizing images for web applications
* generating thumbnails
* converting formats
* preparing datasets for machine learning
* batch processing thousands of images

Using tools like **Pillow and ImageMagick**, large-scale image manipulation tasks can be automated efficiently.
