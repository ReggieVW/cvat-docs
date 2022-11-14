- [User's guide for the Surv-AI-llance project](../README.md)</br>
  - [Human activity recognition]</br>
        - [Add activity to person bounding box](#add-activity-to-person-bounding-box)</br>
        - [Add activity as dummy object to a person bounding box](#add-activity-as-dummy-object-to-a-person-bounding-box)</br>

# Human activity recognition

## Add activity to person bounding box 

You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class ``labels`` of the objects that you would like to detect. 

![image](https://user-images.githubusercontent.com/35894891/199858465-8ed36a86-d373-4401-97dd-b752c2cbd54c.png)
Carefully specify these using the ``Raw`` option. Notice that the variable ``Mutable`` is set to true. Mutable attributes may be changed frame by frame. Click on ``Done``.

```
[
  {
    "name": "person",
    "attributes": [
      {
        "name": "activity",
        "input_type": "select",
        "mutable": true,
        "values": [
          "no action",
          "Fainting and falling",
          "Kicking other person",
          "Punching other person",
          "Pushing other person",
          "Throwing objects"
        ]
      }
    ]
  }
]
```

The result in the ``Constructor`` tab will be similar to this.

![image](https://user-images.githubusercontent.com/35894891/201056811-c3a9a233-4ee7-4b3e-b855-83f07f4ba206.png)


Now you can draw person bounding boxes and specify the activity.
![image](https://user-images.githubusercontent.com/35894891/199813921-76f232d4-b9c5-4540-a2e8-a23028d62eb3.png)

## Add activity as dummy object to a person bounding box
There is a bypass available to decouple the keyframe of the attribute activity from the keyframe of the person bounding box. <b>This is done after the creation of all the bounding boxes </b>.

First click Menu in CVAT. Click Export task dataset and choose COCO.
![image](https://user-images.githubusercontent.com/35894891/201472815-4b160644-cb7a-46a4-87f7-fd437d86ccdd.png)
Add the dummy objects by executing following script. Further information about the tool and installation https://github.com/ReggieVW/cvat-utils
```
python coco2cvatxml.py --coco-json coco.json --cvat-xml annotations.xml --with-dummyobject-activity
```
You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class ``labels`` of the objects that you would like to detect. 
![image](https://user-images.githubusercontent.com/35894891/201473264-f5ebfbb7-125c-43e0-920f-98515747d573.png)
You can to specify the class labels of the objects that you would like to use. Carefully specify these using the ``Raw`` option. 

```
[
  {
    "name": "person",
    "color": "#fa3253",
    "type": "any",
    "attributes": [
      {
        "name": "orig_track_id",
        "input_type": "text",
        "mutable": false,
        "values": [""]
      }
    ]
  },
  {
    "name": "activity",
    "color": "#3d3df5",
    "type": "any",
    "attributes": [
      {
        "name": "activity",
        "input_type": "select",
        "mutable": true,
        "values": [
          "no action",
          "Fainting and falling",
          "Kicking other person",
          "Punching other person",
          "Pushing other person",
          "Throwing objects"
        ],
        "default_value": "no action"
      },
      {
        "name": "orig_track_id",
        "input_type": "text",
        "mutable": false,
        "values": [""]
      }
    ]
  }
]
```
The result in the ``Constructor`` tab, the ``Dummy`` object will be similar to this.

![image](https://user-images.githubusercontent.com/35894891/201473305-e7b6e543-a544-4d2e-8f89-cfff3c6812f2.png)

To upload the annotations, you can click the ``Actions`` button and choose option ``Upload annotations`` from the dropdown menu. Then choose ``CVAT`` to upload the XML.

![image](https://user-images.githubusercontent.com/35894891/201473486-1dca4185-0638-4268-813a-3814a316bfb3.png)

The end result of adding the ``Dummy`` object is an annotation with an activity object connected to a person bounding box by group. Click on ``Group`` to view each person with his connected activity object in a different colour.

![image](https://user-images.githubusercontent.com/35894891/201474221-117fcc36-e03e-442d-a8a2-fd4b31c18677.png)

Note: To have the results in COCO format and not loose the activity annotations you have to first export to CVAT and then convert to COCO using the following script.

```
python cvatxml2coco.py --cvat-xml annotations.xml --coco-json coco.json --with-dummyobject-activity
```






