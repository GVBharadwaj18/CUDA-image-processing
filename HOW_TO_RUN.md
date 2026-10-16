# How to Run

A quick guide to compiling and running the CUDA image processing application.

---

## 1. Prerequisites

- **NVIDIA CUDA Toolkit** (`nvcc`)
- **png++ library** (`libpng++-dev` on Linux / WSL / Ubuntu)

Install dependencies on Ubuntu / Debian:
```bash
sudo apt update
sudo apt install libpng++-dev
```

---

## 2. Compile

Build the binary using `make`:
```bash
make
```
This generates the executable `kernel_convolution`.

To clean build files and recompile:
```bash
make clean
make
```

---

## 3. Execution

### Command Syntax
```bash
./kernel_convolution <filter_type> <image_path> [cuda_mem_type]
```

### Parameters
- **`filter_type`** (Required):
  - `gaussian` - Gaussian blur filter
  - `sharpen` - Image sharpening filter
  - `edge_detect` - Edge detection filter
  - `laplacian` - Laplacian filter
  - `gaussian_laplacian` - Gaussian of Laplacian filter
- **`image_path`** (Required): Path to an input `.png` image (e.g. `images/input.png`).
- **`cuda_mem_type`** (Optional, default: `shared`):
  - `shared` - Uses CUDA shared memory tiles
  - `constant` - Uses CUDA constant memory for the mask
  - `global` - Uses CUDA global device memory

---

## 4. Examples

**Gaussian blur using shared memory:**
```bash
./kernel_convolution gaussian images/input.png shared
```

**Edge detection using constant memory:**
```bash
./kernel_convolution edge_detect images/input.png constant
```

**Sharpen filter using default memory setting:**
```bash
./kernel_convolution sharpen images/input.png
```

---

## 5. Output

- Processed images are automatically saved to `output/` as:
  `output/result_<filter_type>.png` (e.g., `output/result_gaussian.png`).
- The console will display side-by-side benchmark timings comparing **CUDA parallel** vs. **CPU sequential** execution in microseconds (μs).
