## Workflow of the Grayscale Conversion & Pixel Modification Script

1. **Import the PIL Image Module**

   ```python
   from PIL import Image
   ```

   * Provides tools to open, manipulate, and save images.

2. **Open the Original Image**

   ```python
   CITRA = Image.open('Foto/gambar.jpeg')
   ```

   * Loads the color image file into memory as a PIL `Image` object.

3. **Convert to Grayscale**

   ```python
   CITRA_GRAYSCALE = CITRA.convert('L')
   ```

   * Changes the image mode to “L” (luminance), so each pixel holds a single intensity value (0–255).

4. **Read Image Dimensions**

   ```python
   width  = CITRA_GRAYSCALE.size[0]  # horizontal size (columns)
   height = CITRA_GRAYSCALE.size[1]  # vertical size (rows)
   ```

   * These values can help if you need to iterate over every pixel.

5. **Load the Pixel Access Object**

   ```python
   PIXELS = CITRA_GRAYSCALE.load()
   ```

   * `PIXELS` is now a 2D array-like interface:

     * Read any pixel with `PIXELS[x, y]`.
     * Write any pixel by assigning `PIXELS[x, y] = new_value`.

6. **Modify a Specific Pixel**

   ```python
   PIXELS[3, 8] = 128
   print(PIXELS[3, 8])  # outputs: 128
   ```

   * Here we set the pixel at column 3, row 8 to mid-gray (128), then print its new value.

7. **Save the Resulting Grayscale Image**

   ```python
   CITRA_GRAYSCALE.save('Grayscale/hasil_grayscale1.jpeg')
   ```

   * Writes out the modified image into the `Grayscale` folder under the new filename.

---

### Full Example

```python
from PIL import Image

# 1. Open image
CITRA = Image.open('Foto/gambar.jpeg')

# 2. Convert to grayscale
CITRA_GRAYSCALE = CITRA.convert('L')

# 3. Get dimensions (optional)
width, height = CITRA_GRAYSCALE.size

# 4. Load pixel data
PIXELS = CITRA_GRAYSCALE.load()

# 5. Modify one pixel and verify
PIXELS[3, 8] = 128
print(PIXELS[3, 8])  # Should print: 128

# 6. Save the modified image
CITRA_GRAYSCALE.save('Grayscale/hasil_grayscale1.jpeg')
```
