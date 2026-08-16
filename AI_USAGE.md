# AI Use Declaration

## Project Overview

For this project, I implemented and analysed a GPU-accelerated Sierpiński Carpet using PyTorch.

I used ChatGPT as a learning and development assistant. It helped me understand the Part 3 requirements, plan the implementation, develop initial code structures, design experiments and improve the documentation.

I selected the final topic following teaching-staff feedback, configured Google Colab with a Tesla T4 GPU, ran every notebook section, checked the results and managed the GitHub repository myself.

## Project-Related AI Interactions

### 1. Understanding the Requirements and Selecting a Fractal

**My request:**

“Explain the Part 3 requirements and recommend a fractal that is manageable to implement, analyse and explain during the Demo.”

**How I used the response:**

ChatGPT compared possible fractal topics and explained their implementation requirements. After receiving teaching-staff feedback that the Sierpiński Triangle was not permitted, I selected the recommended Sierpiński Carpet and created a new implementation and repository.

### 2. PyTorch Implementation

**My request:**

“Help me design a GPU-compatible Sierpiński Carpet implementation using vectorised PyTorch operations.”

**AI assistance:**

ChatGPT suggested representing the carpet as a two-dimensional tensor and processing many pixel coordinates together. The implementation checks the base-3 position of each pixel and removes a pixel when its horizontal and vertical digits are both equal to the centre value.

**My work and verification:**

I reviewed and ran the implementation in Google Colab. I confirmed that CUDA was available and that the tensors were stored on `cuda:0`.

At recursion depth 5, the program produced:

* Image size: `243 × 243`
* Retained pixels: `32,768`
* Expected retained pixels: `8^5 = 32,768`

This confirmed that the recursive structure was generated correctly.

### 3. Visualisation and Fractal Analysis

**My request:**

“Help me compare recursion depths, create coordinate-based colour visualisations and estimate the box-counting dimension.”

**AI assistance:**

ChatGPT suggested:

* Comparing recursion depths from 1 to 5
* Colouring retained pixels using their horizontal and vertical coordinates
* Counting occupied boxes at different box sizes
* Using a linear fit to estimate the fractal dimension

**My work and verification:**

I ran each experiment and checked the figures and numerical results.

The estimated box-counting dimension was `1.8928`, which matched the theoretical value:

`log(8) / log(3) = 1.8928`

The absolute error was approximately `0.0000`.

### 4. CPU and GPU Performance Comparison

**My request:**

“Help me design a fair CPU and GPU benchmark for different recursion depths.”

**AI assistance:**

ChatGPT suggested using repeated measurements, synchronising CUDA before recording GPU time and comparing the same tensor operations on both devices.

**My work and verification:**

I ran the benchmark five times for each recursion depth and calculated the average execution time.

For the largest tested workload at depth 7:

* Total grid pixels: `4,782,969`
* Retained pixels: `2,097,152`
* CPU time: approximately `2060.362 ms`
* GPU time: approximately `13.429 ms`
* GPU speedup: approximately `153.43×`

The results showed that GPU acceleration became more effective as the workload increased.

### 5. Comments and Documentation

ChatGPT helped me improve the bilingual code comments, notebook explanations, plot layout, README and AI use declaration.

I reviewed and edited the suggested text so that it accurately described my implementation and experimental results.

## Evaluation of the AI Output

I did not treat the AI output as automatically correct. I checked it by:

* Running every notebook section
* Confirming tensor shapes, devices and pixel counts
* Comparing calculated values with theoretical values
* Reviewing all generated figures
* Repeating the CPU and GPU benchmarks
* Following teaching-staff feedback when selecting the final topic
* Keeping only code and explanations that I understood and could verify

Some suggestions required clarification or adjustment, particularly the original topic selection and figure layout. I modified these parts before including them in the final project.

## Ownership Statement

ChatGPT contributed explanations, initial code structures, comments, experiment ideas and documentation suggestions.

I selected the final project direction, obtained teaching-staff guidance, configured the environment, ran and checked all experiments, reviewed the code, interpreted the results, managed the GitHub repository and prepared the final project.

I understand how the Sierpiński Carpet is generated, how PyTorch processes pixel coordinates in parallel, how the box-counting dimension is estimated and why GPU acceleration is more effective for larger workloads.

The relevant ChatGPT conversation history remains available and can be shown to the demonstrator if requested.
