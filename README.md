Real-Time Face Recognition and Face Locking System

A real-time face recognition and tracking system capable of identifying multiple individuals, locking onto a selected person, and continuously monitoring facial actions. The system combines high-accuracy face recognition with facial landmark tracking and automated action logging. It is suitable for surveillance, attendance systems, behavioral analysis, and research applications.

FEATURES

Face Recognition

Real-time face detection and identification

Multi-face support

High-accuracy ArcFace embeddings

Optimized for CPU-based real-time processing

Face Locking and Tracking

Lock onto a specific recognized individual during runtime

Persistent tracking even when other faces appear

Automatic re-acquisition if the face is briefly lost

Visual indicator for the locked face

Action and Expression Detection

Head movement detection (left and right)

Smile detection using facial landmark ratios

System event detection (lock, unlock, lost, regained)

Automatic timestamped logging of all actions

PROJECT STRUCTURE

.
├── models/
│ ├── embedder_arcface.onnx
│ └── face_landmarker.task
├── logs/
├── src/
│ ├── enroll.py
│ ├── recognize.py
│ ├── evaluate.py
│ ├── embed.py
│ └── haar_5pt.py
├── requirements.txt
└── README.txt

INSTALLATION

Prerequisites

Python 3.8 or higher

Webcam or camera device

Install Dependencies

pip install -r requirements.txt

Model Setup

Ensure the following files are placed in the models directory:

embedder_arcface.onnx (ArcFace recognition model)

face_landmarker.task (MediaPipe FaceMesh landmark model)

USAGE

Face Enrollment

Capture and register face samples for new identities.

Command:
python -m src.enroll

Controls:

SPACE : Capture a single face sample

a : Toggle automatic capture

s : Save enrollment data

q : Quit enrollment

Real-Time Recognition and Face Locking

Run live face recognition with tracking and action logging.

Command:
python -m src.recognize

Controls:

/ - : Adjust recognition distance threshold

r : Reload face database

d : Toggle debug overlay

l : Lock or unlock the currently recognized face

q : Quit

FACE LOCKING SYSTEM

Lock Activation

Press 'l' when a recognized face is visible

The closest recognized face is locked

A visual border indicates the locked individual

Tracking Behavior

The locked face remains tracked while visible

If the face is lost, re-acquisition is attempted for 2 seconds

The lock is automatically released if re-acquisition fails

DETECTED ACTIONS

Head Movement

Detects left and right head rotation

Based on horizontal landmark displacement

Default movement threshold: 10 pixels (configurable)

Facial Expression

Smile detection using mouth landmark ratios

Default smile threshold: ratio greater than 1.1

System Events

Face locked

Face unlocked

Face lost

Face re-acquired

LOGGING SYSTEM

Log Files

All logs are saved in the logs directory

A new log file is created for each recognition session

Filename Format
[Name]history[timestamp].txt

Example
Bahati_history_20260131132049.txt

Log Entry Format
[YYYY-MM-DD HH:MM:SS.microseconds] - ACTION_TYPE: Description

Example Log Entries
2026-01-31 13:20:11.324267 - FACE_LOCKED: Face locked: Bahati
2026-01-31 13:20:20.225528 - HEAD_RIGHT: Moved right by 31.9px
2026-01-31 13:20:21.684933 - SMILE: Smile detected (ratio: 1.47)

EVALUATION

Evaluate recognition accuracy and determine the optimal distance threshold.

Command:
python -m src.evaluate

VISUALIZATION AND DEBUG TOOLS

python -m src.embed
Visualizes face embeddings

python -m src.haar_5pt
Displays face detection and landmark tracking

TECHNICAL OVERVIEW

Face Recognition Model: ArcFace (ONNX)

Landmark Tracking: MediaPipe FaceMesh (5-point tracking)

Tracking Method: Bounding box and landmark continuity

Performance: Real-time, CPU-optimized

Logging: Automatic session-based event history

USE CASES

Attendance and identity verification

Surveillance and access control

Behavioral and motion analysis

Academic and research projects

Human-computer interaction systems

LICENSE

This project is intended for educational and research purposes.
Add a license file if distribution or commercialization is planned.
