Overview
This is a simple web app that lets you upload an image of a CAPTCHA and automatically decodes the text using OCR. It uses:
- Flask for the web server
- Pillow (PIL) for image handling and basic preprocessing
- pytesseract to interface with the Tesseract OCR engine

Setup
1) Prerequisites
- Python 3.9+ recommended
- Tesseract OCR engine must be installed on your system

Install Tesseract:
- macOS (Homebrew):
  brew install tesseract
- Ubuntu/Debian:
  sudo apt-get update
  sudo apt-get install -y tesseract-ocr
- Windows:
  - Download from: https://github.com/tesseract-ocr/tesseract
  - Install, then note the path to tesseract.exe (e.g., C:\Program Files\Tesseract-OCR\tesseract.exe)

2) Python dependencies
It’s recommended to use a virtual environment.

- Create and activate a venv:
  python -m venv .venv
  # Windows
  .venv\Scripts\activate
  # macOS/Linux
  source .venv/bin/activate

- Install packages:
  pip install flask pillow pytesseract

3) Configure Tesseract path (Windows or custom path)
If Tesseract isn’t on your PATH, set an environment variable to its executable:

- Windows (PowerShell):
  setx TESSERACT_CMD "C:\Program Files\Tesseract-OCR\tesseract.exe"
  # Then restart your terminal or system to apply

- macOS/Linux (temporary for current shell):
  export TESSERACT_CMD="$(which tesseract)"

Usage
1) Run the app
python index.html

By default it starts on http://localhost:8000

2) Use the app
- Open the URL in your browser.
- Use the image upload form to select a CAPTCHA image (PNG/JPG/etc).
- Click “Decode Text”.
- The page will show a preview of the uploaded image and the detected text.

Notes
- The app applies simple preprocessing (grayscale, autocontrast, threshold) to improve OCR.
- OCR is configured with a whitelist of alphanumeric characters and page segmentation mode suitable for single-line text (PSM 7).
- If you see “Tesseract not found” errors, ensure Tesseract is installed and your TESSERACT_CMD or PATH is properly configured.

Security/Privacy
- Uploaded images are processed in-memory only and are not stored on disk by the application.