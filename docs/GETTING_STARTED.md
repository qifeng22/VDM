# Getting Started

## Dataset Preparation
Our dataset organization and data preparation perfectly follow OpenPCDet. Please refer to the official [OpenPCDet Dataset Preparation](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/GETTING_STARTED.md) guidelines to set up the datasets (e.g., Waymo, nuScenes, Argoverse 2, ONCE).


## Training & Testing

### Training

* Train with multiple GPUs
```shell script
sh scripts/dist_train.sh ${NUM_GPUS} --cfg_file ${CONFIG_FILE}
```

### Testing
* Test with single GPU:
```shell script
python test.py --cfg_file ${CONFIG_FILE} --ckpt ${CKPT}
```

* Test with multiple GPUs:
```shell script
sh scripts/dist_test.sh ${NUM_GPUS} --cfg_file ${CONFIG_FILE} --ckpt ${CKPT}
```

