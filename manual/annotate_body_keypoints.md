# Automatic annotation with person body keypoints

See page [automatic_annotations](https://github.com/ReggieVW/cvat-docs/blob/main/manual/automatic_annotations.md#automatic-annotation-person-body-keypoints).

The result of an automatic annotation is an annotation with bounding boxes and body keypoints.
![image](https://user-images.githubusercontent.com/35894891/176415761-ffcf3c86-be88-418a-affa-de74da49c7b5.png)

# Manual annotation with points
Remark: This can only be executed after task [automatic annotation person body keypoints](#automatic-annotation-with-person-body-keypoints) is executed.

You can drag a point and change the position of individual points. Move the point to the desired position, this way you will create a keyframe.

## Outside Property
When the annotated object disappears, you have to choose Outside Property (see picture below)

![image](https://user-images.githubusercontent.com/35894891/171391600-7cb5d041-0558-4155-842c-860ae18ec5f2.png)

## Shape grouping
Points are automatically grouped — all points with the same colour are linked to a certain person.
![image](https://user-images.githubusercontent.com/35894891/171384083-5e061097-691f-47a4-a970-9bcab0ddb7a9.png)


## Swith on/off the keyframe
You can switch of the keyframe so intermediate frames will be drawn automatically. Interpolation will be used.
![image](https://user-images.githubusercontent.com/35894891/171388737-3f40bbee-b661-497f-9c81-f97362fcf781.png)
 
