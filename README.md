# Shape and Color Detection using OpenCV (Classic CV)

## Overview
Detects simple geometric shapes (rectangle, square, circle, triangle, etc.) and their colors (red/green/blue/yellow) using classical computer vision techniques (no deep learning).

## What's fixed/updated
Originally, average-RGB→single-pixel-HSV approach missed some yellows. This repository uses **HSV color masks** and computes the **fraction of pixels inside each contour** that match a color — far more robust for varied lighting and anti-aliased edges.

## How it works (short)
1. Convert image to grayscale → blur → Canny edges.
2. Find contours and filter by area.
3. Approximate polygons (`cv2.approxPolyDP`) to classify shapes:
   - 3 vertices → triangle
   - 4 vertices → square/rectangle (aspect ratio test)
   - >6 vertices → circle
4. Detect color per contour:
   - Convert image to HSV
   - For each color, `cv2.inRange()` with predefined HSV ranges
   - Compute color fraction inside the contour; choose best color if fraction above threshold
   - Fallback to mean-HSV mapping if needed

## Files
- `shape_color_detector.py` — single-file script for VS Code / local use
- `notebook.ipynb` — optional Colab notebook split into runnable cells (or use the provided code segments)
- `requirements.txt`

## Run locally (VS Code)
1. Clone repo:
   ```bash
   git clone https://github.com/yourname/shape-color-detection.git
   cd shape-color-detection
