# Austrian Traffic Sign Detection using YOLO-V8

## Project Overview
This project implements a traffic sign detection system for Austrian traffic signs using YOLO-V8. The model detects and classifies traffic signs into 8 categories from the Austrian Traffic Sign Dataset (ATSD).

## Dataset
The dataset contains 5,346 images of Austrian traffic signs split into:
- Train: 75%
- Validation: 25%
- Test: Held-out set

### Categories:
1. Prohibitory
2. Danger
3. Priority
4. Mandatory
5. Special
6. Lane
7. Additional panel
8. Inactive

## Model Architecture
**YOLO-V8n** with these specifications:
- Input size: 1024x1024
- Batch size: 32
- Optimizer: AdamW
- Learning rate: 0.001 (cosine schedule)
- Weight decay: 0.00005

### Augmentations:
- Mosaic
- Random flips
- HSV adjustments

## Training
Two-phase training:
1. First checkpoint: 40 epochs
2. Second checkpoint: +30 epochs (70 total)

## Performance
### Validation:
- mAP@0.5: 0.834
- mAP@0.5-0.95: 0.634
- Speed: 4.9ms/image

### Test:
- mAP@0.5: 0.831
- mAP@0.5-0.95: 0.631
- Speed: 5.0ms/image

## Usage
### Training:
```python
model = YOLO('yolov8n.pt')
results = model.train(
    data='Yolo_train.yaml',
    epochs=40,
    imgsz=1024,
    batch=32
)
