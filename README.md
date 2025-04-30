# face_recognition_project
Face Track: Smart Attendance System Using Face Recognition

How to setup and run the project.

1. Prerequisites
Make sure the following are installed:
Python 3.8+
pip (Python package installer)
OpenCV
dlib
face_recognition
numpy, pandas
Streamlit

2. Install Required Libraries
Run the following in your terminal:
pip install opencv-python face-recognition numpy pandas streamlit
Note: If dlib gives issues, you may need to install it via wheel or ensure CMake is installed:
pip install cmake
pip install dlib

3. Project Structure (Recommended)
graphql

face-attendance-system/

├── dataset/                   # Contains images of registered users

├── trained_knn_model.clf     # Saved KNN model file

├── take_attendance.py        # Face recognition & attendance script

├── attendance.csv            # CSV file to store attendance

├── streamlit_app.py          # Streamlit UI to display attendance

├── train_model.py            # Script to train KNN model

├── requirements.txt

4. Train the Face Recognition Model
Run this script to train the model using images in dataset/:
python train_model.py
Make sure your train_model.py uses KNN to encode faces and save the model as trained_knn_model.clf.

5. Take Attendance
Run this to capture faces from webcam and mark attendance:
python take_attendance.py
It should use the trained KNN model.
For each recognized face, add a row to attendance.csv.

6. Show Attendance in Streamlit
Run the Streamlit app to show the attendance sheet:
streamlit run streamlit_app.py

Inside streamlit_app.py, you might have:
import streamlit as st
import pandas as pd
st.title("Attendance Sheet")
df = pd.read_csv("attendance.csv")
st.dataframe(df)

7. Final Notes
Ensure proper lighting when capturing faces.
Train with multiple angles per face to improve accuracy.
Attendance file can include timestamps and names:

Name, Time
John Doe, 2025-04-30 10:05:23

Any dependencies or configuration required

Yes, your Face Recognition Based Smart Attendance System will require several key dependencies and configurations. Here's a complete list to get your system running smoothly:

✅ Dependencies
You can install all dependencies at once by creating a requirements.txt, or install them manually.
🧱 Core Libraries
pip install opencv-python
pip install face-recognition
pip install numpy
pip install pandas
pip install streamlit

Optional but helpful:
pip install imutils
pip install scikit-learn

🛠️ System-Level Requirements
1. CMake
Required to build dlib, which is used by face_recognition.
Windows:
Install CMake from cmake.org
Add it to your PATH during installation.

Linux (Debian/Ubuntu):
sudo apt-get install cmake

2. dlib (used by face_recognition)
Sometimes installing face_recognition via pip handles this, but if not:
pip install dlib

If it fails, try prebuilt wheels:
pip install https://github.com/RPi-Distro/python-dlib/releases/download/19.22.99/dlib-19.22.99-cp38-cp38-win_amd64.whl
(Match your Python version and OS)

⚙️ Configuration Required
1. Directory Setup
Ensure these folders/files exist:

project/
├── dataset/               # Images of registered people
├── attendance.csv         # Output file (create empty if needed)

2. .env (optional)
If you'd like to make file paths configurable:

MODEL_PATH=trained_knn_model.clf
ATTENDANCE_FILE=attendance.csv

Then read it in Python using:

from dotenv import load_dotenv
import os
load_dotenv()
model_path = os.getenv("MODEL_PATH")

3. Model File
You need to train and save the KNN model as a .clf file. If it doesn't exist, run your train_model.py script before attempting attendance capture.

📦 requirements.txt (Recommended)
Here’s a sample you can use:

opencv-python
face-recognition
dlib
numpy
pandas
streamlit
imutils
scikit-learn
python-dotenv

Install it via:
pip install -r requirements.txt






