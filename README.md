# Hand Gesture Recognition with ASL and ARSL

This project implements a hand gesture recognition system using computer vision and machine learning models to classify American Sign Language (ASL) and Arabic Sign Language (ARSL) gestures. It utilizes OpenCV, Mediapipe, and deep learning models to detect and classify hand gestures in real-time from webcam input.

## Features
- ASL and ARSL Gesture Recognition: The system can recognize gestures from both ASL and ARSL.
- Real-time Video Processing: The webcam captures video frames and processes them in real-time.
- Gesture Classification: Uses machine learning models to classify gestures based on hand keypoints.
- Logging and Data Collection: Gesture data and keypoint information are logged and can be used for further analysis or model training.
- FPS Display: Real-time frames per second (FPS) display for performance monitoring.

## Requirements

### Dependencies:
- Python 3.x
- OpenCV
- Mediapipe
- NumPy
- Pillow
- argparse
- CSV (standard Python library)
- Custom models: `KeyPointClassifierASL`, `KeyPointClassifierARSL`, `PointHistoryClassifier`

You can install the required dependencies using `pip`:

```bash
pip install opencv-python mediapipe numpy pillow
```

### Model Files:
The following model files are needed for gesture classification:
- `keypoint_classifier_label_asl.csv` (for ASL gestures)
- `keypoint_classifier_label_arsl.csv` (for ARSL gestures)
- `keypoint_asl.csv` (for ASL keypoints)
- `keypoint_arsl.csv` (for ARSL keypoints)
- `point_history_classifier_label.csv`
- `point_history.csv`

These files should be placed in the appropriate model directories as indicated in the code. 

## Usage

### Command-line Arguments:
The script accepts several command-line arguments for customization:
```bash
python gesture_recognition.py --device 0 --width 960 --height 540 --use_static_image_mode --min_detection_confidence 0.7 --min_tracking_confidence 0.5
```

- `--device`: Camera device index (default is 0).
- `--width`: Camera capture width (default is 960).
- `--height`: Camera capture height (default is 540).
- `--use_static_image_mode`: Use static image mode for hand detection (optional).
- `--min_detection_confidence`: Minimum confidence for detecting hands (default is 0.7).
- `--min_tracking_confidence`: Minimum confidence for tracking hands (default is 0.5).

### Switching Between ASL and ARSL Models:
Press the following keys during runtime to switch between ASL and ARSL gesture recognition:
- Press 1 to load the ASL model.
- Press 2 to load the ARSL model.

### Gesture Recognition Process:
1. Hand Detection: The system detects hands using Mediapipe.
2. Keypoint Detection: Each detected hand's keypoints are extracted.
3. Gesture Classification: The system uses pre-trained models (`KeyPointClassifierASL` or `KeyPointClassifierARSL`) to classify the hand gestures.
4. Point History Classification: Tracks finger gestures based on previous hand positions.

### Display:
- The camera feed is mirrored and displayed in real-time with overlay information such as:
  - Hand bounding box
  - Hand sign classification label (ASL or ARSL)
  - Finger gesture classification label
  - FPS (frames per second)
  - Mode and number being logged (for dataset collection)

## Files Overview

- `gesture_recognition.py`: The main Python script for the hand gesture recognition system.
- `model/`: Contains the trained models and CSV files for classification.
- `utils.py`: Contains utility functions like `CvFpsCalc` for FPS calculation.
- `model/KeyPointClassifierASL.py`: ASL gesture classification model.
- `model/KeyPointClassifierARSL.py`: ARSL gesture classification model.
- `model/PointHistoryClassifier.py`: Model for classifying finger gestures over time.

## License
This project is licensed under the MIT License. See the LICENSE file for more details.

## Acknowledgments
- Mediapipe: For hand tracking and landmark detection.
- OpenCV: For computer vision operations.
- Pillow: For image processing and text overlay.
- Python Libraries: NumPy, CSV, and argparse.

