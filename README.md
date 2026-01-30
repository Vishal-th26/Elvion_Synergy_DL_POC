ARGUS
AI-Driven Flood Detection & Priority-Based Disaster Response (POC)

ARGUS is an AI-powered backend system for flood detection and disaster response planning.
It uses satellite SAR imagery + deep learning to identify flooded regions and lays the foundation for priority-based resource allocation during disasters.

⚠️ Note: This repository contains a Proof of Concept (POC) model built under hackathon constraints.
The focus is on system feasibility, architecture, and extensibility, not final production accuracy.

🚨 Problem Statement

Floods cause massive damage to lives and infrastructure, yet most existing systems:

•Only provide static flood maps

•Do not help decision-makers prioritize regions

•Fail under cloud cover or extreme weather

ARGUS aims to go beyond detection by enabling:

•Reliable flood mapping from SAR data
•Backend intelligence for data-driven response prioritization

🧠 What ARGUS Does (POC Scope)

•Detects flooded regions using satellite imagery

•Generates pixel-level flood masks

•Produces structured outputs for downstream decision layers

•Demonstrates feasibility of AI-assisted disaster response systems

🏗️ System Architecture (POC)
Sentinel-1 SAR Images (VV, VH)

        ↓
        

Preprocessing & Normalization

        ↓

CNN-based Semantic Segmentation (U-Net)
        
        ↓

Flood Mask Prediction (POC)
        
        ↓

Flood Severity Estimation 
        
        ↓

(Planned) Priority Scoring & Resource Allocation


The system is modular, allowing future upgrades without redesigning the pipeline.

📊 Data Used
Dataset

•ECTI 2021 Flood Detection Dataset

•Satellite source: Sentinel-1 SAR

•Tile size: 192 × 192

Why SAR?

•Works day & night

•Penetrates clouds and rain

•Reliable during extreme weather events

Input Channels

•VV polarization

•VH polarization

•Derived VV/VH ratio (pseudo-RGB)

⚙️ Preprocessing Pipeline

•Intensity normalization to [0, 1]

•Conversion of SAR bands into 3-channel input

•Resizing to fixed resolution

•Optional data augmentation (flip, resize)

🧩 Model Details (POC)
Architecture

•Model: U-Net (Semantic Segmentation)

•Encoder: ResNet-34

•Pretraining: ImageNet (transfer learning)

•Framework: PyTorch

Why U-Net?

•Designed for pixel-level tasks

•Efficient on limited data

•Proven in medical & satellite imaging

🏋️ Training Strategy (POC)

•Transfer learning enabled

•Limited epochs due to compute & time constraints

•Dataset undersampling for faster iteration

•Loss function: Cross-Entropy Loss

•Mixed precision training (AMP)

The model is intentionally lightweight and serves as a functional demonstration, not a final trained system.

📤 Output

Binary flood segmentation mask:

•Flooded vs Non-Flooded pixels

•Outputs are designed to feed into:

•Severity estimation

Priority scoring modules (future work)

🖼️ Visual Results

Sample outputs include:

•SAR input images

•Predicted flood masks

•Water body vs flood differentiation

📁 Visuals & demo outputs are provided via Drive (linked in PPT / submission).

🚧 Limitations (POC)

Trained on limited data

No multi-temporal modeling yet

No population or infrastructure data integration

Accuracy not optimized for production

These are engineering constraints, not conceptual limitations.

🔮 Future Roadmap
Phase 1 – Model Improvements

Full dataset training

Better class imbalance handling

Ensemble models (SAR + Optical)

Phase 2 – Decision Intelligence

Population density integration

Infrastructure & critical asset mapping

Flood severity indexing

Phase 3 – Priority Scoring Engine
Priority Score =
  Flood Severity
+ Population Exposure
+ Infrastructure Risk

Phase 4 – Deployment

Backend APIs

Dashboard for authorities

Real-time inference support

🧪 Status

✅ Core ML pipeline implemented

✅ End-to-end flood segmentation working

✅ Visual proof available

🚧 Priority scoring & deployment planned

🧰 Tech Stack

Language: Python

Deep Learning: PyTorch

Models: U-Net, ResNet-34

Data Processing: NumPy, OpenCV

Augmentation: Albumentations

Visualization: Matplotlib

Hardware: GPU (CUDA)

📌 Disclaimer

This repository represents a Proof of Concept developed for idea evaluation and system validation.
The architecture is designed for scalability, retraining, and real-world deployment beyond the hackathon.
