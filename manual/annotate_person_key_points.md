- [User's guide for the Surv-AI-llance project](../README.md)
    - [Annotation person key points]
        - [Automatic annotation with person key points](#automatic-annotation-with-person-key-points)
        - [Manual annotation with person key points](#manual-annotation-with-person-key-points)
        - [Export annotation with person key points](#export-annotation-with-person-key-points)

# Automatic annotation with person key points

See page [automatic_annotations](../../main/manual/automatic_annotations.md#automatic-annotation-person-key-points).

# Manual annotation with person key points
<b>Note: This can only be executed after task [automatic annotation person key points](../../main/manual/automatic_annotations.md#automatic-annotation-person-key-points) is executed.</b>

You can drag a point and change its position.

## Shape grouping
Pre-annotated person key points are automatically grouped. All points with the same colour are linked to a specific person.
![image](https://user-images.githubusercontent.com/35894891/171384083-5e061097-691f-47a4-a970-9bcab0ddb7a9.png)


## Swith on/off the keyframe
You can switch off the keyframe so intermediate frames will be drawn automatically. Interpolation will be used in between two keyframes.
![image](https://user-images.githubusercontent.com/35894891/171388737-3f40bbee-b661-497f-9c81-f97362fcf781.png)

Interpolation can be a solution when there are key-points of two persons that intermingle for a few frames and manually correction with dragging and moving the points is to cumbersome. 
![image](https://user-images.githubusercontent.com/35894891/180450542-465abc43-e065-4fde-8572-11272fa56eaf.png)

# Export annotation with person key points
<b>Note: the feature of directly exporting person key points with JSON is not available in CVAT. The JSON file also does not export the group_id which is required to group the person keypoints.
To have the results in COCO format and not loose the activity annotations you have to first export to CVAT XML and then convert to COCO.</b>

First click on save because CVAT does not automatically saves the changes. Then click ``Menu`` in CVAT. Click ``Export task dataset`` and choose ``CVAT for video``.
![image](https://user-images.githubusercontent.com/35894891/199825605-7ba58ca2-a341-4a23-bf56-709243d1f34e.png)

Convert the CVAT XML into JSON. Further information about the conversion tool and installation https://github.com/ReggieVW/cvat-utils

```
python cvatxml2coco.py --cvat-xml <FILE> --coco-json <FILE>
```

To view the pose estimations from the JSON file in a video execute the following script

```
python vis_pose_tracking_result.py configs/body/2d_kpt_sview_rgb_img/topdown_heatmap/coco/hrnet_w48_coco_384x288_udp.py https://download.openmmlab.com/mmpose/top_down/udp/hrnet_w48_coco_384x288_udp-0f89c63e_20210223.pth --video-path <FILE> --out-video-root vis_results --json-path <FILE>
```

