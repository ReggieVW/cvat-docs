[User's guide for the Surv-AI-llance project](https://github.com/ReggieVW/cvat-docs)

# Human activity recognition

## Add activity to person bounding box 

You can launch a new task in CVAT and drag your video in for labeling. You are also prompted to specify the class ``labels`` of the objects that you would like to detect. 

![image](https://user-images.githubusercontent.com/35894891/199858465-8ed36a86-d373-4401-97dd-b752c2cbd54c.png)
Carefully specify these. Notice that the variable ``Mutable`` is set to true. Mutable attributes may be changed frame by frame. Click on ``Done``.

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

Now you can draw person bounding boxes and specify the activity.
![image](https://user-images.githubusercontent.com/35894891/199813921-76f232d4-b9c5-4540-a2e8-a23028d62eb3.png)
