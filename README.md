# Blind Assistive Robot — Object Detection and Audio Feedback

A Python-based assistive system that detects objects in real time using YOLOv3,
retrieves contextual descriptions via the Wikipedia API, and communicates findings
through text-to-speech audio output and Arduino-controlled servo movement.

This project was built as part of an undergraduate AI degree at SZABIST. The full
system runs on a laptop connected to a physical mannequin fitted with Arduino-controlled
servo motors and a Bluetooth speaker. The mannequin nods when an object is detected
and the system speaks a Wikipedia-sourced description aloud.

## System architecture
- **Object detection** — YOLOv3 (pre-trained on COCO) via OpenCV DNN
- **Knowledge retrieval** — Wikipedia API (2-sentence summaries per detected object)
- **Audio output** — pyttsx3 text-to-speech to Bluetooth speaker
- **Physical feedback** — Serial commands to Arduino for servo motor control

## Hardware requirements (physical demo only)
- Arduino board with servo motors
- Bluetooth speaker
- Webcam

## Running without hardware
The detection, Wikipedia lookup, and text-to-speech components run independently
of the Arduino. To test the software pipeline without hardware, set:

ARDUINO_PORT = None

in `assistant.py`. The system will skip serial connection and still detect objects,
fetch descriptions, and produce audio output.

## Requirements
pip install opencv-python numpy pyttsx3 pyserial wikipedia

YOLOv3 weights and config files are required separately:
- yolov3.weights — https://pjreddie.com/media/files/yolov3.weights
- yolov3.cfg — https://github.com/pjreddie/darknet/blob/master/cfg/yolov3.cfg
- coco.names — https://github.com/pjreddie/darknet/blob/master/data/coco.names

## Usage
python assistant.py
