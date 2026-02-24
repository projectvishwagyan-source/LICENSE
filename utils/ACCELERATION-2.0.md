## ⚡ Hardware Acceleration Support

Project **Vishwagyan** utilizes the `llm` ecosystem (crates like `llm`, `llm-base`, and `ggml`) to provide high-performance inference. We support various hardware acceleration backends to ensure low-latency responses for UPSC aspirants.

### 🌐 Platform Compatibility Matrix
| Platform/OS | CuBLAS (NVIDIA) | CLBlast (OpenCL) | Metal (Apple) |
| :--- | :---: | :---: | :---: |
| **Windows** | ✔️ | ✔️ | ❌ |
| **Linux** | ✔️ | ✔️ | ❌ |
| **MacOS** | ❌ | ❌ | ✔️ |

> **Note:** Only one acceleration backend can be active at a time. If both CuBLAS and CLBlast are specified, **CuBLAS** is prioritized.

---

### 🚀 Utilizing GPU Support

To activate GPU support, set the `use_gpu` attribute of the `ModelParameters` to `true`.

**For CLI Users:**
Add the `--use-gpu` flag to your command. 

#### 📦 Layer Offloading
If your model size exceeds your GPU's VRAM, you can specify the number of layers to offload using the `gpu_layers` parameter:
- **Default:** All layers are offloaded.
- **Example:** `--gpu-layers 20` (Offloads only the first 20 layers).

**Full Command Example (Llama with CUDA):**
```bash
cargo run --release --features cublas -- infer -a llama -m [path/to/model.bin] --use-gpu -p "Explain the Preamble of the Indian Constitution."
Protip: Reduce prompt feed time by increasing the batch size (e.g., --batch-size 256 or 512). Default is 8

Pre-requisites for Building

Windows
CuBLAS: Install the official NVIDIA CUDA Toolkit.

CLBlast: Install via vcpkg: vcpkg install clblast. Set OPENCL_PATH and CLBLAST_PATH environment variables.

Rust Flag (MSVC): Add this to your .cargo\config for static linking:

[target.x86_64-pc-windows-msvc]
rustflags = ["-Ctarget-feature=+crt-static"]

Linux
CuBLAS: Install CUDA. Set CUDA_INCLUDE_PATH and CUDA_LIB_PATH if not automatically detected.

CLBlast: Install via sudo apt install clblast. Set OPENCL_PATH and CLBLAST_PATH variables.

MacOS (Metal)
Ensure Xcode Command Line Tools are installed.

Build with --features=metal and run with --use-gpu.

Note: Metal currently falls back to CPU during prompt feeding but utilizes GPU for token generation.
