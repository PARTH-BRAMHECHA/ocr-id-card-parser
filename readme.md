Document Scanner Web App
Overview
This is a Flask-based web application that extracts information from uploaded images of Aadhaar or PAN cards using OCR (Optical Character Recognition) via the OCR.Space API. The app processes images to identify and extract details such as Aadhaar or PAN numbers, names, dates of birth, and father's names (for PAN cards).
Features

Upload images in JPG, JPEG, or PNG formats.
Extracts Aadhaar number, name, and date of birth from Aadhaar cards.
Extracts PAN number, name, father's name, and date of birth from PAN cards.
Validates file formats and provides error messages for unsupported files or invalid card details.
Uses OCR.Space API for text extraction from images.
Simple web interface for uploading images and displaying results.

Requirements

Python 3.6+
Flask
Requests
python-dotenv
Werkzeug

Installation

Clone the repository:
git clone <repository-url>
cd document-scanner


Create a virtual environment (optional but recommended):
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install dependencies:
pip install flask requests python-dotenv werkzeug


Set up environment variables:

Create a .env file in the project root.
Add your OCR.Space API key:OCR_API_KEY=your_ocr_space_api_key


Obtain an API key from OCR.Space.


Create an uploads folder:

The app automatically creates an uploads folder for storing uploaded images if it doesn't exist.



Usage

Run the application:
python app.py

The app will start in debug mode and be accessible at http://127.0.0.1:5000.

Access the web interface:

Open a browser and navigate to http://127.0.0.1:5000.
Upload an Aadhaar or PAN card image (JPG, JPEG, or PNG).
View the extracted information or error messages on the webpage.



File Structure

app.py: Main Flask application with routes and logic for processing images.
templates/index.html: HTML template for the web interface (not included here but required).
uploads/: Directory for storing uploaded images.
.env: Environment file for storing the OCR.Space API key.

How It Works

File Upload:

Users upload an image via the web interface.
The app validates the file format and saves it to the uploads folder.


OCR Processing:

The image is sent to the OCR.Space API, which extracts text from the image.


Data Extraction:

Regular expressions are used to identify Aadhaar or PAN numbers and dates of birth.
Name and father's name (for PAN) are extracted based on text patterns and card-specific logic.


Result Display:

Extracted details are displayed on the webpage, or an error message is shown if no valid card is detected.



Limitations

Requires a valid OCR.Space API key.
Accuracy depends on image quality and OCR.Space API performance.
Only supports JPG, JPEG, and PNG formats.
Name and father's name extraction may not always be accurate due to varying card formats.

Notes

Ensure the .env file is not committed to version control for security.
The index.html template must be created in the templates folder for the app to render the web interface.
Debug mode is enabled by default; disable it in production for security.


