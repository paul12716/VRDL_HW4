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

2. download the datasets from https://drive.google.com/drive/folders/1H-sIY7zj42Fex1ZjxxSC3PV1pK4Mij6x. And make sure that 
```bash
# Train a new model starting from ImageNet weights.  
# We use HW3's train_images as our dataset.  
python3 samples/coco/coco.py train --dataset=/path/to/train_images/ --model=imagenet

# Continue training the last model you trained. This will find the last trained weights in the model directory.
python3 samples/coco/coco.py train --dataset=/path/to/train_images/ --model=last
```

In coco.py, we preprocess the data and train our model.  
The model's weights will be saved every single epoch in logs/

## Output test.json by running test.py

```bach
python test.py
```

For testing data, we first load the test.json.
```python
cocoGt = COCO("../test.json")
```
Then we import the saved model.
```python
model = modellib.MaskRCNN(mode="inference", config=config, model_dir='logs/')
model_path = model.find_last()
model.load_weights(model_path, by_name=True)
```
After predicting results, we transform the output to perpare the submission.json file.  
In the end, write 'image_id', 'category_id', 'segmentation' and 'score' result to a submission.josn file.  
Upload google drive submission.  
Best accuracy : mAP : 0.47644.  
