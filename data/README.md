# Data

## Source

MICrONS Cubic Millimeter Functional Imaging Dataset

https://www.microns-explorer.org/cortical-mm3

The dataset contains two-photon functional imaging scans and processed
functional data, including neuronal ROI segmentation masks and calcium
traces.

## Data Used in This Project

This repository will not contain the complete MICrONS dataset because the
original functional imaging scans are very large.

The project will use a small subset from one imaging scan or field,
consisting of:

- selected 2D frames or representative images
- corresponding neuronal ROI segmentation masks

Only the data required for model development and evaluation will be
downloaded or exported.

## Not Used

The initial project will not use:

- complete two-photon movies
- visual stimulus movies
- behavioral or pupil traces
- EM imagery
- EM reconstruction
- functional-to-EM co-registration

Calcium traces may be explored later as a capstone extension.
