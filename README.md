Hi👋

Brain Tumor Segmentation using Attention U-Net with Explainable AI
Overview

This project presents a deep learning framework for automatic brain tumor segmentation from multi-modal MRI scans. The system uses an enhanced Attention U-Net architecture along with a dynamic modality reliability module and Explainable AI (Grad-CAM) to accurately identify tumor regions and visualize the model’s decision-making process.

Brain tumor segmentation is an important task in medical image analysis because it helps doctors determine tumor boundaries and plan treatments. Manual segmentation is time-consuming and often varies between experts. This project aims to address these challenges using a deep learning-based automated segmentation pipeline.

Key Features
Multi-Modal MRI Processing

The model uses four MRI modalities from the BraTS dataset:

T1

T2

T1ce

FLAIR

Each modality highlights different brain tissue characteristics, helping the model detect tumors more accurately.

Dynamic Modality Reliability Module (Novelty)

A custom module learns the relative importance of each MRI modality dynamically.
Instead of treating all MRI scans equally, the network automatically adjusts the influence of each modality depending on its contribution to tumor detection.

This improves segmentation robustness when some modalities have weaker tumor contrast.

Attention U-Net Architecture

The core segmentation network is based on Attention U-Net, which extends the standard U-Net architecture with attention gates.

Attention gates allow the model to:

focus on tumor-relevant regions

suppress irrelevant background features

This improves segmentation accuracy, especially around tumor boundaries.

Dice Loss Optimization

The model is trained using Dice Loss, which measures overlap between predicted tumor masks and ground truth annotations.

Dice Loss is particularly effective in medical segmentation because it handles class imbalance between tumor and non-tumor pixels.

Explainable AI using Grad-CAM

To make the model more interpretable, Grad-CAM (Gradient-weighted Class Activation Mapping) is used.

Grad-CAM generates heatmaps that highlight which regions of the MRI image influenced the segmentation prediction, allowing us to verify that the model focuses on meaningful tumor areas.

Dataset

This project uses the BraTS (Brain Tumor Segmentation) dataset, which is widely used for brain tumor research.

Each patient scan includes:

T1 MRI

T2 MRI

T1ce MRI

FLAIR MRI

Ground truth tumor mask

The images are stored in NIfTI (.nii) format.

During preprocessing:

3D MRI volumes are converted into 2D slices

The four modalities are stacked to create a 4-channel input image

Model Pipeline

MRI Modalities (T1, T2, T1ce, FLAIR)
↓
Dynamic Modality Reliability Module
↓
Attention U-Net Encoder-Decoder Network
↓
Tumor Segmentation Mask
↓
Explainable AI Visualization (Grad-CAM)

Training Procedure

Load BraTS MRI dataset

Convert MRI volumes into 2D slices

Stack modalities as 4-channel input

Train Attention U-Net using Dice Loss

Evaluate segmentation results

Generate Grad-CAM explainability visualizations

Visualization Output

The system produces visual outputs including:

MRI slice

Ground truth tumor mask

Predicted tumor segmentation

Grad-CAM heatmap highlighting model attention

These visualizations help interpret the model's predictions and validate segmentation performance.

Requirements

Python libraries used:

PyTorch

NumPy

Matplotlib

Nibabel

pytorch-grad-cam

Kaggle API

Applications

Brain tumor detection

Medical image analysis

Clinical decision support

AI-assisted radiology workflows

Future Improvements

Possible future extensions include:

3D U-Net for volumetric tumor segmentation

Transformer-based medical segmentation models

Multi-class tumor subregion segmentation

Integration with hospital imaging systems
