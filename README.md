# 🚗 Traffic Violation Detection using YOLOv11  

## 📌 Overview  
This project uses **YOLOv11** to detect various **traffic violations**, such as **riding without a helmet, triple riding, using mobile while driving, and different vehicle types (car, bus, truck, motorcycle, auto-rickshaw, etc.).**  
The model is trained on a **custom dataset** and evaluated for **mAP@50, Precision, Recall, and F1 Score**.  

---

## 📂 Dataset  
- **Dataset Name:** Traffic Violation Detection  
- **Source:** Roboflow  
- **Total Images:** 751 (Train: 80%, Validation: 10%, Test: 10%)  
- **Classes:**  
  - Auto Rikshaw  
  - Bus  
  - Car  
  - Helmet  
  - Motorcycle  
  - No Helmet  
  - Rider  
  - Triple Riding  
  - Truck  
  - Using Mobile  

---

## 🚀 Installation & Setup  
### **1️⃣ Install Dependencies**
```bash
pip install ultralytics roboflow matplotlib seaborn numpy

2️⃣ Download Dataset
python
Copy
Edit
from roboflow import Roboflow

rf = Roboflow(api_key="YOUR_API_KEY")  # Replace with your API key
project = rf.workspace("major-project-nlqt0").project("traffic-violation-8voto")
version = project.version(8)
dataset = version.download("yolov11", location="/content/Traffic-violation-8")

📁 YOLOv11-Traffic-Violation-Detection/
├── 📁 dataset/                     # Dataset folder (contains images & labels)
│   ├── 📁 train/                    # Training images & labels
│   ├── 📁 valid/                    # Validation images & labels
│   ├── 📁 test/                     # Test images & labels
│   ├── 📄 data.yaml                  # YOLO dataset configuration file
│
├── 📁 runs/                        # YOLOv11 training runs
│   ├── 📁 detect/                   # Detection results (inference outputs)
│   ├── 📁 train/

3️⃣ Train YOLOv11 Model
python
Copy
Edit
from ultralytics import YOLO

model = YOLO("yolo11n.pt")  # Using nano version
results = model.train(
    data="/content/Traffic-violation-8/data.yaml",
    epochs=50,
    batch=8,
    device="cpu"
)
📊 Model Performance
Metric	Value
mAP@50	0.5493
mAP@50-95	0.4454
Precision	0.8987
Recall	0.4810
F1 Score	0.6266
