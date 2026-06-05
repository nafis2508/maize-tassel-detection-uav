# Dataset

UAV imagery of maize fields with tassel bounding-box annotations.

## Splits
- Train: 733 images
- Validation: 205 images
- Test: 30 images

## Structure
data/ ├── raw/ │ ├── images/{train,val,test}/.jpg │ └── labels/{train,val,test}/.txt # YOLO format └── processed/ # Optional: resized/augmented


## Obtaining the data
Contact the maintainers, or place your own UAV maize imagery here and follow the same folder layout.