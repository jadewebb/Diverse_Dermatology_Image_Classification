# Diverse Dermatology Image Classification

Two machine learning models, Convolutional Neural Network (CNN) - GoogLeNet Architecture and CNN - Basic Architecture, trained to classify dermatology images of diverse skin tones

Dataset: Diverse Dermatology Images Dataset by Stanford University https://ddi-dataset.github.io/

  * 656 dermatology images of skin lesions from 570 diverse patients, labeled according to skin tone, malignancy, and diagnosis

  * Obtained by registering with Standford AIMI to obtain a unique download link, accessed through Microsoft Azure's AzCopy 

   > .\azcopy cp 'source_directory_url' 'destination directory' --recursive

Image dataset was loaded and visualized, metadata was loaded and 'malignancy' labels were isolated, and the datasets were combined

Dataset was shuffled, split into training, validation, and testing sets (70:15:15), preprocessed through standardization and augmentation (flip, rotation, zoom, contrast), and batched

Model architectures were defined as follows:

  * Basic CNN:

     * 3 Conv2D layers with ReLu activation, Kernel regularization
   
     * 2 MaxPooling2D layers
   
     * 4 Dropout layers
       
     * Flattening
     
     * 1 Dense layer
     
     * 1 Dense output layer with softmax activation for classification
  
  * GoogLeNet CNN: GoogLeNet architecture by Szegedy et al. according to https://github.com/KhuyenLE-maths/Implementation-of-GoogLeNet-on-Keras/blob/main/Implementation_of_GoogLeNet_on_Keras.ipynb

     * Note: the pretrained GoogLeNet was not utilized, instead the GoogLeNet architecture was trained from scratch using the DDI dataset
   
Models were trained with hyperparameter tuning based on loss minimization and accuracy maximization

  * Basic CNN Hyperparameters: Image size, Train split, Batch size, L2 regularization penalty, Dropout rate, Optimizer, Learning rate, Early stopping patience

  * GoogLeNet CNN Hyperparameters: Image size, Train split, Batch size, Optimizer, Learning rate, Early stopping patience

Models were evaluated based on training, validation, and test losses and accuracies

  * Best model: GoogLeNet CNN

Basic CNN | Train | Validation | Test
--- | ----- | ---------- | ----
Loss | 0.9848 | 1.0226 | 0.978
Accuracy | 0.7434 | 0.7041 | 0.7755

GoogLeNet CNN | Train | Validation | Test
--- | ----- | ---------- | ----
Loss | 1.6809 | 1.7087 | 1.4856
Dense 21 Loss | 0.5566 | 0.5687 | 0.4963
Dense 23 Loss | 0.5788 | 0.5711 | 0.4932
Dense 24 Loss | 0.5478 | 0.5689 | 0.4961
Dense 21 Accuracy | 0.7633 | 0.7449 | 0.8163
Dense 23 Accuracy | 0.7543 | 0.7449 | 0.8163
Dense 24 Accuracy | 0.7633 | 0.7449 | 0.8163
