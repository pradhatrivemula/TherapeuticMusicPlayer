# Therapeutic Music Player

This project integrates facial emotion recognition with a music player to create an emotion-aware music experience. It uses machine learning techniques to detect the user's current emotional state through their facial expressions and plays music that matches that emotion. The user interface is built with HTML, CSS, and JavaScript, while the core functionality is powered by Python, leveraging libraries such as OpenCV for face detection and emotion recognition, and Eel for creating a simple web application.

## Features

- **Emotion Recognition:** Utilizes OpenCV's facial recognition to identify user emotions like angry, happy, sad, and neutral.
- **Dynamic Music Selection:** Plays music that aligns with the detected emotion from a predefined set.
- **Model Training and Updating:** Allows for taking new images and retraining the model to improve accuracy over time.
- **Web Interface:** A simple and interactive web interface for easy interaction with the application.

## Prerequisites

Before you begin, ensure you have met the following requirements:
- **Python 3.x:** This project is developed with Python, so you need Python installed on your system.
- **OpenCV:** For facial recognition and image processing.
- **Eel:** To create the web interface.
- **NumPy:** Required by OpenCV for array operations.
- **Other Python Libraries:** `argparse`, `time`, `os`, `glob`, `random`.

This code is developed and tested on Ubuntu Linux, but it should be compatible with other operating systems that support Python and the required libraries.

## Installation

1. **Clone the repository** or download the source code.
2. **Install dependencies:** Run the following command to install the required Python libraries: pip install opencv-python eel numpy argparse
3. **Prepare the Dataset:** If you're planning to update the model, gather images for each emotion and place them in the `dataset` folder structured by emotion names.

## Usage

To start the application, navigate to the project directory in your terminal and run: python capture.py


This command launches the web interface in your default web browser and initializes the emotion detection and music player.

### Updating the Model

If you need to update the emotion recognition model with new images, start the application with the `--update` flag:

python capture.py --update

Follow the prompts to capture new images for each emotion. The application will then retrain the model to include the new data.

## Development

- **Adding More Emotions:** You can add more emotions by updating the `emotions` list in the code and adding the corresponding music and images.
- **Improving the Model:** Enhance the model's accuracy by providing a diverse set of facial expression images for training.
- **Customizing the Web Interface:** Modify `main.html` and associated CSS/JS files to personalize the UI.


## Contributing

Contributions to this project are welcome, including bug reports, feature requests, and pull requests. Please ensure to follow the project's coding standards and contribute towards making it more efficient and user-friendly.


