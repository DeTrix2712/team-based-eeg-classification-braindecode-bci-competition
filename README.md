# Team-Based EEG Classification with Braindecode on BCI Competition Datasets

## Overview

This project aims to classify two motor imagery (MI) tasks: right-hand vs. right-foot imagery, using EEG signals from the BCI Competition III Dataset IVa. The primary goal is to build a deep learning pipeline for motor imagery classification while tackling challenges like EEG noise, subject variability, and data preprocessing. The project uses several Braindecode models and compares their performance in EEG classification.

## Dataset

- **Source**: BCI Competition III - Dataset IVa (Motor Imagery)
- **Subjects**: 5 healthy participants (aa, al, av, aw, ay)
- **Channels**: 118 EEG electrodes
- **Sampling Rate**: 100 Hz (downsampled version)
- **Task**: Binary classification of right-hand vs. right-foot motor imagery
- **Total Trials**: 560 labeled epochs (282 right-hand, 278 right-foot)

## Data Preprocessing

- **Bandpass Filtering**: Frequencies between 1–40 Hz to remove noise.
- **ICA-based Artifact Removal**: Using FastICA to remove eye blinks and muscle artifacts.
- **Epoching**: Segmented EEG data into 4-second epochs, event-locked to motor imagery cues.
- **Augmentation**: Applied Gaussian noise, time-shifting, channel dropout, and amplitude scaling to increase data variability.

## Models

Four deep learning architectures were implemented and compared:
- **EEGNet**: Compact convolutional neural network optimized for efficiency in real-time BCI applications.
- **ShallowFBCSPNet**: Integrates filter-bank spatial patterns with a deep learning framework, allowing for more interpretable results.
- **Deep4Net**: A hierarchical convolutional network designed for extracting multi-level spatio-temporal representations from EEG signals.
- **EEGConformer**: Combines convolutional layers with a transformer-based self-attention mechanism to capture both short-range and long-range dependencies.

## Results

Data augmentation significantly improved model performance, with **Deep4Net** and **EEGConformer** showing the largest gains in accuracy and ROC-AUC scores. The augmentation resulted in increased generalization, particularly for complex models.

| Model          | Accuracy (With Aug) | AUC (With Aug) |
|----------------|---------------------|----------------|
| EEGNet         | 85.71%              | 0.8919         |
| ShallowFBCSPNet| 70.54%              | 0.7309         |
| Deep4Net       | 84.82%              | 0.9509         |
| EEGConformer   | 73.21%              | 0.8479         |

## Usage

After installing the required libraries and datasets, you can train and evaluate the models using the Jupyter notebook located in BCI_Final_Project.ipynb. The notebook provides an end-to-end pipeline for preprocessing data, training models, and evaluating their performance.

## Acknowledgments

- Braindecode Library
- BCI Competition III Dataset IVa
- Special thanks to my collaborators Temirlan Nurmakhan, Nurmukhammed Aitymbetov, and Rakhat Myrzakhan.
