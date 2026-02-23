# Installation

### Requirements
All the codes are tested in the following environment:
* Python 3.10
* PyTorch 2.1.0
* CUDA 11.8
* [spconv v2.x](https://github.com/traveller59/spconv) (`spconv-cu118==2.3.6` is recommended and tested)

### Install VDM codebase

**1. Clone the repository**
```bash
git clone https://github.com/qifeng22/VDM-main.git
cd VDM-main
```

**2. Install core dependencies**
```bash
# Install PyTorch with CUDA 11.8
pip install torch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0 --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118)

# Install spconv (crucial for 3D sparse convolution)
pip install spconv-cu118==2.3.6
```

**3. Install OpenPCDet and VDM**
```bash
# This will automatically install the remaining dependencies
python setup.py develop
```

### Install Linear RNN operators
Since VDM integrates SSM-based frameworks (like LION), you need to install specific Linear RNN operators.

* **Mamba**
  * Install `causal-conv1d` by running:
    ```bash
    pip install causal-conv1d==1.2.0.post2
    ```
  * Build and install the Mamba operator locally:
    ```bash
    cd pcdet/ops/mamba
    python setup.py install
    cd ../../../
    ```