# Voxel Densification for Serialized 3D Object Detection: Mitigating Sparsity via Pre-serialization Expansion

[//]:[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/vdm-voxel-densification-module/3d-object-detection)](https://paperswithcode.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository serves as the official implementation for the paper:  
**Voxel Densification for Serialized 3D Object Detection: Mitigating
Sparsity via Pre-serialization Expansion** 

> **Abstract:** Recent advances in point cloud object detection have increasingly adopted Transformer-based and State Space Models (SSMs) to capture long-range dependencies. However, these serialized frameworks strictly maintain the consistency of input and output voxel dimensions, inherently lacking the capability for voxel expansion. This limitation hinders performance, as expanding the voxel set is known to significantly enhance detection accuracy, particularly for sparse foreground objects. To bridge this gap, we propose a novel **Voxel Densification Module (VDM)**. Unlike standard convolutional stems, VDM is explicitly designed to promote *pre-serialization spatial expansion*. It leverages sparse 3D convolutions to propagate foreground semantics to neighboring empty voxels, effectively densifying the feature representation before it is flattened into a sequence. VDM serves two key functions: (1) enhancing spatial connectivity via voxel densification, and (2) aggregating fine-grained local context through residual sparse blocks. Crucially, to balance the computational overhead of increased voxel density, we introduce a strategic downsampling mechanism. We integrate VDM into both Transformer-based (DSVT) and SSM-based (LION) detectors. Extensive experiments demonstrate that VDM consistently improves detection accuracy across multiple benchmarks.

<!--## 🚀 News
- **[2026-02-xx]** The paper is submitted.
- **[2026-02-xx]** Initial code release. Support for VDM-LION and VDM-DSVT.-->
## 🚀 News
- **[2026-02-05]** Initial code release.

## ✨ Highlights
- **Pre-serialization Spatial Expansion:** Defines a new paradigm to explicitly expand the foreground voxel set before sequence flattening, addressing the sparsity limitation in serialized models.
- **Generic Plugin:** Seamlessly integrates with state-of-the-art serialized detectors, including Transformer-based (**DSVT**) and SSM-based (**LION**) frameworks.

## 🏆 Model Zoo & Main Results

We provide the checkpoints and logs for our main models.

| Model | Dataset | Split | Metric | Performance | Download |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **VDM** | Waymo | Val | L2 mAPH | **74.8** | [Baidu Pan](https://pan.baidu.com/s/1sWUcnAvncIXQUyATdwguOA?pwd=jk22) |
| **VDM** | nuScenes | Val | mAP | **68.1** | [Baidu Pan](https://pan.baidu.com/s/1sWUcnAvncIXQUyATdwguOA?pwd=jk22) |
| **VDM** | Argoverse 2 | Val | mAP | **42.3** | [Baidu Pan](https://pan.baidu.com/s/1sWUcnAvncIXQUyATdwguOA?pwd=jk22) |
| **VDM** | ONCE | Val | mAP | **67.6** | [Baidu Pan](https://pan.baidu.com/s/1sWUcnAvncIXQUyATdwguOA?pwd=jk22) |

## 🛠️ Getting Started

### Environment Requirements
This code has been tested in the following environment. Other versions might also work, but we recommend matching these for the best compatibility:
- **OS:** Linux (Ubuntu)
- **Python:** 3.10
- **CUDA:** 11.8
- **PyTorch:** 2.1.0
- **Spconv:** 2.3.6 (`spconv-cu118`)

### Installation

Please refer to **[docs/INSTALL.md](docs/INSTALL.md)** for detailed step-by-step installation instructions, including environment setup and dependency installation.

### Quick Start

Please refer to **[docs/GETTING_STARTED.md](docs/GETTING_STARTED.md)** to learn how to prepare the datasets and run the training and testing scripts.

## 🙏 Acknowledgements

Our codebase integrates and builds upon the LION framework and OpenPCDet. We sincerely thank the authors for their outstanding work:

```bibtex
@article{liu2024lion,
  title={LION: Linear Group RNN for 3D Object Detection in Point Clouds},
  author={Zhe Liu, Jinghua Hou, Xingyu Wang, Xiaoqing Ye, Jingdong Wang, Hengshuang Zhao, Xiang Bai},
  journal={Advances in Neural Information Processing Systems},
  year={2024}
}
```