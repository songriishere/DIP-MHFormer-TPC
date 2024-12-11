## Installation

- Create a conda environment: ```conda create -n hot python=3.11```
- Install PyTorch [official instructions](https://pytorch.org/get-started/locally/)
- ```pip3 install -r requirements.txt```

## Dataset setup

Download the processed data from [here](https://drive.google.com/drive/folders/1mUriHuX8cd4_vXRwkxR8KK7CWsvf4mL1?usp=drive_link). 

```bash
${POSE_ROOT}/
|-- dataset
|   |-- data_3d_h36m.npz
|   |-- data_2d_h36m_gt.npz
|   |-- data_2d_h36m_cpn_ft_h36m_dbb.npz
```

## Train the model

```bash
## MHFormer
python mhformer.py --batch_size 128 --nepoch 20 --lr 1e-3 --lr_decay_epoch 5 --lr_decay 0.95 --frames 351 --stride 1 --model mhformer.mhformer

## TPC w. MHFormer
python mhformer_tpc.py --batch_size 210 --nepoch 20 --lr 1e-3 --lr_decay_epoch 5 --lr_decay 0.95 --frames 351 --stride 1 --model mhformer.tpc_mhformer --token_num 117 --layer_index 1
```

