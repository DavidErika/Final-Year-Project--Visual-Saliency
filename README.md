# Understanding Human Visual Attention: A Statistical Comparison of Deep Learning-Based Saliency Models Across Diverse Scene Complexities
## 📌 Overview
This project explores how state-of-the-art deep learning-based saliency models simulate human visual attention across images with varying levels of scene complexity. By evaluating the predictive performance of **DeepGaze II E, SALICON, and SUM (Saliency Unification through Mamba)**, the study investigates how model architecture, input modality (eye-tracking vs. mouse-tracking), and scene complexity influence saliency prediction accuracy.

The project uses the **MIT1003** dataset, applies standard saliency evaluation metrics, and introduces a custom scene complexity scoring method. This work provides insights into the strengths and limitations of current saliency modelling approaches and lays out directions for building more robust, human-like attention models.

## 🎯 Project Goals
- Evaluate saliency prediction performance across diverse visual stimuli.

- Compare the influence of input modality and model design on attention prediction.

- Analyze the impact of scene complexity on model accuracy.

- Recommend design considerations for future saliency models.

## 🧠 Saliency Models Evaluated
1 **DeepGaze II E** 
- Eye-tracking only.
- Probabilistic readout with pretrained CNNs (e.g., DenseNet, ResNext).

2 **SUM (Mamba)**
- Eye + Mouse Tracking.
- 	Hybrid Conditional U-Net + C-VSS module

3 **SALICON**
- Mouse-tracking only.
- Multi-resolution CNN inspired by peripheral vision.

## 📊 Evaluation Metrics
-**AUC-Judd** – Measures discriminability of fixated vs. non-fixated points.

-**NSS (Normalized Scanpath Saliency)** – Measures how well predicted saliency aligns with actual fixation points.

-**CC (Pearson's Correlation Coefficient)** – Quantifies the spatial similarity between predicted and true fixation maps.

## 🖼️ Scene Complexity Analysis
A custom Scene Complexity Score was calculated using:

- **Edge Density** (via Canny detector)

- **Colour Variation** (RGB standard deviation)

This score was used to categorize scenes into low and high complexity, aiding in stratified model performance evaluation.

## 🧪 Methodology Summary
- **Dataset**: Images from MIT1003 with ground truth eye-tracking data.

- **Model Pipelines**:

DeepGaze II E: Used **deepgaze_pytorch** package for saliency map inference.

SUM: Inference via **inference.py** with domain-specific conditions.

SALICON: Inference via legacy **OpenSALICON** (Caffe-based).

- **Evaluation**: Model predictions compared to ground truth fixations using AUC, NSS, and CC metrics.

- **Complexity Split**: Images were binned into low/high complexity groups to analyze performance variation.

## 📈 Key Findings
- **SUM** had the highest performance in low-complexity scenes across all metrics.

- **DeepGaze II E** showed the most consistent performance across both low and high complexity images.

- **SALICON** struggled in high-complexity scenes due to lower spatial precision from mouse-tracking data.

- Scene complexity significantly influences saliency prediction accuracy.

## 🚀 Future Work
- Incorporate statistical significance testing (e.g., ANOVA).

- Explore transformer-based or diffusion-based saliency models.

- Expand to multi-dataset evaluations (e.g., CAT2000, SALICON).

- Investigate task-specific or personalized saliency modelling.

- Leverage scalable eye-tracking methods like webcam-based GazeCapture.

## 📦 Setup & Installation
- Python 3.8+

- PyTorch

- SciPy, NumPy, scikit-learn, matplotlib

- Caffe (for SALICON only, use Docker or Colab)

### Installation
git clone https://github.com/yourusername/visual-saliency-evaluation.git
cd visual-saliency-evaluation
pip install -r requirements.txt

### 🧑‍💻 Author
David Erika Topos

BSc Computer Science

Cardiff University

LinkedIn • Email

### 📜 Acknowledgements
Thanks to my supervisor **Dr. Hantao Liu**, Cardiff University, and the open-source community behind DeepGaze, SALICON, and SUM. This project would not have been possible without access to public datasets, pretrained models, and research literature
