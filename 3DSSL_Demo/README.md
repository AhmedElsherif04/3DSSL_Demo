# 3D Scanning & Spatial Learning - Gaussian Splatting Demo

This demo repository implements a minimum working example of how Gaussian Splatting can be used to obtain a 3D reconstruction from a set of images with corresponding camera poses.

# 1. Setup

1. Install dependencies. The command will create a new conda environment `3DSSL-demo` that includes pytorch and Gaussian Splatting:
    ```shell
    conda env create -f environment.yml
    ```
2. Ensure that the correct `nvcc.exe` is taken from the conda environment:  
   Linux:
    ```bash
    conda activate 3DSSL-demo
    conda env config vars set CUDA_HOME=$CONDA_PREFIX
    conda activate base
    conda activate 3DSSL-demo
    ```
   Windows: 
   ```bash
    conda activate 3DSSL-demo
    conda env config vars set CUDA_HOME=$Env:CONDA_PREFIX
    conda activate base
    conda activate 3DSSL-demo
    ```
3. Check whether the correct `nvcc` can be found on the path via:
    ```bash
    nvcc --version
    ```
    which should say something like `release 11.8`.   
4. Install Gaussian Splatting (which upon installation will compile CUDA kernels with `nvcc`):
    ```bash
    pip install gaussian_splatting@git+https://github.com/tobias-kirschstein/gaussian-splatting.git
    ```
# 2. Run
Execute the demo via
```bash
BW_IMPLEMENTATION=1 python run_gaussian_splatting.py
```

Despite running 3D reconstruction with Gaussian Splatting, it also starts a web-based interactive 3D viewer where you can follow the optimization:
[http://localhost:8008](http://localhost:8008)