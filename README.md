# K-Means Clustering and Band Analysis Tool

This Python script performs K-Means clustering and related analysis on dose distribution data from radiation beam experiments.  
It is designed to process data from Excel files, remove artifacts, and refine regions of interest (ROIs) for further analysis.

---

## Features

### K-Means Clustering
- **Lloyd's algorithm** is used to iteratively assign data points to clusters and compute cluster representatives.
- Supports initialization for reproducibility and effective clustering.

### Artifact Removal
- Identifies and removes anomalies based on slope criteria to ensure clean data for clustering and regression.

### Linear Regression Analysis
- Fits a linear model to the refined ROI to analyze dose distributions.

### ROI Refinement
- Refines the ROI by centering data and applying a percentage difference cutoff.

### Visualization
- Plots data with cluster assignments, representatives, and regression fits for user verification.

### Support for Multiple Datasets
- Processes data from multiple Excel files specified in predefined paths.

---

## Required Data Format

The input data should be in Excel files with the following columns:
- **`centered_axis_cm`**: Represents the deviation values.
- **`line_dose_normalized`**: Represents normalized dose values.

---

## Usage

Instantiate the `Band` class with the following parameters - this seperates the plateau from the penumbra, and fits it with a 'crude fit':

```python
band_analysis = Band(
    path="path_to_excel_file.xlsx",
    weight=0.5,
    orientation="vertical",
    k=3,
    m=0.45
)
```

Then refine the fit, specifying how close the data must be to the original fit to be considered in refined fit - done in terms of %SD

```python
band_analysis.refine(allot_pct=3)
```
