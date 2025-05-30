# Weapon Detection using YOLOv8

A deep learning project for detecting weapons in images and video using YOLOv8.

## Project Overview

This project uses YOLOv8 to train a weapon detection model based on the [Weapon Detection Dataset v2](https://universe.roboflow.com/joao-assalim-xmovq/weapon-2/dataset/2) from Roboflow. It can detect various types of weapons including knives, pistols, and rifles in images and video streams.

## Model Performance

The trained YOLOv8s model achieves:
- Precision: ~0.85
- Recall: ~0.83
- mAP50: ~0.89
- mAP50-95: ~0.65

## Installation

`ash
# Clone the repository
git clone https://github.com/yourusername/weapon-detection-yolov8.git
cd weapon-detection-yolov8

# Install dependencies
pip install -r requirements.txt
`

## Usage

### Training a Model
`python
from ultralytics import YOLO

# Load a pre-trained YOLOv8 model
model = YOLO('yolov8s.pt')

# Train the model on your dataset
model.train(
    data='path/to/data.yaml',
    epochs=50,
    batch=16,
    imgsz=640,
    project='weapon_detection',
    name='yolov8s_weapon_detection'
)
`

### Inference with a Trained Model
`python
from ultralytics import YOLO

# Load trained model (replace with path to your best.pt)
model = YOLO('path/to/best.pt')

# Run inference on an image
results = model('path/to/image.jpg')

# Process results
for r in results:
    print(f'Detections: {r.boxes.shape[0]}')
    print(f'Classes: {r.boxes.cls.tolist()}')
`

## Dataset

The model is trained on the [Weapon Detection Dataset v2](https://universe.roboflow.com/joao-assalim-xmovq/weapon-2/dataset/2), which contains annotated images of various weapons.

## Files in this Repository

- yolo_train.ipynb: Jupyter notebook for training the YOLOv8 model
- equirements.txt: List of required Python packages
- model/best.pt: The trained model weights (not included in repo - download separately)

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [Ultralytics](https://github.com/ultralytics/ultralytics) for YOLOv8
- [Roboflow](https://roboflow.com/) for the dataset

