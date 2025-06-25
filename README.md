# Emotional-Classification-Speech-Processing

## Project Description:
This project is a machine learning pipeline developed to classify emotions from speech audio files using the RAVDESS dataset (audio-only). The pipeline utilizes Librosa for audio feature extraction and a Multi-Layer Perceptron (MLP) classifier for model training.

The emotions considered include:

   •	Neutral
   
   •	Calm
   
   •	Happy
   
   •	Sad
   
   •	Angry
   
   •	Fearful
   
   •	Disgust
   
   •	Surprised

The primary objective is to build an accurate classifier capable of identifying emotional content from speech using MFCC features.

## Pre-Processing Methodology:

Dataset Information (RAVDESS Audio Files)

Each audio file is named using the following format:

03-01-01-01-01-01-03.wav, where:

      •	Modality: 03 = Audio-only
      
      •	Vocal Channel: 01 = Speech
      
      •	Emotion: Encoded as integers (01-08)
      
      •	Intensity, Statement, Repetition, Actor: Used to identify and structure the data

### Steps:

1.	Loading Audio Files:
   
     o	Used librosa.load to load WAV files while preserving their original sample rates.

2.	Feature Extraction:
   
     o	Extracted MFCCs (Mel Frequency Cepstral Coefficients) using librosa.feature.mfcc

     o	Mean MFCCs across time frames are used as features for model input.

3.	Data Labeling:
   
     o	Emotion class parsed from file names using string operations.

     o	Mapped emotion codes to human-readable labels.

4.	Data Preparation:
   
     o	Features and labels are stored in X and y.

     o	Splitting into training and test sets using train_test_split.


## Model Pipeline:

Classifier Used:
Multi-Layer Perceptron (MLP) from sklearn.neural_network:

•	Architecture:

      	Hidden Layers: 2
      
      	Activation: relu
   
      	Solver: adam
      

•	Fitting:
   
      	Model trained on preprocessed MFCC features.
      
      	Labels are encoded using LabelEncoder.


## Workflow:

      	Read audio file paths.
      
      	Extract MFCC features.
      
      	Create dataset with extracted features.
      
      	Preprocess (scale, encode) the dataset.
      
      	Train and validate MLP model.
      
      	Evaluate accuracy on test set.



## Accuracy Metrics:


Before Reducing Features:
   
   •	Overall Accuracy: 77%
   
   •	Overall F1 Score:73.4%
   
   •	Accuracy of classes:
   
      1.	Neutral:92%
         
      2.	Calm: 76%
         
      3.	Happy: 62%
         
      4.	Sad: 75%
         
      5.	Angry: 76%
          
      6.	Fearful:82%
          
      7.	Disgust:70%
          
      8.	Surprised:76%

    
After Reducing Features:

   •	Overall Accuracy: 82%
   
   •	Overall F1 Score:81.7%
   
   •	Accuracy of classes:
   
      1.	Calm: 82%
      
      2.	Happy: 85%
      
      3.	Sad: 78%
      
      4.	Angry: 82%
      
      5.	Fearful:85%
      
      6.	Disgust:81%
      


## Saved Model:

	Trained model is saved as: best_emotion_model.pth (Pickled)

	This can be used for deployment or inference on new audio data.
