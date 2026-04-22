# comfyui-z-image-turbo-gguf
Use Z-Image Turbo (GGUF) in ComfyUI.
This guide handles installing ComfyUI and configuring the workflow.
Tested on Ubuntu Server LTS 24.04.4 with a i5-4590 and 12GB DDR3 and 16GB SWAP.

## Why use GGUF
<img width="921" height="291" alt="image" src="https://github.com/user-attachments/assets/f8d70489-6f8e-4f5d-a582-ab6a2a3845fa" />
It is a smaller version of the same image but suitable for Low to No VRAM and CPU configurations. This also makes it very fast if you do have a gpu even a GT 710 can perform with GGUF (Not Tested). 

## Install ComfyUI
ComfyUI requires Python 3.12 or higher (Python 3.13 is recommended). Check your Python version:
``` bash
python3 --version
```

If Python is not installed or the version is too low, install it following these steps:
``` bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

Install Git (if not installed)
``` bash
sudo apt install git
```

Create a virtual environment named comfy-env and activate the virtual environment. (Normal USER not root)
``` bash
python3 -m venv comfy-env
source comfy-env/bin/activate
```

Install Comfy-CLI
``` bash
pip install comfy-cli
```

Configure Command Line Auto-completion (Optional)
``` bash
comfy --install-completion
```

Installing ComfyUI with comfy-cli is very simple, requiring just one command: *(If you use cpu only like I do you need to add --cpu else it will fail.)*
``` bash
comfy install
```

### Install GPU Support

If you’re using an CPU, you need to install the CPU version of PyTorch:
``` bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

If you’re using an NVIDIA GPU, you need to install PyTorch with CUDA support:
``` bash
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu130
```

If you’re using an AMD GPU, you need to install PyTorch with ROCm support:
``` bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm6.4
```

If you’re using an Intel GPU, you need to install PyTorch with XPU support:
``` bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/xpu
```

## Launch ComfyUI
You can normally launch ComfyUI or use additional flags to change the IP & Port binding or modes.
``` bash
comfy launch
```
This will launch ComfyUI at http://localhost:8188

*Specify listen address and port*:  ```comfy launch -- --listen 0.0.0.0 --port 8080```
 
*Use CPU mode*:  ```comfy launch -- --cpu```
 
*Low VRAM mode*:  ```comfy launch -- --lowvram```
 
*Ultra-low VRAM mode*:  ```comfy launch -- --novram```
