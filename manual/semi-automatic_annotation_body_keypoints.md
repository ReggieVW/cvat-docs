# semi-automatic annotation body keypoints
## HRNET
HRNET is a state-of-the-art algorithm human pose estimation. HRNet uses the top-down method, the network is built for estimating key points based on person bounding boxes

## Exporting person bounding box annotations
Click "Export task dataset" and then choose "CVAT for video". Convert the CVAT XML into JSON.
```
python cvatxml2coco.py --cvat-xml annotations.xml --coco coco.json 
```
Add the body keypoints by executing following script. 
```
python top_down_pose_tracking_input.py configs/body/2d_kpt_sview_rgb_img/topdown_heatmap/coco/hrnet_w48_coco_384x288_udp.py https://download.openmmlab.com/mmpose/top_down/udp/hrnet_w48_coco_384x288_udp-0f89c63e_20210223.pth --video-path <FILEPATH> --out-video-root vis_results --json-path coco.json
```
Convert the JSON into CVAT XML.
```
python coco2cvatxml.py --coco data.json --cvat-xml annotations.xml --withBodyKeyPoints
```
Click "Upload annotations" and then choose "CVAT" to upload the XML

## Shape grouping
Points are automatically grouped — all points are linked to a certain person.
![image](https://user-images.githubusercontent.com/35894891/171384083-5e061097-691f-47a4-a970-9bcab0ddb7a9.png)

## Annotation with points
You can drag a point and change the position of individual points. Move the point to the desired position, this way you will create a keyframe. You can hide it using the Outside, move around, etc.

![image](https://user-images.githubusercontent.com/35894891/171391600-7cb5d041-0558-4155-842c-860ae18ec5f2.png)

## Swith on/off the keyframe
You can swith of the keyframe so intermediate frames will be drawn automatically.
![image](https://user-images.githubusercontent.com/35894891/171388737-3f40bbee-b661-497f-9c81-f97362fcf781.png)



