- [User's guide]
    - [Automatic annotation person bounding boxes](#automatic-annotation-person-bounding-boxes)
       - YOLO-v5 and Person reidentification 
       - Tracking using SiamMask
    - [Automatic annotation person body keypoints](#automatic-annotation-person-body-keypoints)
        - HRNET

CVAT is also optimized for automatic annotation that can help you speed up the process significantly. 

To use CVAT’s AI tools, you need the corresponding deep learning models to be available in the models’ section. 
<img src="https://user-images.githubusercontent.com/35894891/176121952-d8c05dac-a788-4072-8655-8130ad8d4df4.png"/>

<b>Note: the default models provided (for e.g., Person reidentification & SiamMask) are often not well trained. Try to use other models instead. </b>

# Automatic annotation Person bounding boxes

## YOLO-v5 and Person reidentification

To launch automatic annotation, you should open the dashboard and find a task which you want to annotate. Then click the Actions button and choose option 'Automatic Annotation' from the dropdown menu.
![image](https://user-images.githubusercontent.com/35894891/199705706-3517dd36-58d0-46e0-98fb-33fd66b579bb.png)

In the dialog window select a model you need. DL models are created for specific labels. Adjust the labels so that the task labels will correspond to the labels of the DL model. For example, consider a task where you have to annotate labels “person”. You should connect the “person” label from the model to the “person” label in the task. Click Submit to begin the automatic annotation process. Supported models, such as YOLO-v5, are suitable only for specific labels (for e.g. person). 

<img src="https://user-images.githubusercontent.com/35894891/176120074-2e87da94-dc6f-4f37-855e-0822cf93ad62.png" width="600" height="400" />

You can combine separate bounding boxes into tracks using the Person reidentification model. To do this, click on the automatic annotation item in the action menu again and select the model of the ReID type (in this case the Person reidentification model). You can set the following parameters:
- Model Threshold is a maximum cosine distance between objects’ embeddings.
- Maximum distance defines a maximum radius that an object can diverge between adjacent frames.

<img src="https://user-images.githubusercontent.com/35894891/176121237-5a16cbb3-2421-4f46-9440-9108aee75d53.png"/>

The end result of the automatic annotation is an annotation with person bounding boxes.
![image](https://user-images.githubusercontent.com/35894891/199706050-77161b5e-3c6c-495c-ad89-a6d2cc5cb2c1.png)

## Tracking using SiamMask
Open the task and use AI tools to start tracking an object. Draw a bounding box around an object, and sequentially switch through the frame. Labeled objects are automatically tracked when you move to the next frame. 

<img src="https://user-images.githubusercontent.com/35894891/176134413-011a325d-f398-4890-9fd8-9aaeef26c1cf.png"/>

![image](https://user-images.githubusercontent.com/35894891/176135289-b39dbab7-17ad-4754-9f96-44ac1eccb634.png)


# Automatic annotation person keypoints 
<b>Note: This task can only be executed after the annotation of the bounding boxes is done. </b>

## HRNET
HRNET is a human pose estimation algorithm. HRNet uses the top-down method, the algorithm is built for estimating key points based on person bounding boxes

### Add automatic keypoints to person bounding box annotations

You first want to click "Save". CVAT does not automatically save work. Then click "Menu", in CVAT. Click "Export task dataset" and choose "CVAT for video".

<img src="https://user-images.githubusercontent.com/35894891/176140939-559e8601-32a8-4c90-ad14-616d2e6ebd37.png" width="400" height="400" />

<img src="https://user-images.githubusercontent.com/35894891/176141285-82bc5ad4-ef06-4bef-a43b-c2ca4cc567a3.png" width="600" height="400" />

Convert the CVAT XML into JSON. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils

```
python cvatxml2coco.py --cvat-xml annotations.xml --coco coco.json --onlyBoxes
```
Add the automatic generated body keypoints by executing following script. Further information about the tool and installation https://github.com/ReggieVW/mmpose 
```
python top_down_pose_tracking_input.py configs/body/2d_kpt_sview_rgb_img/topdown_heatmap/coco/hrnet_w48_coco_384x288_udp.py https://download.openmmlab.com/mmpose/top_down/udp/hrnet_w48_coco_384x288_udp-0f89c63e_20210223.pth --video-path <FILEPATH> --out-video-root vis_results --json-path coco.json
```
Convert the JSON into CVAT XML.
```
python coco2cvatxml.py --coco data.json --cvat-xml annotations.xml --withBodyKeyPoints
```
You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class labels of the objects that you would like to detect. Carefully specify these.
![image](https://user-images.githubusercontent.com/35894891/176416947-b5201edc-f577-4f0c-a025-9f5ef712c4f4.png)

```
[
  {
    "name": "left_shoulder",
    "id": 157,
    "color": "#fafa37",
    "attributes": []
  },
  {
    "name": "right_shoulder",
    "id": 158,
    "color": "#33ddff",
    "attributes": []
  },
  {
    "name": "right_elbow",
    "id": 159,
    "color": "#33ddff",
    "attributes": []
  },
  {
    "name": "left_wrist",
    "id": 160,
    "color": "#fafa37",
    "attributes": []
  },
  {
    "name": "right_wrist",
    "id": 161,
    "color": "#33ddff",
    "attributes": []
  },
  {
    "name": "left_hip",
    "id": 162,
    "color": "#24b353",
    "attributes": []
  },
  {
    "name": "right_hip",
    "id": 163,
    "color": "#2a7dd1",
    "attributes": []
  },
  {
    "name": "left_knee",
    "id": 164,
    "color": "#24b353",
    "attributes": []
  },
  {
    "name": "right_knee",
    "id": 165,
    "color": "#3d3df5",
    "attributes": []
  },
  {
    "name": "left_ankle",
    "id": 166,
    "color": "#24b353",
    "attributes": []
  },
  {
    "name": "right_ankle",
    "id": 167,
    "color": "#3d3df5",
    "attributes": []
  },
  {
    "name": "nose",
    "id": 168,
    "color": "#ff00cc",
    "attributes": []
  },
  {
    "name": "left_elbow",
    "id": 169,
    "color": "#fafa37",
    "attributes": []
  },
  {
    "name": "left_eye",
    "id": 170,
    "color": "#ff007c",
    "attributes": []
  },
  {
    "name": "right_eye",
    "id": 171,
    "color": "#ff007c",
    "attributes": []
  },
  {
    "name": "left_ear",
    "id": 172,
    "color": "#ff00cc",
    "attributes": []
  },
  {
    "name": "right_ear",
    "id": 173,
    "color": "#ff355e",
    "attributes": []
  },
  {
    "name": "person",
    "id": 174,
    "color": "#fa3253",
    "attributes": []
  }
]
```
Click "Upload annotations" and then choose "CVAT" to upload the XML.

![image](https://user-images.githubusercontent.com/35894891/176418506-08208283-7fcc-404d-b73b-54b76ceb4dfb.png)


The end result of an automatic annotation is an annotation with bounding boxes with body keypoints.
![image](https://user-images.githubusercontent.com/35894891/176415761-ffcf3c86-be88-418a-affa-de74da49c7b5.png)


