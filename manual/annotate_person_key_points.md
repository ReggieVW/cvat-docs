# Automatic annotation with person key points

See page [automatic_annotations](https://github.com/ReggieVW/cvat-docs/blob/main/manual/automatic_annotations.md#automatic-annotation-person-body-key-points).


# Manual annotation with person key points
<b>Note: This can only be executed after task [automatic annotation person key points](#automatic-annotation-with-person-key-points) is executed.</b>

You can drag a point and change the position of individual points. Move the points to the desired position. 

## Shape grouping
Pre-annotated points are automatically grouped — all points with the same colour are linked to a certain person.
![image](https://user-images.githubusercontent.com/35894891/171384083-5e061097-691f-47a4-a970-9bcab0ddb7a9.png)


## Swith on/off the keyframe
You can switch off the keyframe so intermediate frames will be drawn automatically. Interpolation will be used.
![image](https://user-images.githubusercontent.com/35894891/171388737-3f40bbee-b661-497f-9c81-f97362fcf781.png)

Interpolation can be used when there are key-points of two persons that intermingle for a few frames and manually correction is to cumbersome. 
![image](https://user-images.githubusercontent.com/35894891/180450542-465abc43-e065-4fde-8572-11272fa56eaf.png)

# Export person key points
<b>Note: the feature of directly exporting person key points with JSON is not available in CVAT. The JSON file also does not export the group_id which is necessary to group the person keypoints.</b>

First click on save because CVAT does not automatically saves the changes. Then click "Menu" in CVAT. Click "Export task dataset" and choose "CVAT for video".
![image](https://user-images.githubusercontent.com/35894891/199825605-7ba58ca2-a341-4a23-bf56-709243d1f34e.png)

Convert the CVAT XML into JSON. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils

```
python cvatxml2coco.py --cvat-xml annotations.xml --coco-json person_keypoints_coco.json
```

 
