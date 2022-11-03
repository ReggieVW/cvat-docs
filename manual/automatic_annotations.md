- [User's guide]
    - [Automatic annotation person bounding boxes](#automatic-annotation-person-bounding-boxes)
       - YOLO-v5 and Person reidentification 
       - Tracking using SiamMask
    - [Automatic annotation person key points](#automatic-annotation-person-key-points)
        - HRNET

CVAT is also optimized for automatic annotation that can help you speed up the process significantly. 

To use CVAT’s AI tools, you need the corresponding deep learning models to be available in the models’ section. 
![image](https://user-images.githubusercontent.com/35894891/199738807-349c4230-6a25-4215-ae4c-0ca1324b3fa6.png)

<b>Note: the default models provided (for e.g., Person reidentification & SiamMask) are often not well trained. Try to use other models instead. </b>

# Automatic annotation Person bounding boxes

## YOLO-v5 and Person reidentification

To launch automatic annotation, you should open the dashboard and find a task which you want to annotate. Then click the ``Actions`` button and choose option ``Automatic Annotation`` from the dropdown menu.
![image](https://user-images.githubusercontent.com/35894891/199705706-3517dd36-58d0-46e0-98fb-33fd66b579bb.png)

In the dialog window select a model you need. DL models are created for specific labels. Adjust the labels so that the task labels will correspond to the labels of the DL model. For example, consider a task where you have to annotate labels ``person``. You should connect the ``person`` label from the model to the ``person`` label in the task. Click ``Submit`` to begin the automatic annotation process. Supported models, such as YOLO-v5, are suitable only for specific labels (for e.g. person). 

<img src="https://user-images.githubusercontent.com/35894891/176120074-2e87da94-dc6f-4f37-855e-0822cf93ad62.png" width="600" height="400" />

You can combine separate bounding boxes into tracks using the ``Person reidentification model``. To do this, click on the ``Automatic annotation`` item in the action menu again and select the model of the ReID type (in this case the Person reidentification model). You can set the following parameters:
- ``Model Threshold`` is a maximum cosine distance between objects’ embeddings.
- ``Maximum distance`` defines a maximum radius that an object can diverge between adjacent frames.

<img src="https://user-images.githubusercontent.com/35894891/176121237-5a16cbb3-2421-4f46-9440-9108aee75d53.png"/>

The end result of the automatic annotation is an annotation with person bounding boxes.
![image](https://user-images.githubusercontent.com/35894891/199706050-77161b5e-3c6c-495c-ad89-a6d2cc5cb2c1.png)

## Tracking using SiamMask
Open the task and use AI tools to start tracking an object. Draw a bounding box around an object, and sequentially switch through the frame. Labeled objects are automatically tracked when you move to the next frame. 

<img src="https://user-images.githubusercontent.com/35894891/176134413-011a325d-f398-4890-9fd8-9aaeef26c1cf.png"/>

![image](https://user-images.githubusercontent.com/35894891/176135289-b39dbab7-17ad-4754-9f96-44ac1eccb634.png)


# Automatic annotation person key points 
<b>Note: This task can only be executed after the annotation of the bounding boxes is done. </b>

## HRNET
HRNET is a human pose estimation algorithm. HRNet uses the top-down method, the algorithm is built for estimating person key points based on bounding boxes

### Add automatic key points to person bounding box annotations
<b>Note:This model is not included yet into the CVAT’s AI tools. So the process requires manual intervention. Also the feature of directly importing person key points with JSON is not available in CVAT.</b>

First click ``Menu`` in CVAT. Click ``Export task dataset`` and choose ``COCO``.

![image](https://user-images.githubusercontent.com/35894891/199809798-002be189-31ae-43a4-a2c9-9a338096c828.png)

Add the automatic generated body key points by executing following script. Further information about the tool and installation https://github.com/ReggieVW/mmpose 
```
python top_down_pose_tracking_input.py configs/body/2d_kpt_sview_rgb_img/topdown_heatmap/coco/hrnet_w48_coco_384x288_udp.py https://download.openmmlab.com/mmpose/top_down/udp/hrnet_w48_coco_384x288_udp-0f89c63e_20210223.pth --video-path <FILE> --out-video-root vis_results --input-json-path person_bbox_coco.json --output-json-path person_keypoints_coco.json
```
Convert the JSON back into CVAT XML. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils
```
python coco2cvatxml.py --coco-json person_keypoints_coco.json --cvat-xml annotations.xml --with-personkeypoints
```

You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class labels of the objects that you would like to use. Carefully specify these.
![image](https://user-images.githubusercontent.com/35894891/199746800-4e78f427-6cd2-44ae-8b08-f82c545558ca.png)

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
Click ``Upload annotations`` and then choose ``CVAT`` to upload the XML.

![image](https://user-images.githubusercontent.com/35894891/199748628-e78d275a-19e1-48ee-a70a-85118df59c70.png)


The end result of the automatic annotation is an annotation with bounding boxes with person key points.
![image](https://user-images.githubusercontent.com/35894891/199747631-9efb99cd-6069-4fb1-abb5-2b9c427bdf9c.png)

Click on group to view each person in a different colour.

![image](https://user-images.githubusercontent.com/35894891/199750231-fdc97f87-9a78-4f78-babc-50658a31d282.png)

![image](https://user-images.githubusercontent.com/35894891/199750054-90d94047-0329-4454-8787-8c2c1cb29426.png)

Note: The quantity of the persons can be demanding on the processing power. This feature is normally used for only tracking the key points of the actors (i.e. person in an action or process)



