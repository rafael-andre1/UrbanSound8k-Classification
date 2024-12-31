## UrbanSound8k Classification

This project, developed for **Computer Learning II**, focuses on audio preprocessing and classification of the **UrbanSound8k** dataset, using different deep learning models.

This dataset contains 8732 labeled audio recordings, each up to four seconds long, categorized into the following classes:

| Label              | Class ID |
|--------------------|----------|
| air conditioner    | 0        |
| car horn           | 1        |
| children playing   | 2        |
| dog bark           | 3        |
| drilling           | 4        |
| engine idling      | 5        |
| gun shot           | 6        |
| jackhammer         | 7        |
| siren              | 8        |
| street music       | 9        |

The work involves designing, training, and evaluating two deep learning classifiers:
- **Convolutional Neural Network (CNN)**
- **Recurrent Neural Network (RNN)**

Additionally, we assess the models' robustness against adversarial attacks using the **DeepFool** algorithm.

\
Project developed by:

 - **Eduardo Passos**
 - **Pedro Fernandes**
 - **Rafael Pacheco**
 
For development and results review: **`report.ipynb`**

\
**Thank you for exploring this project! You can find the original repository [here](https://github.com/pmgfernandes04/Urban-Sounds-Classification.git)! 🚀**



## Solutions Implemented
- **Convolutional Neural Network (CNN)**
- **Recurrent Neural Network (RNN) with LSTM units**



## Project Development Phases
### 1. **Data Preprocessing and Feature Extraction**
- **Data Preprocessing**: Includes zero-padding, resampling (22050Hz and 44100Hz), and MinMax scaling.
- **Feature Extraction**:
  - Mel-scaled spectrograms (2D arrays)
  - Chromagrams (2D arrays)
  - Spectral flatness, bandwidth, roll-off, centroid (1D arrays)
  - Log Mel-Scaled Spectrograms (for RNN)

### 2. **Model Development**
#### **Convolutional Neural Network (CNN)**
- **Architecture**:
  - Parallel processing of 1D and 2D features.
  - Leveraged convolutional and pooling layers to extract hierarchical features.
- **Performance Assessment**:
  - Cross-validation with confusion matrix analysis.
  - Achieved a training accuracy of 90.97% but validation accuracy of 69.27%, indicating potential overfitting.
  - Suggested improvements: Attention mechanisms and advanced data augmentation techniques.

#### **Recurrent Neural Network (RNN)**
- **Architecture**:
  - Utilized LSTM units for sequential pattern recognition.
  - Designed to identify time-dependent characteristics of urban sounds.
- **Performance Assessment**:
  - Cross-validation results showed a significant gap between training (70.04%) and validation accuracy (51.90%), highlighting overfitting challenges.
  - Suggested optimizations: Simpler architectures and increased dropout rates.

### 3. **Robustness Evaluation with DeepFool**
- **DeepFool Algorithm**:
  - Evaluates model vulnerability to adversarial examples by computing the smallest perturbation needed to misclassify inputs.
  - Applied to spectrogram representations of audio data.
- **Insights**:
  - The algorithm highlighted outliers and areas where decision boundaries were fragile.
  - Computational limitations prevented full implementation for the RNN.



## Results Summary
### CNN Results:
- **Training Accuracy**: 90.97% ± 1.38%
- **Validation Accuracy**: 69.27% ± 3.10%
- **Test Accuracy**: 66.27% ± 4.11%
- **Strengths**:
  - High accuracy for distinct sound classes like `gun_shot` and `dog_bark`.
- **Weaknesses**:
  - Struggled with acoustically similar classes like `engine_idling` and `air_conditioner`.

### RNN Results:
- **Training Accuracy**: 70.04% ± 2.52%
- **Validation Accuracy**: 51.90% ± 3.22%
- **Test Accuracy**: 49.01% ± 3.63%
- **Strengths**:
  - Captured time-dependent features well for some classes.
- **Weaknesses**:
  - Large gap between training and validation accuracy indicated overfitting.

### DeepFool Insights:
- Revealed vulnerabilities in decision boundaries for both models.
- Identified outliers affecting classification robustness.


## Conclusion
This project showcased the challenges and potential of applying deep learning models to urban sound classification. While the CNN model demonstrated better performance than the RNN, both struggled with acoustically similar classes and overfitting issues. The DeepFool algorithm provided valuable insights into model vulnerabilities and robustness. Future improvements could include:
- Advanced regularization techniques.
- Incorporation of attention mechanisms.
- More robust data augmentation strategies.
