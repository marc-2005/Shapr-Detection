# Shape and Color Detection using OpenCV (Classic CV)

## Overview
Detects simple geometric shapes (rectangle, square, circle, triangle, etc.) and their colors (red/green/blue/yellow) using classical computer vision techniques .

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
## Problems 
- There was a problem in detecting yellow color

## Files
- `Shape_Detector.py` — single-file script for VS Code / local use
- `tst.jpg`
