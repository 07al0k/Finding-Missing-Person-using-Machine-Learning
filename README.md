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

## Installation and Setup

To run this project, you will need to set up the necessary environment, including Python libraries, MySQL, and the Haar Cascade classifier file. Follow these steps to get the system up and running:

### 1. Clone the Repository

First, clone the repository to your local machine using Git:

```bash
git clone https://github.com/your-username/face-recognition-system.git
```

Navigate to the project directory:

```bash
cd face-recognition-system
```

### 2. Install Required Libraries

The system requires several Python libraries, including OpenCV, Tkinter, MySQL connector, and Pillow. You can install these using `pip`. If you don’t have these libraries installed yet, you can do so by running the following commands:

```bash
pip install opencv-python opencv-python-headless
pip install mysql-connector-python
pip install pillow
```

**Note**: Tkinter should already be installed with your Python installation. If you encounter any issues with Tkinter, you may need to install it separately based on your operating system.

### 3. Set Up MySQL Database

To store user data, you need to create a MySQL database and table. Open the MySQL client and run the following SQL commands:

1. **Create the database** (if it doesn’t exist already):

```sql
CREATE DATABASE lost;
```

2. **Create the table** to store user details:

```sql
CREATE TABLE info_lost (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    aadhar VARCHAR(12),
    mobile VARCHAR(15),
    email VARCHAR(100)
);
```

This table will hold user information such as their name, Aadhar number, mobile number, and email.

### 4. Download Haar Cascade Classifier

OpenCV uses a Haar Cascade classifier for face detection. You need to download the Haar Cascade XML file and place it in the project directory. You can download it from OpenCV’s GitHub repository:

[Download Haar Cascade Classifier](https://github.com/opencv/opencv/tree/master/data/haarcascades)

Save the file as `haarcascade_frontalface_default.xml` in the project directory.

### 5. Run the Application

With all dependencies set up, you can now run the application. The system uses a simple GUI built with Tkinter that allows you to:

- **Register a new user** by entering personal details (Name, Aadhar, Mobile, and Email).
- **Capture facial images** and save them to the database for future recognition.
- **Detect faces** and match them with registered users.

To run the application, simply execute the following command:

```bash
python face_recognition_system.py
```

### 6. User Interaction

Upon running the application, a Tkinter window will appear with fields for entering user details (Name, Aadhar Number, Mobile Number, and Email). The steps involved are:

1. **New Entry**: When you click the "New Entry" button, the system checks if all the required fields are filled. If not, it prompts you to complete the information. Upon successful registration, the data is saved in the MySQL database, and facial images are captured using the webcam. These images are saved and used to train the face recognition model.
   
2. **Face Capture**: The system starts capturing images from the webcam to create a dataset of facial images. These images are resized, converted to grayscale, and stored in a folder named `data/`. The system captures 200 images per user and associates them with a unique ID.
   
3. **Face Recognition**: After the dataset is ready and the model has been trained, you can click the "Detect the face" button to start real-time face recognition. The system uses the webcam to detect faces and match them with the registered dataset. If a match is found, the user’s name is displayed; if not, it shows "UNKNOWN".

### 7. Training the Classifier

After capturing the images, the system trains a face recognition model using the **LBPH (Local Binary Patterns Histograms)** algorithm. This model is then saved as `classifier.xml`. The classifier is used later to identify faces in real-time during the detection phase.

The `train_classifier()` function handles the training process, where it loads the dataset, processes the images, and trains the model.

## Code Explanation

### 1. **GUI Setup (Tkinter)**

- The GUI is designed using Tkinter, with entry fields for the user to provide their personal information (name, Aadhar, mobile, and email).
- Buttons are added for **New Entry** and **Detect the face**.

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
