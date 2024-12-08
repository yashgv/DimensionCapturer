# Dimension Capturer

## Project Overview
This project demonstrates a web-based application for detecting and measuring objects in an image using OpenCV and Python as the backend and React Native as the frontend. It leverages computer vision techniques to detect objects and their dimensions using an ArUco marker for calibration. The backend processes the image and provides measurements in centimeters, while the React Native frontend allows users to upload images and view the results.

---

## Features
- **Object Detection:** Identify and measure objects in images using a homogeneous background detector.
- **ArUco Marker Calibration:** Use ArUco markers to determine the pixel-to-centimeter ratio for accurate measurements.
- **Backend in Python:** Built with Flask and OpenCV, ensuring efficient and scalable image processing.
- **Frontend in React Native:** A mobile-friendly UI for uploading images and displaying results.
- **CORS Enabled:** Enables cross-origin requests between the frontend and backend.
- **Logging:** Logs incoming requests and responses for debugging purposes.

---

## Architecture
- **Backend (Python/Flask):** Processes images to detect objects and measure their dimensions. Uses OpenCV for computer vision tasks and Flask to handle API endpoints.
- **Frontend (React Native):** Provides a user-friendly interface for uploading images and displaying results with visual annotations.

---

## How It Works
1. The user uploads an image from the React Native app.
2. The image is sent to the Flask backend via the `/process-image/` endpoint.
3. The backend uses OpenCV to:
   - Detect the ArUco marker in the image.
   - Calculate the pixel-to-centimeter ratio.
   - Detect objects and compute their dimensions (length and width).
   - Annotate the image with dimensions and boundaries.
4. The processed image, along with a success or error message, is returned to the frontend.
5. The frontend displays the annotated image and measurement details to the user.

---

## API Endpoints

### `POST /process-image/`
**Description:** Accepts an image file and returns the processed image with annotated measurements.

**Request Parameters:**
- `file` (Form Data): The image file to be processed.

**Response:**
- **Success:** Returns the processed image (PNG format) with headers containing a message (`X-Process-Message`).
- **Error:** HTTP status `400` with an error message.

---

## Setup Instructions

### Backend
1. Clone the repository.
2. Create a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
3. Install dependencies:
   ```bash
   pip install flask flask-cors opencv-python-headless numpy
   ```
4. Run the Flask server:
   ```bash
   python app.py
   ```
5. The server will run at `http://127.0.0.1:5000`.

### Frontend
1. Clone the React Native frontend repository (if separate).
2. Install dependencies:
   ```bash
   npm install
   ```
3. Configure the API URL in your React Native project to point to the backend (`http://127.0.0.1:5000/process-image/`).
4. Run the app:
   ```bash
   npm start
   ```
5. Use an emulator or physical device to test the application.

---

## Technologies Used
- **Backend:** Python, Flask, OpenCV, NumPy
- **Frontend:** React Native
- **Others:** Flask-CORS, Logging

---

## Logging
- Logs are saved in `info.log` to capture request payloads and responses for troubleshooting.

---

## Future Improvements
- Add support for multiple object detection methods.
- Enhance the frontend UI/UX with real-time preview.
- Support more image formats and handle larger file uploads.
- Include detailed error handling and reporting.

---

