# VRDL_HW4

code for Selected Topics in Visual Recognition using Deep Learning Homework 4

## Hardware

- Ubuntu 16.04 LTS
- NVIDIA 1080ti

## Requirements
- Python 3 (Anaconda is recommended)
- skimage
- imageio
- Pytorch (Pytorch version >=0.4.1 is recommended)
- tqdm
- pandas
- cv2 (pip install opencv-python)
- Matlab

## Training

1. Clone this repository

2. download the datasets from https://drive.google.com/drive/folders/1H-sIY7zj42Fex1ZjxxSC3PV1pK4Mij6x.  

3. Run ***./scripts/Prepare_TrainData_HR_LR.m*** in Matlab to generate HR/LR training pairs with corresponding degradation model and scale factor.

4. Edit ***./options/train/train_SRFBN_example.json*** for your needs.

5. Then, run command:
```bash
python train.py -opt options/train/train_SRFBN_example.json
```

6. The model weights will be saved in ***./experiments***

## Testing

1. Edit ***./options/test/test_SRFBN_example.json*** for your needs.

2. Run command:
```bash
python test.py -opt options/test/test_SRFBN_example.json
```

Upload the output images into the google drive and compute psnr.
Best psnr : 25.922.  
