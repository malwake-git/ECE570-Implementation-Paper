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
The current code works on the following tools' versions
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


