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
| **VDM** | Waymo | Val | L2 mAPH | **74.8** | [Coming Soon] |
| **VDM** | nuScenes | Val | mAP | **68.1** | [Coming Soon] |
| **VDM** | Argoverse 2 | Val | mAP | **42.3** | [Coming Soon] |
| **VDM** | ONCE | Val | mAP | **67.6** | [Coming Soon] |

## 🛠️ Getting Started

### Environment Requirements
This code has been tested in the following environment. Other versions might also work, but we recommend matching these for the best compatibility:
- **OS:** Linux (Ubuntu)
- **Python:** 3.10
- **CUDA:** 11.8
- **PyTorch:** 2.1.0
- **Spconv:** 2.3.6 (`spconv-cu118`)

### Installation
This project is based on [OpenPCDet](https://github.com/open-mmlab/OpenPCDet).

```bash
# Clone the repository
git clone https://github.com/qifeng22/VDM.git
cd VDM


# Install OpenPCDet
python setup.py develop
