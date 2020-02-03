# Training Yolo Model using Darknet

## Project Configuration

- darknet
    
    Framework downloaded to https://github.com/pjreddie/darknet
    
    There is no custom_data directory, yolov3.weights and darkenet53.conv.74 file in initial framework.
    
    We should make custom_data directory and download weights and conv file.
    
- training_dataset
    
    Annotated dataset with images and xmls
    
- utils
    
    Several functions to prepare for training dataset

## Main reference site

    https://blog.francium.tech/custom-object-training-and-detection-with-yolov3-darknet-and-opencv-41542f2ff44e
    
## Notes to follow this site
    
- Structure of custom_data directory

    There is no labels directory in custom_data directory shown in this site.
    
    But if there is not a labels directory, we can meet error while performing train. So after making labels directory, we must put text files in it.
    
- No instruction about usage of GPU
    
    If we want to use GPU instead of CPU, we must modify configuration file before training.
    Please refer as following:
    
    1. Edit Makefile GPU=1
    2. Edit Makefile CUDNN=1
    3. Leave Makefile OPENCV=0
    4. Install re-install CUDA using pip (my advice is to use version 10.1)
    5. Edit Makefile NVCC=/usr/local/cuda/bin/nvcc (failure to do this will result in a recipe for target 'obj/convolutional_kernels.o' error during compilation)
    6. Compile (or recompile if you previously compiled) the Darknet binary build via admin privileges -- SUDO

    Also we must modify batch size of yolov3-custom.config in custom_data/cfg according to image size.
    Following reference site, we may set batch size 64, but in our case, there happened an out of memory issue while training.
    After modifying it 32, we could perform train well.
