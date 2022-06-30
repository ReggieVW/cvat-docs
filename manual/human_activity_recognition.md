# Human activity recognition

## Add actions to person bounding box annotations (after annotations body bounding boxes)

Remark: This task can only be executed after task annotation body bounding boxes is executed.

You first click on "Save". CVAT does not automatically save work. Then click "Menu", in CVAT. Click "Export task dataset" and choose "CVAT for video".

<img src="https://user-images.githubusercontent.com/35894891/176140939-559e8601-32a8-4c90-ad14-616d2e6ebd37.png" width="400" height="400" />

<img src="https://user-images.githubusercontent.com/35894891/176141285-82bc5ad4-ef06-4bef-a43b-c2ca4cc567a3.png" width="600" height="400" />

Convert the CVAT XML into JSON. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils

```
python cvatxml2coco.py --cvat-xml annotations.xml --coco coco.json 

```
Add the action boxes by executing following script. 
```
