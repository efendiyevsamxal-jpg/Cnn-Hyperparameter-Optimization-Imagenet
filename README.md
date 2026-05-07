CNN Optimization with Optuna: ImageNet Lite Classification

1. Project Overview
This project demonstrates an end-to-end Computer Vision pipeline for binary image classification.
The core highlight is the use of Optuna, an automated hyperparameter tuning framework,
to find the most efficient Convolutional Neural Network (CNN) architecture and training parameters.
The model is trained on a localized version of the ImageNet dataset to classify images with high precision by optimizing filters,
kernel sizes, dropout rates, and learning rates.

2. Technical Stack
Deep Learning Framework: TensorFlow, Keras

Hyperparameter Optimization: Optuna

Automated Tuning Sampler: TPESampler (Tree-structured Parzen Estimator)

Data Processing: NumPy, Pandas

Image Augmentation: ImageDataGenerator

Metrics: AUC (Area Under Curve), Binary Crossentropy

Bu kodlar əsasında hazırladığım README faylı layihənin həm texniki mürəkkəbliyini, həm də Optuna ilə həyata keçirdiyin hiperparametr optimallaşdırılması üstünlüyünü ön plana çıxarır.

GitHub üçün tam hazır mətn:

🧠 CNN Optimization with Optuna: ImageNet Lite Classification
1. Project Overview
This project demonstrates an end-to-end Computer Vision pipeline for binary image classification. The core highlight is the use of Optuna, an automated hyperparameter tuning framework, to find the most efficient Convolutional Neural Network (CNN) architecture and training parameters.

The model is trained on a localized version of the ImageNet dataset to classify images with high precision by optimizing filters, kernel sizes, dropout rates, and learning rates.

2. Technical Stack
Deep Learning Framework: TensorFlow, Keras

Hyperparameter Optimization: Optuna

Automated Tuning Sampler: TPESampler (Tree-structured Parzen Estimator)

Data Processing: NumPy, Pandas

Image Augmentation: ImageDataGenerator

Metrics: AUC (Area Under Curve), Binary Crossentropy

3. Data Augmentation & Preprocessing
To improve the model's ability to generalize and prevent overfitting, a robust Image Augmentation strategy was implemented:

Rescaling: Pixel normalization (1/255).

Shear & Zoom Transformations: To simulate different viewing angles.

Horizontal Flips: To ensure the model recognizes objects regardless of orientation.

Target Size: Images are resized to 64x64 pixels to balance detail and computational speed.

4. Automated Hyperparameter Tuning (Optuna)
Instead of manual trial-and-error, the project uses a create_model objective function to search for the best:

CNN Architecture: Number of filters (16-64), kernel sizes (2-5), and pool sizes.

Regularization: SpatialDropout2D for convolutional layers and standard Dropout for dense layers (0.1 - 0.5 range).

Optimization: Selection between Adam, SGD, RMSprop, and Adagrad.

Learning Rate: Log-scale search from 1e-5 to 1e-2.

5. Final Model Architecture
The optimized final model (create_final_model) consists of:

Conv2D Layers: Optimized filters and ReLU activation.

MaxPooling2D: Downsampling features.

SpatialDropout2D: Reducing spatial redundancy.

Flatten: Transitioning from 2D features to 1D vectors.

Dense Layers: Fully connected layers with tuned units.

Sigmoid Output: Producing binary classification probabilities.

6. Training & Evaluation
The final model is trained for 20 epochs using the best parameters found during the Optuna study. Performance is measured using the AUC score, providing a reliable metric for binary classification quality.

Train AUC: Measured on the augmented training set.

Test AUC: Validated on unseen test data.

7. Inference & Single Prediction Visualization
The project includes a custom inference pipeline that:

Extracts test images from ZIP files.

Preprocesses individual images for the model.

Visual Prediction Table: Uses HTML/Base64 encoding to display the actual images directly alongside the model's predictions in a clean, formatted table.

8. Key Results
Efficiency: Automated tuning reduced the manual effort for architecture design.

Generalization: Strategic dropout and augmentation ensured a minimal gap between training and test AUC.

Scalability: The pipeline can be easily adapted to multi-class problems or larger datasets.
