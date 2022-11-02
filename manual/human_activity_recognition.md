# Human activity recognition

## Add action to person bounding box 

You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class labels of the objects that you would like to detect. Carefully specify these. Notice that the variable "Mutable" is set to true. Mutable attributes may be changed frame by frame. Click on "Done".

![image](https://user-images.githubusercontent.com/35894891/199530755-a2ae7b7c-0c72-4fc7-ad0d-0c1627a369a8.png)

```
[
  {
    "name": "person",
    "attributes": [
      {
        "name": "action",
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

Now you can draw person bounding boxes and specify the action.
![image](https://user-images.githubusercontent.com/35894891/199532868-8cd52e27-568e-4ade-ba1f-590068027738.png)
