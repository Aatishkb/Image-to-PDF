
## Image to PDF Converter

This Python script converts an image file into a PDF document. It utilizes the `Pillow` library for image processing and the `reportlab` library for PDF generation.

### Dependencies

- Pillow
- reportlab

### Notes

- The function resizes the image to fit within a letter-sized PDF page (8.5 x 11 inches).
- Make sure to provide the correct file paths for the input image and output PDF.
- This script supports various image formats such as JPG, PNG, etc.

# Explantion :

1. **Import Libraries**:
   ```python
   from PIL import Image
   from reportlab.lib.pagesizes import letter
   from reportlab.pdfgen import canvas
   ```
   This line imports the necessary modules: `Image` from PIL for image processing, `letter` from reportlab to define the standard letter size for PDF pages, and `canvas` from reportlab to create the PDF canvas.

2. **Define the Conversion Function**:
   ```python
   def convert_image_to_pdf(image_path, pdf_path):
   ```
   This function `convert_image_to_pdf` takes two arguments: `image_path` (the path to the input image file) and `pdf_path` (the desired path for the output PDF file).

3. **Open the Image**:
   ```python
   img = Image.open(image_path)
   ```
   This line opens the image file specified by `image_path` using PIL's `Image.open` function.

4. **Calculate Scaling Factor**:
   ```python
   scale = min(letter[0] / img.width, letter[1] / img.height)
   ```
   This line calculates the scaling factor to fit the image within the PDF page. It divides the width and height of the letter-sized page by the width and height of the image, respectively, and takes the minimum of the two ratios.

5. **Calculate New Image Size**:
   ```python
   new_width = img.width * scale
   new_height = img.height * scale
   ```
   These lines calculate the new width and height of the image based on the calculated scaling factor.

6. **Create PDF Canvas**:
   ```python
   c = canvas.Canvas(pdf_path, pagesize=letter)
   ```
   This line creates a PDF canvas using reportlab's `canvas.Canvas` function. It specifies the `pagesize` parameter as `letter`.

7. **Draw Image on PDF Canvas**:
   ```python
   c.drawImage(image_path, 0, 0, width=new_width, height=new_height)
   ```
   This line draws the image on the PDF canvas at the coordinates (0, 0) with the specified width and height.

8. **Save the PDF**:
   ```python
   c.save()
   ```
   
