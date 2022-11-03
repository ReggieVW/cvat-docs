# Automatic annotation with person key points

See page [automatic_annotations](https://github.com/ReggieVW/cvat-docs/blob/main/manual/automatic_annotations.md#automatic-annotation-person-body-key-points).

The result of an automatic annotation is an annotation with bounding boxes and key points.

# Manual annotation with person key points
Remark: This can only be executed after task [automatic annotation person key points](#automatic-annotation-with-person-key-points) is executed.

You can drag a point and change the position of individual points. Move the point to the desired position, this way you will create a keyframe.

## Shape grouping
Points are automatically grouped — all points with the same colour are linked to a certain person.
![image](https://user-images.githubusercontent.com/35894891/171384083-5e061097-691f-47a4-a970-9bcab0ddb7a9.png)


## Swith on/off the keyframe
You can switch off the keyframe so intermediate frames will be drawn automatically. Interpolation will be used.
![image](https://user-images.githubusercontent.com/35894891/171388737-3f40bbee-b661-497f-9c81-f97362fcf781.png)

Interpolation can be used when there are key-points of two persons that intermingle for a few frames and manually correction is to cumbersome. 
![image](https://user-images.githubusercontent.com/35894891/180450542-465abc43-e065-4fde-8572-11272fa56eaf.png)

 
