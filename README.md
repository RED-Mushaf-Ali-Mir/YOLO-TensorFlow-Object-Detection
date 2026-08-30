# YOLO Object Detection — Autonomous Driving Car Detection

An implementation of the YOLO ("You Only Look Once") object detection pipeline, applied to a self-driving car camera dataset. The pipeline filters raw model predictions by class-score threshold, computes Intersection over Union (IoU), and applies Non-Max Suppression (NMS) to produce clean, non-overlapping bounding boxes on real driving images.

## What it does

- Filters candidate boxes from YOLO's raw output using a class-confidence threshold
- Computes IoU between bounding boxes
- Runs Non-Max Suppression to remove duplicate/overlapping detections
- Loads a pre-trained YOLO model and runs end-to-end inference on images, drawing labeled bounding boxes

## Repo structure

```
YOLO-Object-Detection/
│
├── notebook/
│   └── YOLO_Object_Detection.ipynb   # Full implementation + walkthrough
│
├── demo/
│   └── yolo_detection_demo.mp4       # Short demo of detections on sample frames
│
├── README.md
└── requirements.txt
```

## Setup

```bash
pip install -r requirements.txt
```

You'll also need:
- **YOLO utility functions** (`yad2k` module) — used for reading anchors/classes, drawing boxes, and preprocessing images. See [YAD2K by Allan Zelener](https://github.com/allanzelener/YAD2K).
- **Pre-trained YOLO weights** (`model_data/`) — not included in this repo due to file size. Point the notebook's `load_model(...)` call at your local copy.

## Notes

This project was built while working through the Convolutional Neural Networks course of DeepLearning.AI's Deep Learning Specialization (Andrew Ng). The core YOLO filtering/NMS logic in the notebook is my own implementation, written to satisfy the algorithm described in the papers below — full credit for the underlying model, architecture, and dataset goes to their original authors.

## Credits & References

- Joseph Redmon, Santosh Divvala, Ross Girshick, Ali Farhadi — [You Only Look Once: Unified, Real-Time Object Detection](https://arxiv.org/abs/1506.02640) (2015)
- Joseph Redmon, Ali Farhadi — [YOLO9000: Better, Faster, Stronger](https://arxiv.org/abs/1612.08242) (2016)
- Allan Zelener — [YAD2K: Yet Another Darknet 2 Keras](https://github.com/allanzelener/YAD2K)
- The official YOLO website: https://pjreddie.com/darknet/yolo/
- Car-detection dataset: [The Drive.ai Sample Dataset](https://www.drive.ai/), licensed under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/). Thanks to Brody Huval, Chih Hu, and Rahul Patel for providing this data.
