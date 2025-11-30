Image Processing Tasks – Sampling, Quantization, Bitplanes, X-Ray Analysis

This repository contains a full collection of image-processing tasks implemented in Python, focusing on sampling, quantization, channel separation, bitplane analysis, and X-ray image processing.
All experiments were performed using NumPy, OpenCV, Pillow, and Matplotlib.

The project includes both color and X-ray (grayscale & DICOM) images.

📌 Contents
1. Down Sampling Comparison (Two Methods)

Two different down-sampling methods were implemented:

Method A: Removing rows/columns with a fixed step

Method B: Block-based averaging (mean pooling)

Both down-sampled outputs were converted to matrices and subtracted to analyze:

The smoothness difference between the two

Loss of sharp edges

Structural distortions due to non-uniform sampling

This comparison illustrates how different sampling strategies affect texture, edges, and overall pixel distribution.

2. A Third Custom Down Sampling Method

A new method—different from the two introduced in class—was designed.

Example:

Weighted sampling

Or Gaussian-blur + subsampling

Or randomized pixel selection

This method enabled comparing traditional sampling with more advanced approaches in terms of noise preservation, perceived sharpness, and aliasing.

3. Effect of Scale Parameter in Up Sampling

The scale parameter directly influences:

Output resolution

Amount of pixel replication/interpolation

Smoothing or blockiness in the final image

Low scale → minimal enlargement, low distortion
High scale → visible blocky patterns (nearest) or smoothed artifacts (bilinear/bicubic)

4. Pixel-by-Pixel Up Sampling (Manual Implementation)

A complete pixel-wise up-sampling algorithm was implemented without using library functions.

Steps included:

Creating a larger empty matrix

Copying each pixel into an expanded neighborhood

Forming a nearest-neighbor up-sampled image manually

This approach clarifies how up-sampling operates at its lowest computational level.

5. Color Image Quantization

Quantization was extended from grayscale to full RGB images, including:

Bit-depth reduction per channel

Comparison between uniform and non-uniform quantization

Visual effects of reducing colors while keeping structural details

The results demonstrate color banding, loss of gradients, and saturation changes depending on quantization levels.

6. Channel Separation + Bitplane Visualization (Three Color Images)

Three different color images were processed to analyze:

RGB channel separation

Bitplane decomposition for each channel

Effect of color region intensity on bit significance

This allows studying:

How high-order bitplanes preserve dominant structures

How low-order planes capture noise and fine edges

Differences between saturated vs. low-intensity regions in each channel

7. Six Images From Six Types of Bitplane Combinations

Six composite images were generated using different bitplane combinations such as:

Sum of top bitplanes (MSB only)

Sum of lower bitplanes (LSB)

Mixed (e.g., bits 0–3 or bits 4–7)

Single-channel vs multi-channel bitplane fusion

Analysis included:

High-order bitplanes → contain most structural information

Low-order bitplanes → texture/noise details

Multi-channel combinations → restore more recognizable color features

8. Bitplane Extraction for X-Ray Images (JPG + DICOM)

Both standard and medical DICOM X-ray files were processed.

Performed tasks:

Reading DICOM with pydicom

Converting pixel data into viewable format

Extracting all 8 bitplanes

Analyzing diagnostic information in high vs. low significance bits

Observations:
🛠 Technologies & Libraries

Python 3.x

NumPy

OpenCV

Pillow (PIL)

Matplotlib

pydicom

📁 Included Files

lab4#2.ipynb

lab5#2.ipynb

lab6#2.ipynb

lab7#2.ipynb

lab8#2.ipynb

pics/ (folder containing all required images)

📌 Purpose

This project demonstrates core image-processing concepts used in:

Image compression

Medical imaging

Feature extraction

Digital image representation

Visualization of pixel-level operations

It is suitable for university assignments, machine-vision learning, or practical research.
Higher bitplanes highlight bone structures

Lower bitplanes reveal noise and minor intensity variations

Bitplane patterns differ strongly from natural RGB images because X-ray is grayscale with higher dynamic range

