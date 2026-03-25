# Smart Headlight System: YOLOv8 Object Detection

![YOLOv8](https://img.shields.io/badge/YOLOv8-00FFFF?style=for-the-badge&logo=yolo&logoColor=black)
![Roboflow](https://img.shields.io/badge/Roboflow-6706CE?style=for-the-badge)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-FF9900?style=for-the-badge)

This repository contains the machine learning pipeline for a smart headlight system. It leverages computer vision to detect relevant environmental features (like oncoming vehicles or pedestrians) and dynamically adjust lighting.

## 🚀 Technical Highlights

* **Custom Dataset Generation:** Image dataset built, curated, and fully annotated using **Roboflow** to ensure high-quality bounding boxes and class definitions.
* **Model Architecture:** Utilizes the state-of-the-art **YOLOv8** framework for fast, real-time object detection.
* **Comparative Model Training:** Features training configurations and evaluation pipelines for both **YOLOv8 small** and **YOLOv8 medium** models to analyze the trade-offs between inference speed and detection accuracy.

## ⚙️ How It Works

1. **Data Preparation:** Images are processed and exported via Roboflow in the standard YOLO format.
2. **Training Phase:** The annotated dataset is passed through the training pipeline to optimize the YOLOv8 small and medium models. 
3. **Evaluation:** The models are evaluated on a test set to validate their precision, recall, and mean Average Precision (mAP) for intelligent headlight control.

## 📊 Results & Discussion

The YOLOv8 medium (YOLOv8m) architecture demonstrated robust feature extraction and localization capabilities, achieving a mean Average Precision (mAP@0.5) of 0.78 for vehicle detection across local driving scenarios. When evaluated against the custom-annotated Roboflow dataset, the model showed a strong balance between precision and recall. This 0.78 mAP score indicates a high level of reliability in correctly bounding oncoming vehicles.

**Comparative Analysis: Accuracy vs. Efficiency**

The performance of the YOLOv8m model highlights a distinct trade-off when compared to the lighter YOLOv8 small (YOLOv8s) variant. While the medium model possesses a deeper neural network that captures more complex spatial hierarchies—resulting in the strong 0.78 mAP score—it inherently requires more computational overhead. However, the increased parameter count in the YOLOv8m model proved highly beneficial for detecting vehicles at further distances and in challenging local conditions, such as varying street elevations or partial occlusions from roadside infrastructure.

**Application in Smart Headlight Systems**

For the specific application of dynamic headlight control, the 0.78 mAP achieved by YOLOv8m is highly promising. The model successfully recognized vehicles consistently enough to theoretically trigger timely headlight dimming, reducing glare for oncoming drivers. The primary challenge moving forward is balancing this high detection accuracy with the strict latency requirements of edge hardware. Because a vehicle traveling at local speed limits requires near-instantaneous lighting adjustments, future iterations of this project will need to evaluate if the inference speed (Frames Per Second) of the medium model on embedded automotive hardware remains fast enough, or if the slight accuracy drop of the YOLOv8s model is a necessary compromise for real-time safety.

## 💻 Usage

To run the training or inference scripts locally:
1. Clone the repository.
2. Install the required dependencies (e.g., `ultralytics`).
3. Run the inference script on a test video or image stream.
