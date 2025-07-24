🍬 Custom YOLO Candy Detection with Google Colab
This notebook trains a custom YOLOv8/YOLOv5/YOLO11 object detection model using a candy image dataset. The workflow is fully compatible with Google Colab and ideal for training and deploying models on PCs, Raspberry Pi, or mobile devices.
✅ Key Features
Train YOLO models (v8, v5, or 11) on a custom or pre-made dataset

Use Label Studio to annotate images

Automatically splits data into train and validation folders

Easily export trained models for deployment on PC or edge devices

Supports GPU acceleration in Colab

Tested with: Ultralytics, PyTorch, Python 3.12+
🧠 Workflow Summary
1.📥 Prepare Your Dataset

Collect at least 200 labeled images of candy (variety of objects, lighting, backgrounds).

Use tools like Label Studio or grab pre-made datasets.

Follow YOLO folder structure (images/train, labels/train, etc.)

2.📁 Upload Dataset to Colab

Upload via Colab UI, Google Drive, or download from Evan’s hosted zip:

bash
Copy
Edit
!wget -O /content/data.zip https://s3.us-west-1.amazonaws.com/evanjuras.com/resources/candy_data_06JAN25.zip


3.🗂️ Split Dataset

Automatically divides into training and validation sets using:

bash
Copy
Edit
!python train_val_split.py --datapath="/content/custom_data" --train_pct=0.9


4.⚙️ Configure Training

Auto-generate data.yaml config file from classes.txt

5.🚀 Train the Model

Example training command:

bash
Copy
Edit
!yolo detect train data=/content/data.yaml model=yolo11s.pt epochs=60 imgsz=640

6.🧪 Test & Visualize

Run predictions on validation data and visualize:

bash
Copy
Edit
!yolo detect predict model=runs/detect/train/weights/best.pt source=data/validation/images save=True

7.📦 Export & Deploy

Zip trained model (my_model.pt) and download

Supports deployment on:

Windows/Linux/macOS via Anaconda + Python script

Raspberry Pi (NCNN conversion coming soon)

Mobile (via ONNX or TFLite formats)

