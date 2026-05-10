
# 🌲 Forest Cover Type Prediction & Analysis
> **Deep Learning (MLP) vs. Ensemble Methods (Random Forest)**

## 💼 Business Context
The objective of this project is to automate the classification of forest cover types using 54 geological and geographical variables (Elevation, Soil Type, Distance to Hydrology, etc.). High-accuracy classification is essential for ecological research, forest management, and resource allocation.

**Outcome:** I successfully engineered a solution that pushed predictive accuracy from a baseline stall of **92% to a robust 94.05% (MLP) and 95.8% (Random Forest).**

---

## ⚙️ 1. Analysis Workflow
I followed a structured data science lifecycle to overcome data noise and extreme class imbalance.

### I. Data Preprocessing
* **Standardization:** Applied `StandardScaler` to ensure features like Elevation (meters) and Slope (degrees) don't overpower smaller-scale binary variables.
* **Validation Strategy:** Implemented a three-way split (Train/Val/Test) to ensure the model generalizes to unseen data.

### II. Neural Network (MLP) Engineering
To break the 92% "performance wall," I integrated the following:
* **Dynamic Learning:** Used `ReduceLROnPlateau` to shrink the learning rate once progress slowed (creating the "kink" in the learning curve).
* **Regularization:** Utilized `BatchNormalization` and `Dropout` (0.3) to prevent overfitting.
* **Weighting:** Applied `balanced` class weights to force the model to learn rare classes like Class 3, which was 100x smaller than the majority class.

### III. Ensemble Benchmarking
I compared the Neural Network against a **Random Forest Classifier** to determine the most efficient model for tabular data structures.

---

## 📊 2. Results & Discussion

### Performance Comparison
| Metric | Multi-Layer Perceptron | Random Forest |
| :--- | :---: | :---: |
| **Accuracy** | 94.05% | **95.82%** |
| **Macro F1-Score** | 0.91 | **0.93** |
| **Computational Effort**| High (GPU Required) | Low (CPU Efficient) |

### Key Findings
1.  **The "Kink" Effect:** The MLP stalled at 92% until the learning rate was reduced. This forced the model into "fine-tuning" mode, allowing it to drop into a deeper global minimum.
2.  **Tree Supremacy:** The Random Forest outperformed the MLP because forest data is defined by "hard thresholds" (e.g., specific elevations where certain trees cannot grow). Decision trees are mathematically optimized for these sharp splits.
3.  **Class Imbalance:** By using class weights, we achieved an **81% Recall for Class 3**, ensuring that rare ecological types are not ignored in the final report.

---

## 🛠️ Tech Stack
* **Frameworks:** TensorFlow, Keras
* **Libraries:** Scikit-Learn, Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Environment:** Google Colab / Python 3.x

---

## 🚀 Future Improvements
* **Feature Engineering:** Creating interaction terms (e.g., Distance to Water * Elevation).
* **XGBoost Integration:** Testing Gradient Boosted Trees for even higher precision.

**Developed by:** [Your Name]  
**Date:** May 2026
