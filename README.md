### Recommended Environment:
python==3.9<br>
torch==2.0.1+cu118<br>
numpy=1.19<br>
opencv-python==4.9.0.80<br>
pillow==10.2.0<br>
PyYAML==6.0.1<br>
pandas==2.2.2<br>
## Datasets
Each image corresponds to one *.txt file, formatted as `class x_center y_center width height`.
### Dataset configuration format
```
path: ../datasets/data # dataset root dir
train: images/train # train images (relative to 'path') 2700 images
val: images/val # val images (relative to 'path') 300 images
test:  # 

# Classes
names:
  0: gczywzqpdaqd
  1: tszywrft
  2: zyxckdwzg
  3: wgfzz
  4: kyhxcaqwl
```
```
-datasets/
  -data/
    -images/
      -train/
      -test/
      -val/
    -labels/
      -train/
      -test/
      -val/
```
### __To train__:
```
yolo detect train data=dianwang.yaml model=yolov10nx.yaml epochs=500 batch=256 imgsz=640 device=0
```
### Or
```
from ultralytics import YOLOv10
model = YOLOv10('yolov10x.pt')
model.train(data='dianwang.yaml', epochs=500, batch=16, imgsz=640, device=0)
```

### To test:
```
from ultralytics import YOLOv10

# model = YOLOv10.from_pretrained('./yolov10x')
model = YOLOv10('./runs/detect/train/weights/best.pt')
source = './datasets/data/images/val'
model.predict(source=source, save=True)
```
