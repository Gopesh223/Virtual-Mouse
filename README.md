
# Virtual Mouse




##  Overview
This project aims to develop a program that detects hands which enables us to control the screen without using a mouse/touchpad.
## Libraries Used
OpenCV

Mediapipe

PyAutoGUI
## System requirements

The system requires the latest version of Python and the aforementioned 3 libraries.
## Installation
```bash
pip install opencv-python
```
```bash
pip install mediapipe
```
```bash
pip install pyautogui
```
## Working of the Code
This program makes use of a framework called MediaPipe which is developed by Google. This library was created to tackle difficult AI problems like face detetction, facial landmarks, handtracking and object detetction.

The module we are using is called handtracking. It uses two modules at the backend-
1) Palm detetction
2) Hand landmarks

The Palm detection provides a cropped image of the hand. Then the Hand landmarks module finds 21 different points on your hand

This hand landmarks module was trained using manually annotated images(about 30000) of different hands.

We start the video and flip it about the ordinate axis so that it is not mirrored.
We then use inbuilt functions of the MediaPipe library to detect the hand and also the 21 different landmarks on the hand.

To find the coordinate of each landmark which is initally in the of form of ratio(i.e values ranging from 0 to 1), we need to multiply the x-coordinate using the width and the y-coordinate using the length to get the exact coordinate location in the form of pixel number.

The landmark of the tip of the index finger is 8. This landmark number is used to navigate across the screen using the PyAutoGUI library. Here before doing that, we need to scale the frame again.

The landmark of the tip of the thumb is 4. This landmark number is used to perform the mouse-click operation in coordination with the tip of the thumb. We find the difference between the y coordinates of the tip of the thumb and index finger. If this difference is below a certain pixel value, then we consider it to a be a click and use PyAutoGUI to generate a mouse-click.

## Hand Landmark 
![image](https://github.com/user-attachments/assets/2a2514a6-c17b-4e22-95ba-23e73264a621)

