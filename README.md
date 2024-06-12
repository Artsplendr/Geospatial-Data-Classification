# Geospatial Images Classification Using Ensemble CNNs

## Reference: 
EuroSAT dataset, used in this experiment, is avalable at the following link: <http://madm.dfki.de/files/sentinel/EuroSAT.zip>

## Dataset: EuroSAT

The EuroSAT dataset is a dataset, which can be used for land cover classification, and it is based on Sentinel-2 satellite images. It consists of 27,000 labeled images covering 10 distinct classes:

1. Annual Crop
2. Forest
3. Herbaceous Vegetation
4. Highway
5. Industrial
6. Pasture
7. Permanent Crop
8. Residential
9. River
10. Sea Lake

Each image is 64x64 pixels in size, containing multi-spectral data. 
However, for this project, the RGB bands were used.

## Data Loading and Preprocessing

  ### Data Loading:
  Images and labels were loaded from the dataset directory: <http://madm.dfki.de/files/sentinel/EuroSAT.zip>.
  RGB bands were extracted and normalized.

  ### Data Splitting:
  The dataset was split into training (80%) and testing (20%) sets.
  Stratified sampling ensured balanced class representation.

  ### Data Augmentation:
  ImageDataGenerator was used to perform data augmentation, including rotations, shifts, and flips, to enhance the model's generalization.

## Ensemble Model
Three different CNN architectures were trained to form an ensemble model:

  ### Model 1: Simple CNN:
  Consists of 3 convolutional layers with 32, 64 filters and a dense layer with 128 units.
  Includes dropout for regularization.

  ### Model 2: Deeper CNN:
  A deeper model with 3 convolutional layers having 64, 128, and 256 filters, respectively.
  Includes a dense layer with 256 units and dropout.

  ### Model 3: CNN with Different Filter Sizes:
  Uses larger filter sizes (5x5) in the convolutional layers.
  Consists of 3 convolutional layers with 32, 64, and 128 filters, respectively.

## Training and Optimization

  ### Training Process:
  Each model was trained for up to 50 epochs using the Adam optimizer and sparse categorical cross-entropy loss.
  Data augmentation was applied during training.
  
  ### Callbacks:
  TensorBoard: Used for logging training metrics and visualization.
  EarlyStopping: Stopped training early if the validation loss did not improve for 10 epochs, restoring the best model weights.
  ReduceLROnPlateau: Reduced the learning rate if the validation loss plateaued.

## Evaluation:
Each model's performance was evaluated on the test set.
Accuracy and loss curves were plotted for training and validation phases.

## Ensemble Prediction:
Predictions from all three models were averaged to produce the final prediction.
This approach leverages the strengths of each individual model, leading to better generalization.

## Final Accuracy:
The ensemble model achieved an accuracy of approximately 94% on the test set, indicating a high level of performance and robustness in classifying the EuroSAT dataset images.

## Visualization and Predictions
To validate the model, three test images were randomly selected, and their predicted classes were visualized along with the true labels. This helped in qualitatively assessing the model's performance.

## Conclusion
The project successfully demonstrates the application of ensemble CNN models for geospatial image classification using the EuroSAT dataset. The ensemble approach combined multiple CNN architectures, leading to improved accuracy and robustness. The final ensemble model achieved a commendable accuracy of 94%, making it a reliable model for land use and land cover classification tasks using satellite imagery.
