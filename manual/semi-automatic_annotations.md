# semi-automatic annotation body bounding boxes

## YOLO-v5 and Person reidentification
CVAT is also optimized for semi-automatic annotation that can help you speed up the process significantly. 

To use CVAT’s AI tools, you need the corresponding deep learning models to be available in the models’ section. 
<img src="https://user-images.githubusercontent.com/35894891/176121952-d8c05dac-a788-4072-8655-8130ad8d4df4.png" width="800" height="400" />

To launch automatic annotation, you should open the dashboard and find a task which you want to annotate. Then click the Actions button and choose option Automatic Annotation from the dropdown menu.

<img src="https://user-images.githubusercontent.com/35894891/176123597-e69e69a3-1e85-4656-b7f9-674574b12745.png" width="800" height="400" />

In the dialog window select a model you need. DL models are created for specific labels. Adjust the labels so that the task labels will correspond to the labels of the DL model. For example, consider a task where you have to annotate labels “person”. You should connect the “person” label from the model to the “person” label in the task. Click Submit to begin the automatic annotation process. Supported models, such as YOLO-v5, are suitable only for specific labels (for e.g. person). 

<img src="https://user-images.githubusercontent.com/35894891/176120074-2e87da94-dc6f-4f37-855e-0822cf93ad62.png" width="600" height="400" />

You can combine separate bounding boxes into tracks using the Person reidentification model. To do this, click on the automatic annotation item in the action menu again and select the model of the ReID type (in this case the Person reidentification model). You can set the following parameters:
- Model Threshold is a maximum cosine distance between objects’ embeddings.
- Maximum distance defines a maximum radius that an object can diverge between adjacent frames.

<img src="https://user-images.githubusercontent.com/35894891/176121237-5a16cbb3-2421-4f46-9440-9108aee75d53.png" width="600" height="400" />

The end result of an automatic annotation is an annotation with separate bounding boxes.
<img src="https://user-images.githubusercontent.com/35894891/176129602-e34617b8-e628-4809-9487-e9602f09d237.png" width="800" height="400" />

## Tracking using SiamMask
Open the task and use AI tools to start tracking an object. Draw a bounding box around an object, and sequentially switch through the frame and correct the restrictive box if necessary. Labeled objects are automatically tracked when you move to the next frame. 

<img src="https://user-images.githubusercontent.com/35894891/176134413-011a325d-f398-4890-9fd8-9aaeef26c1cf.png" width="600" height="400" />

![image](https://user-images.githubusercontent.com/35894891/176135289-b39dbab7-17ad-4754-9f96-44ac1eccb634.png)


# semi-automatic annotation body keypoints
## HRNET
HRNET is a state-of-the-art algorithm human pose estimation. HRNet uses the top-down method, the network is built for estimating key points based on person bounding boxes

## Add automatic body keypoints to person bounding box annotations (after annotations body bounding boxes)
Remark: This task can only be executed after task annotation body bounding boxes is executed.

You first want to click "Save". CVAT does not automatically save work. Then click "Menu", in CVAT. Click "Export task dataset" and choose "CVAT for video".

<img src="https://user-images.githubusercontent.com/35894891/176140939-559e8601-32a8-4c90-ad14-616d2e6ebd37.png" width="400" height="400" />

<img src="https://user-images.githubusercontent.com/35894891/176141285-82bc5ad4-ef06-4bef-a43b-c2ca4cc567a3.png" width="600" height="400" />

Convert the CVAT XML into JSON. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils

```
python cvatxml2coco.py --cvat-xml annotations.xml --coco coco.json 
```
Add the body keypoints by executing following script. 
```
python top_down_pose_tracking_input.py configs/body/2d_kpt_sview_rgb_img/topdown_heatmap/coco/hrnet_w48_coco_384x288_udp.py https://download.openmmlab.com/mmpose/top_down/udp/hrnet_w48_coco_384x288_udp-0f89c63e_20210223.pth --video-path <FILEPATH> --out-video-root vis_results --json-path coco.json
```
Convert the JSON into CVAT XML.
```
python coco2cvatxml.py --coco data.json --cvat-xml annotations.xml --withBodyKeyPoints
```
You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class labels of the objects that you would like to detect. Carefully specify these.
```
[
  {
    "name": "left_shoulder",
    "id": 7,
    "color": "#33ddff",
    "attributes": []
  },
  {
    "name": "right_shoulder",
    "id": 8,
    "color": "#83e070",
    "attributes": []
  },
  {
    "name": "right_elbow",
    "id": 9,
    "color": "#ff007c",
    "attributes": []
  },
  {
    "name": "left_wrist",
    "id": 10,
    "color": "#ff6037",
    "attributes": []
  },
  {
    "name": "right_wrist",
    "id": 11,
    "color": "#ddff33",
    "attributes": []
  },
  {
    "name": "left_hip",
    "id": 12,
    "color": "#24b353",
    "attributes": []
  },
  {
    "name": "right_hip",
    "id": 13,
    "color": "#b83df5",
    "attributes": []
  },
  {
    "name": "left_knee",
    "id": 14,
    "color": "#66ff66",
    "attributes": []
  },
  {
    "name": "right_knee",
    "id": 15,
    "color": "#32b7fa",
    "attributes": []
  },
  {
    "name": "left_ankle",
    "id": 16,
    "color": "#ffcc33",
    "attributes": []
  },
  {
    "name": "right_ankle",
    "id": 17,
    "color": "#83e070",
    "attributes": []
  },
  {
    "name": "nose",
    "id": 18,
    "color": "#fafa37",
    "attributes": []
  },
  {
    "name": "left_elbow",
    "id": 19,
    "color": "#8c78f0",
    "attributes": []
  },
  {
    "name": "person",
    "id": 20,
    "color": "#fa3253",
    "attributes": []
  }
]
```
Click "Upload annotations" and then choose "CVAT" to upload the XML.

## Shape grouping
Points are automatically grouped — all points with the same colour are linked to a certain person.
![image](https://user-images.githubusercontent.com/35894891/171384083-5e061097-691f-47a4-a970-9bcab0ddb7a9.png)

## Annotation with points
You can drag a point and change the position of individual points. Move the point to the desired position, this way you will create a keyframe. You can hide it using the Outside, move around, etc.

![image](https://user-images.githubusercontent.com/35894891/171391600-7cb5d041-0558-4155-842c-860ae18ec5f2.png)

## Swith on/off the keyframe
You can swith of the keyframe so intermediate frames will be drawn automatically.
![image](https://user-images.githubusercontent.com/35894891/171388737-3f40bbee-b661-497f-9c81-f97362fcf781.png)



