# Full code will be released soon!

PyTorch implementation of "CAGT: Sim-to-Real Depth Completion with Interactive Embedding Aggregation and Geometry Awareness for Transparent Objects". The grasping video can be found [here](https://youtu.be/jyhZQPdEabQ).

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

- Ubuntu 16.04 + NVIDIA GeForce RTX 4090
- PyTorch 1.13.0

System dependencies can be installed by:

```bash
sudo apt-get install libhdf5-10 libhdf5-serial-dev libhdf5-dev libhdf5-cpp-11
sudo apt install libopenexr-dev zlib1g-dev openexr
```

Other dependencies can be installed by

```bash
pip install -r requirements.txt
```

## Testing
We provide CGsyn+ood pretrained checkpoints at [google drive](https://drive.google.com/file/d/1LpLP0cFohM_a9mP8Uxyqi1lMm43XcqIp/view?usp=sharing).

## Training

```
#Train on CGsyn dataset and test on CGreal
python train.py -c ./configs/train_cgsyn_val_cgreal.yaml

#Tran on CGsyn+ood and test on Transcg
python train.py -c ./configs/train_cgsyn+ood_val_transcg.yaml

```
