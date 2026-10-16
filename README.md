# CUDA C++ Multithreading Kernel Image Processing

A high-performance **CUDA C++ application** for image processing using **2D kernel convolution**.
This project demonstrates **parallel GPU acceleration vs sequential CPU processing** while applying common filters such as Gaussian blur, sharpening, edge detection, and more.

---

##  Features

* Process `.png` images and output results in grayscale `.png` format.
* Multiple convolution filters available:

  * **Gaussian Blur**
  * **Sharpen**
  * **Edge Detection**
  * **Laplacian**
  * **Gaussian + Laplacian**
* Benchmark comparison between:

  * **CUDA parallel kernel execution**
  * **Sequential CPU implementation**
* Flexible CUDA memory usage: run kernels with **global, constant, or shared memory** to compare performance.

---

##  Requirements

* **CUDA Toolkit** ([installation guide](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html))
* **png++ library** (wrapper for libpng):

```bash
sudo apt update
sudo apt install libpng++-dev
```

---

##  Build Instructions

A `Makefile` is included for easy compilation. Run:

```bash
make
```

This generates the executable `kernel_convolution` in the root directory.

---

##  Usage

```bash
./kernel_convolution <filter_type> <image_path> [cuda_mem_type]
```

### Arguments

* **`filter_type`** (required): one of
  `gaussian | sharpen | edge_detect | laplacian | gaussian_laplacian`
* **`image_path`** (required): path to input `.png` image
* **`cuda_mem_type`** (optional): CUDA memory type to use

  * `global`
  * `constant`
  * `shared` *(default)*

### Example

```bash
./kernel_convolution gaussian images/input.png shared
```

The processed image will be saved automatically in the `output/` folder.
Execution times for **parallel (CUDA)** and **sequential (CPU)** runs will be printed in the terminal.

---

## 📂 Project Structure

```
├── main.cu                # Application controller
├── image.h / image.cpp    # Image loading & saving (png++)
├── kernel.h / kernel.cpp  # Kernel creation (filter matrices)
├── gpu_convolution.cu     # CUDA kernels for parallel filtering
├── gpu_convolution.h      # CUDA kernel definitions
├── output/                # Processed output images
└── Makefile
```

---

## 📊 Example Output

Input vs. Processed (Gaussian blur example):

| Input                      | Output                       |
| -------------------------- | ---------------------------- |
| ![Input](images/input.png) | ![Output](output/output.png) |

---

## 🌟 Why This Project?

This project demonstrates:

* **Multithreading** using CUDA’s GPU kernels.
* **Performance benchmarking** between CPU and GPU.
* **Low-level memory optimization** (global, constant, shared memory).
* **Practical C++ system design** (modular architecture with classes for kernels, images, and GPU processing).



