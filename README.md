This repository contains a program designed to identify driver's drowsiness based on real-time camera image processing techniques. The system triggers warning alarms corresponding to different levels of drowsiness detected during driving.

Description
Using a real-time Vision System, the program applies techniques for detecting drivers' faces and eyes, removes lighting effects that may cause false positives in eye detection, and leverages supervised learning algorithms to classify the level of drowsiness.

The Histogram of Oriented Gradients (HOG) and learned Face Landmark estimation techniques are used for detecting faces and eyes. To eliminate lighting effects, the light channels of the original images are separated, inverted, and then merged with the grayscale version of the images.

The system uses the concept of Eye Aspect Ratio (EAR) to detect drowsiness. The K-Nearest Neighbors (KNN) algorithm is used to classify drowsiness into three stages, and the system triggers differential alarms based on the detected level.

This technology contributes to research and development in the field of intelligent vehicle systems and vision computing.

System Diagram
The diagram below outlines the drowsiness detection process:

Capture face images from the camera.
Grayscale the image.
Process lighting effects.
Apply HOG for face detection.
Perform face landmark estimation.
Detect drowsiness.
Face and Eye Detection
The system utilizes HOG face pattern detection to locate faces from grayscale images, and Face Landmark Estimation to identify 68 key landmarks on the face, which help in identifying the eye regions.

Preprocessing
The system addresses lighting effects, which significantly impact image processing. The lightness channel is separated from the original image, inverted, and then merged with the grayscale version to create a clear image. Luma coding is used to convert the images to grayscale, and LAB color space is employed to separate the lightness, followed by median filtering to adjust the lighting values to match actual conditions.

Drowsiness Detection
The Eye Aspect Ratio (EAR), calculated from six (x, y) coordinates around each eye, helps in detecting whether the eyes are open or closed. When eyes are open, the EAR is greater than zero; when closed, the EAR approaches zero. The program sets the threshold for detecting drowsiness at 50% of the average EAR value when the eyes are open. If the EAR value falls below this threshold for a set number of frames (27 frames or 0.9 seconds), an alarm is triggered.

Drowsiness Level Selection
The program calculates drowsiness levels based on factors such as driving speed, response time, and the duration for which the eyes remain closed. It categorizes drowsiness into three stages, using the KNN algorithm to determine the level of drowsiness based on the EAR values over time. Alarms of increasing intensity are triggered depending on the severity of drowsiness.

Test Results
You can view the difference between the system's performance before and after applying preprocessing:

Before preprocessing
After preprocessing
Execution
To run the code, open the drowsiness_detector.ipynb file and run it using Jupyter Notebook (or Python).

References
Machine Learning is Fun! Part 4: Modern Face Recognition with Deep Learning
Real-Time Eye Blink Detection using Facial Landmarks
Eye Blink Detection with OpenCV, Python, and dlib
How to Install dlib
Histograms of Oriented Gradients for Human Detection
Removing Lighting Effects
This project demonstrates a practical application of computer vision and machine learning techniques in improving road safety by detecting driver drowsiness in real-time.
  
