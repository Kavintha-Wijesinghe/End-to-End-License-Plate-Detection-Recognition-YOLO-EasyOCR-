# End-to-End-Automatic-License-Plate-Recognition-(YOLOv9-EasyOCR)-

This project detects license plates in images or videos using **YOLOv9** (You Only Look Once) and extracts the plate text using **EasyOCR**.

## 📌 Features
- **YOLO-based object detection** for robust license plate localization.
- **EasyOCR** integration to read plate text from detected regions.
- Works with **images, videos, and webcam streams**.
- Supports **GPU acceleration** (CUDA) or CPU fallback.
- Optional saving of:
  - Bounding-boxed images
  - Cropped detections
  - Detected text in `.txt` files

## 🏗 Project Structure
```
.
├── detect_with_ocr.py      # Main Python script for inference
├── Car_Number_Detection.ipynb  # Jupyter/Colab notebook for interactive usage
├── data/                   # Sample images and dataset config (if any)
├── runs/detect/            # Auto-generated folder with results
└── README.md               # This file
```

## 🛠 Requirements
Install the dependencies:

```bash
pip install torch torchvision torchaudio  # PyTorch
pip install opencv-python                 # OpenCV for image/video I/O
pip install easyocr                       # OCR engine
```

You also need the YOLO repository files (models, utils). Clone YOLOv5 repo or copy its `models/` and `utils/` folders into your project.

## 🚀 Usage

### Run on an Image or Folder
```bash
python detect_with_ocr.py --weights yolo.pt --source data/images
```

### Run on Webcam
```bash
python detect_with_ocr.py --weights yolo.pt --source 0 --view-img
```

### Key Arguments
| Argument | Description |
|---------|-------------|
| `--weights` | Path to YOLO weights (`.pt` file) |
| `--source`  | Image/video file, directory, URL, or webcam index |
| `--conf-thres` | Confidence threshold (default 0.25) |
| `--iou-thres` | NMS IoU threshold (default 0.45) |
| `--save-txt` | Save detection results in txt format |
| `--save-crop` | Save cropped detected plates |
| `--view-img` | Display results in a window |

## 🧠 How It Works
1. **YOLO detects license plates** and returns bounding boxes.
2. Each bounding box is cropped and passed to **EasyOCR**.
3. OCR output is drawn on the image and optionally saved.

## 🖼 Example Output
Detected plate with OCR text overlay:

![example](https://user-images.githubusercontent.com/example/demo_output.jpg)

## 📂 Results
Results (images/videos + labels) are saved to:
```
runs/detect/exp/
```

## 📜 License
This project is released under the MIT License. Feel free to modify and use it for your own applications.

## 🤝 Contributing
Pull requests are welcome! If you find a bug or have a feature request, open an issue.

## 🙏 Acknowledgments
- [Ultralytics YOLO](https://github.com/ultralytics/yolov5) for object detection.
- [EasyOCR](https://github.com/JaidedAI/EasyOCR) for OCR engine.
- OpenCV for visualization and video processing.
