# CAPTCHA OCR Decoder

## Overview
This is a simple web app that lets you upload a CAPTCHA image and decodes the text automatically using Python’s pytesseract (Tesseract OCR) library. The app provides an image upload form and displays the detected text on the page after processing.

Key points:
- Built with Flask (Python)
- Uses Pillow for image handling and light preprocessing
- Uses pytesseract to run OCR (requires Tesseract OCR binary installed on the system)

## Setup
1) Prerequisites
- Python 3.8+
- Tesseract OCR binary installed on your system and accessible on PATH

Install Tesseract:
- macOS (Homebrew):
  brew install tesseract
- Ubuntu/Debian:
  sudo apt-get update && sudo apt-get install -y tesseract-ocr
- Windows (Chocolatey):
  choco install tesseract

If Tesseract is installed in a non-standard location, set an environment variable before running:
- macOS/Linux:
  export TESSERACT_CMD=/full/path/to/tesseract
- Windows (PowerShell):
  $env:TESSERACT_CMD="C:\Program Files\Tesseract-OCR\tesseract.exe"

2) Python dependencies
Install required packages:
- pip install Flask Pillow pytesseract

## Usage
1) Run the app:
- python index.html

2) Open the browser to:
- http://127.0.0.1:5000

3) Upload a CAPTCHA image and click “Decode”.
- The page will show a preview of the image and the detected text.

Notes:
- For best results, use clear, high-contrast images. The app applies grayscale + thresholding and uses an alphanumeric whitelist to improve OCR on typical CAPTCHAs.

## Improvements from Round 1
- Added preprocessing pipeline (grayscale + dynamic invert + thresholding) for better OCR accuracy on noisy CAPTCHAs.
- Tuned Tesseract configuration with page segmentation modes (PSM 7 with fallback to 8) and an alphanumeric whitelist for higher precision.
- Image preview is now displayed using an in-memory data URL; no files are written to disk.
- Improved validation and error messages for unsupported formats and empty uploads.
- Single-file app with clearer styling and layout, while keeping setup simple.