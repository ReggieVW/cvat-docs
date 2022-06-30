# Human activity recognition

## Add actions to person bounding box annotations (after annotations body bounding boxes)

Remark: This task can only be executed after task [annotation body bounding boxes](https://github.com/ReggieVW/cvat-docs/blob/main/manual/annotate_bbox.md) is executed.

You first click on "Save". Then click "Menu", in CVAT. Click "Export task dataset" and choose "CVAT for video".

<img src="https://user-images.githubusercontent.com/35894891/176140939-559e8601-32a8-4c90-ad14-616d2e6ebd37.png" width="400" height="400" />

<img src="https://user-images.githubusercontent.com/35894891/176141285-82bc5ad4-ef06-4bef-a43b-c2ca4cc567a3.png" width="600" height="400" />

Convert the CVAT XML into JSON. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils

```
python cvatxml2coco.py --cvat-xml annotations.xml --coco coco.json 
```
Add the action boxes by executing following script. 
```
python coco2cvatxml.py --coco coco_actions.json --cvat-xml annotations_actions.xml --withDummyAction
```
You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class labels of the objects that you would like to detect. Carefully specify these.

![image](https://user-images.githubusercontent.com/35894891/176632885-0f102585-6407-44e4-b206-879abcf47448.png)


[
  {
    "name": "person",
    "color": "#c06060",
    "attributes": []
  },
  {
    "name": "Actions",
    "color": "#c06060",
    "attributes": [
      {
        "name": "Daily Actions",
        "input_type": "select",
        "mutable": true,
        "values": [
          "no action",
          "arm swings",
          "butt kicks",
          "counting money",
          "kicking something",
          "open a box",
          "pick up",
          "put object into bag",
          "put on bag",
          "reach into pocket",
          "shake fist",
          "side kick",
          "sit down",
          "stand up",
          "take object out of bag",
          "take off bag",
          "throw"
        ]
      },
      {
        "name": "Mutual Actions",
        "input_type": "select",
        "mutable": true,
        "values": [
          "no action",
          "carry something with other person",
          "exchange things",
          "follow other person",
          "giving something to other person",
          "grab other person’s stuff",
          "hit other person with something",
          "kicking other person",
          "knock over other person (hit with body)",
          "punching/slapping other person",
          "pushing other person",
          "shoot with gun",
          "step on foot",
          "touch other person's pocket",
          "wield knife towards other person"
        ]
      },
      {
        "name": "Medical Conditions",
        "input_type": "select",
        "mutable": true,
        "values": [
          "no action",
          "chest pain",
          "falling down"
        ]
      }
    ]
  }
]

Click "Upload annotations" and then choose "CVAT" to upload the XML.
![image](https://user-images.githubusercontent.com/35894891/176633357-00a4b88c-dd4e-48f8-bc69-cd473d60d78d.png)
The end result of an automatic annotation is an annotation with bounding boxes with body keypoints.
![image](https://user-images.githubusercontent.com/35894891/176633566-7c63796f-9502-4031-999a-fed6ff4a8d3c.png)
