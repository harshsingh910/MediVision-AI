# Medical AI API

This project provides a Flask-based API for analyzing medical images, prescriptions, and symptoms using Google Gemini AI. It enhances medical image quality, processes prescriptions, and predicts potential conditions based on symptoms.

## Features
- **Medical Image Analysis**: Enhances and analyzes medical images (X-rays, MRIs, CT scans, etc.).
- **Symptom Analysis**: Identifies possible medical conditions based on patient symptoms.
- **Prescription Processing**: Extracts details from handwritten prescriptions and identifies possible drug interactions.
- **Medical Report Analysis**: Extracts and interprets data from medical reports.

## Technologies Used
- **Flask** (API framework)
- **Google Gemini AI** (Medical analysis model)
- **OpenCV** & **PIL** (Image processing)
- **Flask-CORS** (Cross-Origin Resource Sharing)
- **Werkzeug** (File handling and security)
- **NumPy** (Image manipulation)

## Installation
### Prerequisites
- Python 3.8+
- Google Gemini AI API Key
- Virtual environment (optional but recommended)

### Steps
1. Clone the repository:
   ```sh
   git clone <repository_url>
   cd <repository_name>
   ```
2. Create a virtual environment (optional):
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
4. Set up environment variables:
   ```sh
   export GOOGLE_API_KEY="your_google_api_key"
   ```
5. Run the Flask application:
   ```sh
   python api.py
   ```

## API Endpoints
### 1. Health Check
- **Endpoint:** `/health`
- **Method:** `GET`
- **Response:** `{ "status": "healthy", "timestamp": "<server_time>" }`

### 2. Analyze Medical Image
- **Endpoint:** `/api/analyze_medical_image`
- **Method:** `POST`
- **Form Data:** Image file, optional enhancements (`contrastBoost`, `noiseReduction`, `edgeEnhancement`)
- **Response:** JSON with medical findings and analysis.

### 3. Analyze Symptoms
- **Endpoint:** `/api/analyze_symptoms`
- **Method:** `POST`
- **Request Body:** `{ "symptoms": ["fever", "cough"], "patientInfo": { "age": 30, "gender": "Male" } }`
- **Response:** JSON with possible medical conditions.

### 4. Process Prescription
- **Endpoint:** `/api/process_prescription`
- **Method:** `POST`
- **Form Data:** Image file of a prescription
- **Response:** Extracted prescription details and possible drug interactions.

### 5. Analyze Medical Report
- **Endpoint:** `/api/analyze_medical_report`
- **Method:** `POST`
- **Form Data:** Medical report image file
- **Response:** JSON with extracted report details, abnormal findings, and recommendations.

## Deployment
For production, use a WSGI server like Gunicorn:
```sh
pip install gunicorn
export GOOGLE_API_KEY="your_google_api_key"
gunicorn -w 4 -b 0.0.0.0:5000 api:app
```

## License
This project is licensed under the MIT License. See `LICENSE` for details.


