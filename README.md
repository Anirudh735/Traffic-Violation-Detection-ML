# 🚦 Traffic Violation Detection System using Machine Learning

## 🔍 Overview
This project is a real-time **Traffic Violation Detection System** built using **YOLOv8** for vehicle detection and **EasyOCR** for number plate recognition. It is designed to monitor live traffic footage, detect violations such as red light jumping or restricted zone entries, recognize vehicle number plates, and display everything on a real-time **Flask dashboard**. The system also logs each violation with metadata and a screenshot for record-keeping and enforcement.

---

## 🎯 Objective
- Detect traffic violations using video surveillance.
- Recognize vehicle number plates from the frames.
- Display live detections and log data on a web dashboard.
- Maintain a record of detected violations with time, vehicle type, and plate number.

---

## 🛠 Technologies Used
- **YOLOv8** – for vehicle detection (`ultralytics` library)
- **EasyOCR** – for optical character recognition (number plate detection)
- **OpenCV** – for frame processing
- **Flask** – for creating the web dashboard
- **PyNgrok** – to host Flask app publicly via Colab
- **Google Colab** – for cloud-based development & demo

---

## 📁 Folder Structure

traffic_violation/
├── app.py # Main Flask backend
├── requirements.txt # Dependencies
├── README.md # Project documentation
├── static/
│ └── violations/ # Stored violation screenshots
├── templates/
│ ├── index.html # Live video stream UI
│ └── violations.html # Violations log UI


---

## 📦 Features
- 🔍 **Real-time object detection** of vehicles (car, bus, truck, motorcycle)
- 🔤 **Live number plate recognition** using OCR
- 📸 **Automatic screenshot capture** for each unique violation
- 📃 **Violation logging** with timestamp, plate number, and vehicle type
- 🌐 **Live dashboard** to display stream and logged violations
- ☁️ **Colab + Ngrok compatible** for easy demo hosting

---

## 🧪 How It Works

1. User uploads a video (e.g., `traffic.mp4`) to Colab.
2. YOLOv8 processes each frame and detects vehicles.
3. EasyOCR reads the number plate from the detected region.
4. Each vehicle that violates rules is logged **once** (no duplicate entries).
5. A screenshot is taken and saved in `/static/violations/`.
6. Flask dashboard shows:
   - Live feed from the video
   - Logged violations with images and metadata
7. The dashboard is made public using Ngrok.

---

## 💻 Setup & Execution

### 🟢 On Google Colab
1. Upload the project folder or run the auto-setup notebook.
2. Upload your traffic video.
3. Install dependencies:
   ```bash
   !pip install flask pyngrok ultralytics easyocr opencv-python-headless
Run app.py from /content/traffic_violation.

Copy and open the Ngrok public link to access the dashboard.

📋 Sample Violation Log Entry
Timestamp	          Plate Number	  Vehicle Type	  Screenshot
2025-05-08 14:22:10	  TN01AB1234	  Car	


🙋‍♂️ Future Improvements
Integrate with live CCTV feeds

Export violation logs to Excel/CSV

Add authentication to the dashboard

Categorize different types of violations

Enable real-time alert notifications



