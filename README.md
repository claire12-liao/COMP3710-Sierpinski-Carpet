# COMP3710 Sierpinski Carpet

> A GPU-accelerated implementation and analysis of the Sierpiński Carpet using PyTorch for COMP3710 Lab 1.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/claire12-liao/COMP3710-Sierpinski-Carpet/blob/main/COMP3710_Sierpinski_Carpet.ipynb)

---

## Project Overview

The Sierpiński Carpet is a self-similar fractal created by repeatedly dividing a square into a 3 × 3 grid and removing the centre square.

This project uses vectorised PyTorch operations to test many pixel coordinates simultaneously. When CUDA is available, the calculations are performed on the GPU.

For recursion depth `d`:

- Image width and height: `3^d`
- Total grid pixels: `9^d`
- Retained pixels: `8^d`
- Theoretical fractal dimension: `log(8) / log(3) ≈ 1.8928`

## Main Features

- GPU acceleration using PyTorch and CUDA
- Vectorised coordinate processing
- Sierpiński Carpet generation at different recursion depths
- Coordinate-based colour visualisations
- Box-counting dimension estimation
- CPU and GPU execution-time comparison
- Automatic validation of the expected number of retained pixels

## Parallel Implementation

Each pixel is identified by its row and column coordinates.

The algorithm repeatedly examines the base-3 digits of both coordinates. A pixel is removed whenever the current horizontal and vertical digits are both equal to `1`. All other pixels remain in the carpet.

Because every pixel can be tested independently using the same operations, the calculation is suitable for PyTorch broadcasting and GPU parallel processing.

## Results

### Carpet Generation

At recursion depth 5:

- Image size: `243 × 243`
- Retained pixels: `32,768`
- Expected retained pixels: `8^5 = 32,768`
- Tensor device: `cuda:0`

The measured result matched the expected value.

### Box-Counting Dimension

At analysis depth 6:

- Estimated dimension: `1.8928`
- Theoretical dimension: `1.8928`
- Absolute error: `0.0000`

The measured box-counting dimension matched the theoretical value of `log(8) / log(3)`.

### CPU and GPU Benchmark

The benchmark was run on a Tesla T4 GPU with five repetitions.

| Depth | Grid Pixels | Retained Pixels | CPU Time (ms) | GPU Time (ms) | Speedup |
|---:|---:|---:|---:|---:|---:|
| 3 | 729 | 512 | 4.855 | 0.512 | 9.48× |
| 4 | 6,561 | 4,096 | 1.434 | 0.563 | 2.55× |
| 5 | 59,049 | 32,768 | 15.673 | 0.630 | 24.90× |
| 6 | 531,441 | 262,144 | 184.757 | 1.616 | 114.31× |
| 7 | 4,782,969 | 2,097,152 | 2,060.362 | 13.429 | 153.43× |

The results show that GPU acceleration becomes more effective as the workload increases. Timing results may vary between different runs and hardware.

## How to Run

1. Click the **Open in Colab** button near the top of this page.
2. In Colab, select **代码执行程序 → 更改运行时类型**.
3. Select **T4 GPU** as the hardware accelerator.
4. Click **全部运行**.
5. Check that the output displays `GPU available: True` and `Device: cuda`.

## Repository Files

- `COMP3710_Sierpinski_Carpet.ipynb` — complete implementation and experimental results
- `README.md` — project description and instructions
- `AI_USAGE.md` — declaration of AI-assisted work
- `LICENSE` — MIT licence

## AI Assistance

ChatGPT was used as a learning and development assistant. Details of its use, the generated suggestions and my evaluation of those suggestions are documented in `AI_USAGE.md`.

## Licence

This project is provided under the MIT Licence.