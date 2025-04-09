# Finding-Missing-Person-using-Machine-Learning

## Overview

The **Face Recognition System** is a Python-based application that allows for user registration, face image capture, and real-time face recognition using a webcam. The system leverages several popular Python libraries, including OpenCV, Tkinter, MySQL, and Pillow, to perform tasks such as capturing facial images, storing user data, and identifying users based on facial features. This project aims to create a simple yet effective face recognition solution that can be integrated into security or personal identification systems.

## Key Features

- **User Registration**: Allows users to enter personal details (Name, Aadhar number, Mobile number, and Email address).
- **Face Data Collection**: Captures facial images via webcam for each registered user and saves them in a dataset.
- **Face Recognition**: Identifies faces in real-time and matches them against the registered dataset.
- **Database Integration**: Saves user details (name, Aadhar, mobile, and email) in a MySQL database, which is used for identification purposes.

## Technologies Used

- **Python 3.x**: The primary programming language used for the development of this system.
- **OpenCV**: An open-source computer vision library that provides tools for face detection and recognition.
- **Tkinter**: A Python library for creating graphical user interfaces (GUIs).
- **MySQL**: A relational database management system used for storing user data.
- **Pillow (PIL)**: A Python Imaging Library used for image manipulation and processing.

## Code Explanation

### 1. **GUI Setup (Tkinter)**

- The GUI is designed using Tkinter, with entry fields for the user to provide their personal information (name, Aadhar, mobile, and email).
- Buttons are added for **New Entry** and **Detect the face**.

  ![GUI](https://github.com/user-attachments/assets/b2131dae-b6a0-4aed-b644-64fd42e629f4)


### 2. **Dataset Generation (Face Capture)**

- The function `generate_dataset()` handles the capture of facial images.
- It uses OpenCV's **CascadeClassifier** to detect faces from the webcam feed.
- Faces are then cropped and saved as images in the `data/user.ID.ImageNumber.jpg` format.

### 3. **Training the Classifier**

- The `train_classifier()` function loads all the images from the `data/` folder, processes them, and trains the LBPH face recognizer.
- The trained model is saved as `classifier.xml` and used for face detection and recognition.

### 4. **Face Recognition**

- The `detect_face()` function uses the trained classifier to detect faces from the webcam feed in real-time.
- Detected faces are compared with the dataset, and if a match is found, the name of the person is displayed.

## Troubleshooting

- **Tkinter Issues**: Ensure Tkinter is installed on your machine. If you're using a Linux-based system, it may require separate installation.
- **MySQL Connection**: If the system cannot connect to MySQL, make sure the database server is running and the connection details (host, user, password) are correct in the script.
- **Webcam Issues**: If the webcam is not detected, ensure that your camera drivers are correctly installed.

## Contributions

Feel free to contribute to this project! You can fork the repository, make changes, and submit pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
