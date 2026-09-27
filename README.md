Midterm Project for Computation Vision class Fall 2026
# Automated Neuronal ROI Segmentation in MICrONS Two-Photon Imaging

## Project Overview

This project is a Tier 1 computer vision application for automated neuronal
region-of-interest (ROI) segmentation in two-photon microscopy images.

The application will take selected processed two-photon images from the
MICrONS functional imaging dataset as input and use a U-Net segmentation
model to predict neuronal ROI masks. The predicted masks will be compared
with published MICrONS reference segmentations using IoU and Dice scores.

## Tier

**Tier 1 – Single-model computer vision application**

This tier was selected because the project focuses on one end-to-end
semantic segmentation model with a clearly defined image input, mask output,
and quantitative evaluation.

## Problem Statement

Two-photon microscopy can produce large numbers of image frames, making
manual identification of neuronal regions repetitive and time-consuming.
Consistent neuronal ROIs are important for downstream visualization and
functional analysis, including analysis of calcium activity.

## Solution Overview

The application will process selected two-photon images using a U-Net
segmentation model and generate predicted neuronal ROI masks.

Predicted masks will be compared with MICrONS reference segmentation masks
using visual overlays, Intersection over Union (IoU), and Dice coefficient.

## Technical Approach

- Computer vision task: semantic segmentation
- Initial output: binary neuronal ROI mask
- Model: U-Net segmentation model
- Framework: PyTorch
- Input: processed 2D two-photon image
- Evaluation: IoU, Dice coefficient, and visual mask comparison

A pretrained encoder will be used if it is compatible with the selected
microscopy data. Otherwise, a small U-Net baseline will be trained on the
selected subset.

## Data Plan

**Source:** MICrONS cubic-millimeter functional imaging dataset

The public MICrONS release contains raster- and motion-corrected two-photon
functional imaging scans together with processed functional data including
cell segmentation masks and calcium traces.

Because the complete imaging dataset is very large, this project will use
only a small subset from one scan or imaging field.

Planned data preparation:

1. Select one functional imaging scan or field.
2. Extract a manageable set of representative 2D frames or summary images.
3. Retrieve the published ROI segmentation for the same imaging field.
4. Prepare aligned image-mask pairs for model development and evaluation.

Data source:
https://www.microns-explorer.org/cortical-mm3

## Success Metrics

### Primary metric
Mean Intersection over Union (IoU)

Initial target: **mean IoU >= 0.60**

### Secondary metric
Mean Dice coefficient

Initial target: **mean Dice >= 0.70**

Qualitative evaluation will also compare the original image, reference mask,
predicted mask, and overlay.

## Milestone Plan

| Week | Phase | Goal |
|---|---|---|
| 5 | Blueprint | Proposal, GitHub repository, data source, and metrics defined |
| 6 | First Working Demo | Run an end-to-end segmentation baseline on 5–10 sample images |
| 7–8 | Make It Yours | Prepare MICrONS subset, refine preprocessing, and train or fine-tune if needed |
| 9 | Improve & Measure | Compute IoU and Dice, inspect failure cases, and make focused improvements |
| 10 | Package & Present | Finalize notebook, demo, README, repository, and presentation |

## Risks and Plan B

### Risk 1: Data access and format

MICrONS functional imaging files are very large and may require specialized
preprocessing.

**Plan B:** Work only with exported representative images and matching ROI
masks instead of downloading complete scans.

### Risk 2: Model and data compatibility

A pretrained segmentation model may not transfer well to two-photon
microscopy images.

**Plan B:** Train a small U-Net baseline on the selected subset and limit the
application to a one-field proof of concept.

## Resources

- Python
- PyTorch
- NumPy
- OpenCV
- Matplotlib
- Google Colab
- GitHub

Estimated project cost: **$0**

## Future Extension

A future version could extend the application from ROI segmentation to
calcium-activity analysis:

Two-photon image → neuronal ROI segmentation → ROI calcium trace extraction
→ activity visualization over time.

This would keep the capstone focused on the functional imaging data without
requiring EM co-registration.

