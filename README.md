# Traffic-Sign-Detection

The Traffic Sign Dataset is a comprehensive collection of road sign images designed for training and testing deep learning models in traffic sign recognition tasks. This dataset contains 39,209 RGB images of various traffic signs, making it suitable for applications such as autonomous driving, intelligent transportation systems, and road safety enhancements.

**Dataset Structure**

The dataset is organized into a hierarchical folder structure:

- The main folder contains 43 subfolders, each named from 0 to 42.
- Each subfolder corresponds to a specific traffic sign class, representing a unique road sign type.

- **1. Traffic Sign Dataset and Label Names:**

The traffic sign dataset contains images of various traffic signs categorized into multiple classes. Each image is labeled with a ClassId, which corresponds to a specific traffic sign. The dataframe containing the label names is created from labels.csv file that maps each ClassId to its descriptive label (e.g., "Speed limit (50km/h)", "Stop", "Yield"). This mapping is crucial for interpreting model predictions and evaluating the performance.

**2. Loading the Train and Test Images with Processing:**

Training and test images are loaded from designated folders. Each image undergoes preprocessing steps, including:

- Resizing: Images are resized to a standard dimension (e.g., 32x32) for consistency.

- Color Conversion: Images are converted to RGB format to ensure color consistency.

- Normalization: Pixel values are scaled to the [0, 1] range to stabilize training.

- Parallel Processing: Multiprocessing is used to expedite loading, especially with large datasets. The processed images and corresponding labels are saved as NumPy arrays for efficient reuse.

**3. Computation of Weights for Class Imbalance:**

Certain traffic sign classes have significantly more samples than others as seen from the class distribution plot. To quantify this class imbalance, the frequency of each class is computed.

Addressing class imbalance is vital because:

- Models tend to be biased toward majority classes.

- Minority classes may be underrepresented, leading to poor generalization.

- Techniques like class weighting ensure that the model pays adequate attention to underrepresented classes, improving overall robustness.

**4. Data Augmentation:**

Data augmentation artificially expands the training dataset by applying transformations such as:

Rotation, translation, and flipping

This process enhances the model's ability to generalize, making it resilient to variations in traffic sign appearances due to environmental factors like lighting or angle changes.

**5. Model Building:**

Multiple architectures were explored for this projects:

- Custom CNN Model
- VGG16 Model
- ResNet50 Model
- DenseNet

Each model was trained with the processed dataset, using appropriate loss functions and optimizers.

**6. Model Evaluation:**

Model's performance was assessed using:

- Classification Report: Provides metrics like precision, recall, and F1-score for each class, highlighting how well each traffic sign is recognized.

- Confusion Matrix: Offers a visual representation of true vs. predicted labels, revealing which classes are often misclassified.

These evaluations help identify strengths and weaknesses of the models, guiding further improvements.

**7. Result Summarization:**

Among the tested models:

- Custom CNN Model has demonstrated superior performance, particularly in recognizing minority classes with less epochs.

- VGG16 and DenseNet Models has achieved good accuracy but required more computational resources.

- ResNet50 has shown poor performance for the same number of epochs.

Data augmentation and class imbalance handling significantly improved overall performance, with the final models achieving high accuracy and robust generalization across varied traffic sign classes.
