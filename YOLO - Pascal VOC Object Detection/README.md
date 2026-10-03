# YOLO - Pascal VOC Object Detection

A PyTorch project using a pretrained YOLO model for object detection on the Pascal VOC dataset. The model identifies objects in an image, predicts their classes, and places bounding boxes around them.

## Overview

This project applies YOLO to a multi-class object detection problem using the Pascal VOC dataset.

Unlike image classification, the model has to determine both what objects are present and where they are located. The notebook covers dataset preparation, transfer learning, model training, validation, class-wise evaluation, sample predictions, confidence analysis, and ONNX export.

## Dataset

The project uses the Pascal VOC dataset with 20 object categories:

- aeroplane
- bicycle
- bird
- boat
- bottle
- bus
- car
- cat
- chair
- cow
- diningtable
- dog
- horse
- motorbike
- person
- pottedplant
- sheep
- sofa
- train
- tvmonitor

The Ultralytics VOC configuration was used to download the dataset and prepare the annotations for YOLO training.

The training split contains 16,551 images and the evaluation split contains 4,952 images.

## Dataset Source

Pascal VOC Dataset

The dataset is downloaded automatically through the Ultralytics `VOC.yaml` configuration and is not included in this repository.

## Notebook Structure

1. Import Libraries and Check Runtime
2. Configure Training
3. Load the Pascal VOC Dataset
4. Inspect the Detection Dataset
5. Load the Pretrained YOLO Model
6. Train the YOLO Detector
7. Inspect Training History
8. Plot Training and Validation Metrics
9. Load the Best Checkpoint
10. Evaluate the Best Detector
11. Summarize Detection Metrics
12. Analyze Class-wise Performance
13. Select Evaluation Images
14. Run Object Detection
15. Visualize Predicted Bounding Boxes
16. Summarize Sample Detections
17. Inspect Detection Confidence
18. Export the Trained Model
19. Key Findings
20. Conclusion

## Repository Contents

YOLO - Pascal VOC Object Detection/
├── YOLO_Pascal_VOC_Object_Detection.ipynb
├── README.md
└── requirements.txt

The trained weights, downloaded dataset, and ONNX export are generated during notebook execution and are not required to be stored in the repository.

## Model

The project uses the pretrained YOLO26n model from Ultralytics.

The pretrained model is fine-tuned for the 20 Pascal VOC classes. This allows the project to use transfer learning instead of training the detector entirely from scratch.

The model is trained at an image size of 640 pixels with a batch size of 16.

## Training

Training was carried out for 40 epochs on an NVIDIA Tesla T4 using CUDA.

The main settings were:

- Epochs: 40
- Image size: 640
- Batch size: 16
- Random seed: 42
- Workers: 2
- Pretrained model: YOLO26n
- Optimizer: automatically selected by Ultralytics
- Early stopping patience: 10

The best checkpoint from training was saved as `best.pt` and used for the final evaluation.

## Runtime

The notebook was executed in Google Colab using:

- Python
- PyTorch 2.11.0
- Ultralytics 8.4.165
- CUDA
- NVIDIA Tesla T4

## Evaluation Metrics

The model was evaluated using precision, recall, mAP@0.50, and mAP@0.50:0.95.

mAP@0.50 measures detection performance at an IoU threshold of 0.50, while mAP@0.50:0.95 averages performance across multiple IoU thresholds.

The notebook also checks performance for individual object classes and visualizes the predicted bounding boxes.

## Results

The 40-epoch run reached its highest logged mAP@0.50:0.95 at epoch 40.

On the evaluation set, the detector achieved:

- Precision: 82.89%
- Recall: 76.94%
- mAP@0.50: 84.47%
- mAP@0.50:0.95: 64.64%

The class-wise results varied across the 20 categories. The stronger classes included bus, car, cat, horse, train, and aeroplane, while pottedplant, chair, boat, and bottle were more difficult for the detector.

## Prediction Analysis

The notebook runs the trained model on a small set of evaluation images and displays the predicted bounding boxes together with class labels and confidence scores.

For the selected images, the detector produced 8 detections in total. The mean confidence was 84.13%, with a median confidence of 90.67%.

The notebook also plots the distribution of prediction confidence values to provide a simple view of how strongly the model scored the detected objects.

## Model Export

The trained model is exported to ONNX after evaluation.

The exported file can be used with ONNX-compatible inference tools outside the original notebook environment.

## Key Findings

The YOLO detector achieved an overall precision of 82.89% and recall of 76.94% on the evaluation set.

The mAP@0.50 score reached 84.47%, while the stricter mAP@0.50:0.95 score was 64.64%. The difference reflects the additional difficulty of maintaining accurate bounding-box localization across several IoU thresholds.

Performance was not uniform across all Pascal VOC classes. Larger and visually distinctive objects were generally detected more consistently, while smaller or less distinct categories were harder for the model.

The detector also produced reasonably confident predictions on the manually selected sample images, with a mean confidence of 84.13%.

## Conclusion

This project demonstrates a complete YOLO object detection workflow using Pascal VOC.

A pretrained YOLO26n model was fine-tuned for 20 object categories and evaluated using standard object detection metrics. After 40 epochs, the model achieved 84.47% mAP@0.50 and 64.64% mAP@0.50:0.95, along with 82.89% precision and 76.94% recall.

The project also includes class-wise analysis, visual inspection of bounding boxes, confidence analysis, and ONNX export, making it a practical example of a modern object detection pipeline.