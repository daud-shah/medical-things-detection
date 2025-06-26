# 🏥 AI Surgical Instrument Detection System  
![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-1.22+-orange)
![YOLO](https://img.shields.io/badge/YOLO-Ultralytics-red)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5+-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

A real-time surgical instrument detection system that identifies 33 medical tools in operating room videos to assist in inventory management and procedural documentation.

## 🌟 Features
- **33-class instrument detection** using YOLOv11 (Coveralls, Hemostats, Mayo scissors, etc.)
- **Frame-by-frame analysis** with 150-600ms processing time
- **Visual annotation** of detected instruments
- **Video processing pipeline** with OpenCV
- **Performance metrics display** (FPS, detection counts)
- **GPU acceleration support** for faster inference

## 🛠️ Installation
1. Clone the repository:
```bash
git clone https://github.com/yourusername/medical-things-detection.git
cd medical-things-detection
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Download model weights:
- Place `best.pt` in project root
- *(or train your own model with custom data)*

## 🚀 Usage
### Video Processing
```python
python process_video.py \
  --input m1.mp4 \
  --output output.mp4 \
  --conf 0.5  # Confidence threshold
```

### Key Features:
```python
# Customizable detection
results = model(frame, conf=0.5, imgsz=640)  

# Real-time visualization
annotated_frame = results[0].plot()  
```

## 📂 Project Structure
```
medical-things-detection/
├── best.pt                # Pretrained YOLOv8 model
├── model-testing.ipynb    # Jupyter notebook for development
├── process_video.py       # Main processing script
├── medical-things-test-video/
│   └── m1.mp4            # Sample surgical video
├── outputs/              # Processed video outputs
├── utils/                # Helper functions
├── requirements.txt      # Dependencies
└── README.md
```

## 📋 Requirements
```python
# requirements.txt
ultralytics==8.0.0
opencv-python==4.5.5.64
numpy==1.23.5
torch==1.12.1
```

## 🧠 How It Works
1. **Frame Capture**:  
   - OpenCV reads video frames (640x384 resolution)
   
2. **YOLOv11 Inference**:  
   - Detects instruments with class-specific confidence scores

3. **Visualization**:  
   ```python
   # Example detection output:
   0: 640x384 1 Hemostat, 2 Mayos, 204.4ms
   Speed: 3.8ms preprocess, 204.4ms inference, 1.0ms postprocess
   ```

4. **Output Generation**:  
   - Saves annotated video with bounding boxes

## 📈 Future Improvements
- [ ] Integration with surgical recording systems
- [ ] Instrument usage analytics dashboard
- [ ] Sterilization compliance tracking
- [ ] 3D spatial mapping of tools
- [ ] Multi-camera OR integration

## 🤝 Contributing
1. Fork the repository  
2. Create your feature branch (`git checkout -b feature/NewInstrument`)  
3. Commit your changes (`git commit -m 'Add new instrument class'`)  
4. Push to the branch (`git push origin feature/NewInstrument`)  
5. Open a Pull Request  

## 📜 License
Distributed under the MIT License. See `LICENSE` for more information.

---
