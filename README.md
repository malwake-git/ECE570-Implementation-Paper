# ECE570-Implementation-Paper: An Attention-based Selection Network for Light Field Disparity Estimation

This repository is created to explain the running code behind the paper for the ECE 57000 class (Purdue University). The README.md will illustrate the adjustments done to the imported code. In addition to explaining how to run the code. The work is based on the LFattNett paper (github.com/LIAGM/LFattNet).

## First Introduction:-
 
The code introduces a network for estimating depth maps from a light field (LF) image. The model proposes a selection module that generates an attention map indicating the importance of each light field scene view and creates a disparity estimation based on it. The model contributes to the field of creating accurate depth estimation for LF images.

### Files:
* 1- LFattNet_evalution.py (LFattNet - modified)
* 2- LFattNet_train.py (LFattNet - modified)
* 3- func_generate_traindata_noise.py (LFattNet - modified)
* 4- func_makeinput.py (LFattNet - modified)
* 5- func_model_81.py (LFattNet - modified)
* 6- func_pfm.py (LFattNet - original)
* 7- func_savedata.py (LFattNet - original)
* 8- util.py (LFattNet - original)
* 9- LFNatt.ipynb (Train & Test - Preliminary)
* 10- LFNatt_dataset2.ipynb (Train & Test - Final)

 
## Second Implementation & Adjustment:-

### Primary Implementation Properties:

* Modified to work with newer Tensorflow, Keras, CUDA, Cudnn, and Python versions
* Better utilization of limited training resources, and low-level CPU/GPU
* Reliable to train and test over all HCL scenes dataset and any 512x512 light-field scene.
* Removed all unwanted warnings

### Environment:
The current code works on the following versions:
```
Python 3.6.0 & above
Tensorflow 2.x.x
Tensorflow-addons 0.15
CUDA 10.x.x 11.x.x
Cudnn 8.1
```

### Adjustments:
The following changes were made in order to satisfy the above implementation requirements:

#### LFattNet_train.py

* Functions (myGenerator, generate_traindata_for_train, data_augmentation_for_train) were adjusted to accept one invalid scene argument (Lines 88 - 93, 76 - 78, 243 - 244).

* Introduced display_status_ratio to control the batch size (Line 142). In addition to adjusting the number of epochs (Line 248).

* Adjusted input dataset (Lines 165 - 174, 183 - 189, 195 - 200)

```
```

#### LFattNet_evalution.py

* Adjusted input dataset (Lines 66 - 75)

* Eliminate version conversion errors (Lines 115 - 116, 120 - 121)

```
```

#### func_generate_traindata_noise.py

* Functions (generate_traindata_for_train) were adjusted to accept one invalid scene argument (Lines 7 - 8).

* Introduced new aa_arr array to create random selection array based on the shape of the given dataset for training (Line 69, 91).

```
```

#### func_model_81.py

* Adjusted function calls and imported packages to meet newer tools version requirements (Lines 1 - 11, 53, 120).

* Eliminated version conversion error (Lines 257).

```
```

## Third How to Run:-

### Dataset:

The dataset used in the implementation is the HCI 4D Light Field, to download:
http://hci-lightfield.iwr.uni-heidelberg.de/

Note: the scene dataset names used for training and/or testing can be found inside LFNatt_dataset2.ipynb and LFNatt.ipynb

After downloading the desired scene, extract the LF dataset inside the 'hci_dataset/'. (additional/, training/, test/, stratified/)


### Training:
* Uncomment line 250 in 'LFattNet_func/func_model_81.py', and comment line 253.
* Run python LFattNet_train.py (as in the notebooks)
* Checkpoint files will be saved as 'iterXXXX_valmseXXXX_bpXXX.hdf5'.' for every epoch. (Ex. check 'LFattNet_checkpoint/LFattNet_ckp/')
* Training process will be saved as 'train_iterXXXXX.jpg' 'val_iterXXXXX.jpg' for every epoch. (Ex. check 'LFattNet_output/LFattNet/')

### Testing:
* Uncomment line 253 in 'LFattNet_func/func_model_81.py', and comment line 250.
* Run python LFattNet_evalution.py (as in the notebooks)
* You may use the model created from training or use the pre-trained model 'pretrain_model_9x9.hdf5'
* To change the model for evaluation: change ``` path_weight= ""``` inside ('LFattNet_evalution.py' Line 84) to your desired model.

## Fourth Implementation Goal:-

The main goal of this project was to test the given algorithm over different LF datasets and compare the final metric performance results of the network. Secondary objectives included adjusting the imported source code to utilize limited resources running machines, eliminating all warnings and errors, and employing up-to-date environment tools' versions.
