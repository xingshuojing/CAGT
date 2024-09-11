# Full code will be released soon!

PyTorch implementation of "CAGT: Sim-to-Real Depth Completion with Interactive Embedding Aggregation and Geometry Awareness for Transparent Objects". The grasping video can be found [here](https://youtu.be/Sp3Yb0dGUMQ).

## Dataset Preparation
### ClearGrasp Dataset
ClearGrasp can be downloaded at their [official website](https://sites.google.com/view/cleargrasp/data) (Both training and testing dataset are needed). After you download zip files and unzip them on your local machine, the folder structure should be like
```
${DATASET_ROOT_DIR}
├── cleargrasp
│   ├── cleargrasp-dataset-train
│   ├── cleargrasp-dataset-test-val
```
### Omniverse Object Dataset
Omniverse Object Dataset can be downloaded [here](https://drive.google.com/drive/folders/1wCB1vZ1F3up5FY5qPjhcfSfgXpAtn31H?usp=sharing). After you download zip files and unzip them on your local machine, the folder structure should be like
```
${DATASET_ROOT_DIR}
├── omniverse
│   ├── train
│   │	├── 20200904
│   │	├── 20200910
```
### TransCG Dataset
TransCG dataset is now available on [official page](https://graspnet.net/transcg). 

## Requirements
The code has been tested under

- Ubuntu 20.04 + NVIDIA GeForce RTX 4090
- Python 3.8.1
- PyTorch 1.13.0

System dependencies can be installed by:

```bash
sudo apt-get install libhdf5-10 libhdf5-serial-dev libhdf5-dev libhdf5-cpp-11
sudo apt install libopenexr-dev zlib1g-dev openexr
```

Base dependencies can be installed by a conda environment:

```bash
conda env create -f environment.yaml
```

Other dependencies can be installed by:

```bash
conda activate cagt
conda install pytorch==1.13.0 torchvision==0.14.0 torchaudio==0.13.0 pytorch-cuda=11.7 -c pytorch -c nvidia
pip install causal_conv1d-1.0.0+cu118torch1.13cxx11abiFALSE-cp38-cp38-linux_x86_64.whl
pip install mmamba_ssm-1.0.1+cu118torch1.13cxx11abiFALSE-cp38-cp38-linux_x86_64.whl
```
The .whl files of causal_conv1d and mamba_ssm could be found here [causal_conv1d](https://github.com/Dao-AILab/causal-conv1d/releases/tag/v1.0.0) | [mmamba_ssm](https://github.com/state-spaces/mamba/releases/tag/v1.0.1).


## Testing
We provide CGsyn+OOD pretrained checkpoint at [google drive](https://drive.google.com/file/d/1LpLP0cFohM_a9mP8Uxyqi1lMm43XcqIp/view?usp=sharing).

## Training

```
#Train on CGsyn dataset and test on CGreal
python train.py -c ./configs/train_cgsyn_val_cgreal.yaml

#Tran on CGsyn+ood and test on Transcg
python train.py -c ./configs/train_cgsyn+ood_val_transcg.yaml
```
