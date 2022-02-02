# Focus On Depth - A single DPT encoder for AutoFocus application and Dense Prediction Tasks

![pytorch](https://img.shields.io/badge/pytorch-v1.10-green.svg?style=plastic)

<!-- ![presentation](https://i.ibb.co/rbySmMc/DL-FOD-POSTER-1.png) -->

## Abstract

> Recent works have shown that in the real world, humans
rely on the image obtained by their left and right eyes in or-
der to estimate depths of surrounding objects. Thus, depth
estimation is a classic task in computer vision, which is of
great significance for many applications such as augmented
reality, target tracking and autonomous driving. We firstly
summarize the deep learning models for monocular depth
estimation. Secondly, we will implement a recent Vision
Transformers based architecture for this task. We will seek
to improve it by adding a segmentation head in order to
perform multi-task learning using a customly built dataset.
Thirdly, we will implement our model for in-the-wild im-
ages (i.e. with no control on the environment, the distance
and size of objects of interests, and their physical properties
(rotation, dynamics, etc.)) for Auto-focus application on
humans and will give qualitative comparison across other
methods.

<!--
## TO DOs

- [x] Make the training script work
- [x] Create the dataset with person segmentation and depth estimation
- [x] Create a strong codebase for training
- [x] Add data augmentations
- [x] Make the code modulable with timm and the list of hooks
- [x] Add an option to select whether we want depth only or segmentation only or both
- [x] Make 2 optimizers?
- [x] Do we have to fix a seed for reproducibility?
- [x] Scheduler
- [x] Create a strong code base for inference
- [ ] Training wiki
- [ ] Why the predicted depth map is inverted?
- [ ] Understand the impact of the transformation
- [ ] Make our training data opensource
- [ ] Push the model into HuggingFace?
-->

## Requirements

Run: ``` pip install -r requirements.txt ```

## Training

### Build the dataset

Our model is trained on a combination of
+ [inria movie 3d dataset](https://www.di.ens.fr/willow/research/stereoseg/).
+ [NYU2 Dataset](https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html)
+ [PoseTrack](https://posetrack.net/)

#### Inria 3d Movie Dataset

1. Download the disparity video frames directly from [here](https://www.di.ens.fr/willow/research/stereoseg/dataset/inria_stereo_dataset_video_segmentation_disparity.tar.gz).
2. Get the segmentation masks from ...

#### NYU2 Dataset

1. Download the labeled dataset directly from [here](http://horatio.cs.nyu.edu/mit/silberman/nyu_depth_v2/nyu_depth_v2_labeled.mat).


### Configure ```config.json```
You can check the wiki to have a good documentation about all possible values in each field.

### Run the training script
After that, you can simply run the training script: ```python train.py```

## Testing on our pre-trained model (or on your own trained weights)
Put your input images (that have to be ```.png``` or ```.jpg```) into the ```input/``` folder. Then, just run ```python run.py``` and you should get the depth maps as well as the segmentation masks in the ```output/``` folder.

After that, you need to update the ```config_run.json``` according to the pre-trained model.

### Model zoo

Get the links of the following models:

+ [```vit_base_patch16_384```](https://drive.google.com/file/d/1Q7I777FW_dz5p5UlMsD6aktWQ1eyR1vN/view?usp=sharing)
+ Other models coming soon...

And put the ```.p``` file into the directory ```models/```


