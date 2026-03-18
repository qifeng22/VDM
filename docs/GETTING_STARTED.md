# Getting Started

## Dataset Preparation
Our dataset organization and data preparation perfectly follow OpenPCDet. Please refer to the official [OpenPCDet Dataset Preparation](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/GETTING_STARTED.md) guidelines to set up the datasets (e.g., Waymo, nuScenes, Argoverse 2, ONCE).

## Training & Testing

All training and testing scripts should be executed within the `tools` directory.

```bash
cd tools
```

### Training

* **Waymo:**
```bash
CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7 python -m torch.distributed.launch \
--nproc_per_node=8 --master_port=29988 train.py  --tcp_port 29988  --launcher pytorch  \
--cfg_file ./cfgs/VDM_lion_models/lion_mamba_waymo_8x_1f_1x_one_stride_128dim.yaml \
--extra_tag lion_mamba_waymo_8x_1f_1x_one_stride_128dim \
--batch_size 16 --epochs 24 --max_ckpt_save_num 4 --workers 4 --sync_bn --dataset waymo
```

* **nuScenes:**
```bash
CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7 python -m torch.distributed.launch \
--nproc_per_node=8 --master_port=29988 train.py  --tcp_port 29988  --launcher pytorch  \
--cfg_file ./cfgs/VDM_lion_models/lion_mamba_nusc_8x_1f_1x_one_stride_128dim.yaml \
--extra_tag lion_mamba_nusc_8x_1f_1x_one_stride_128dim \
--batch_size 16 --epochs 36 --max_ckpt_save_num 4 --workers 4 --sync_bn --dataset nuscenes
```

* **Argoverse 2:**
```bash
CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7 python -m torch.distributed.launch \
--nproc_per_node=8 --master_port=29988 train.py  --tcp_port 29988  --launcher pytorch  \
--cfg_file ./cfgs/VDM_lion_models/lion_mamba_1f_1x_argo_128dim_sparse_v2.yaml \
--extra_tag lion_mamba_1f_1x_argo_128dim_sparse_v2 \
--batch_size 16 --epochs 12 --max_ckpt_save_num 4 --workers 4 --sync_bn --dataset argo2
```

* **ONCE:**
```bash
CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7 python -m torch.distributed.launch \
--nproc_per_node=8 --master_port=29988 train.py  --tcp_port 29988  --launcher pytorch  \
--cfg_file ./cfgs/once_models/centerpoint_with_lion_with_128dim_mamba.yaml \
--extra_tag centerpoint_with_lion_with_128dim_mamba \
--batch_size 16  --epochs 80 --max_ckpt_save_num 4 --workers 4 --sync_bn --dataset once
```

### Testing

* **Test with a single GPU:**
```bash
python test.py --cfg_file ${CONFIG_FILE} --ckpt ${CKPT}
```
