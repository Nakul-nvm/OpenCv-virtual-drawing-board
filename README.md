# Virtual Drawing Board with OpenCV

Interactive virtual drawing board using OpenCV: detects a colored marker tip and lets you “draw” on your live webcam feed in real time.

## 📋 Features

* Real-time marker cap color detection using HSV thresholds
* Draw virtually on webcam feed by tracking marker movement
* Simple two-step system: calibrate color → draw

## 🛠 Requirements

* Python 3.x
* OpenCV: `pip install opencv-python`
* NumPy: `pip install numpy`

## 📁 Folder Structure

```
Project1_OpenCv/
├── color_detector.py   # HSV color calibrator using webcam
└── project_1.py        # Virtual drawing board using color detection
```

## 🚀 How to Use

### 1. Calibrate Your Marker Color

Run the color detector:

```bash
python color_detector.py
```

* A window with HSV sliders will open.
* Adjust the sliders until only your marker cap is highlighted in the mask.
* Note the HSV min and max values.

### 2. Update project\_1.py with HSV Values

Open `project_1.py` and find the `myColors` list:

```python
myColors = [[H_min, S_min, V_min, H_max, S_max, V_max]]
```

Replace the values with what you noted during calibration.

### 3. Run the Drawing Board

```bash
python project_1.py
```

* The webcam window will open.
* Move your marker in front of the camera and draw in the air.
* Press `q` to exit.

## 📈 How It Works

* Converts webcam frames to HSV color space
* Applies a mask using your defined HSV color range
* Finds contours of the masked area to locate the marker tip
* Draws circles at the detected tip position on every frame
* Stores all points to simulate persistent drawing

## 🔧 Configurable Variables (in project\_1.py)

```python
frameWidth = 1280
frameHeight = 960
cap.set(10, 100)  # Camera brightness

myColors = [[H_min, S_min, V_min, H_max, S_max, V_max]]
myColorValues = [[B, G, R]]  # Drawing color for each HSV range
```

## ✨ Tips

* Use a bright, solid-colored marker cap
* Run in consistent lighting for stable HSV detection
* Increase contour area threshold if marker detection is jittery

---

Enjoy drawing in the air with just your colored marker and a webcam! 🎨
