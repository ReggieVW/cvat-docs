# Automatic annotation bounding boxes

See page [automatic_annotations](https://github.com/ReggieVW/cvat-docs/blob/main/manual/automatic_annotations.md).

The result of an automatic annotation is an annotation with separate bounding boxes.
<img src="https://user-images.githubusercontent.com/35894891/176129602-e34617b8-e628-4809-9487-e9602f09d237.png" width="800" height="400" />

# Manual annotation bounding boxes

## Track mode 

-   You need to select a ``Rectangle`` on the sidebar,
    in the appearing form, select the desired ``Label`` and the ``Drawing method``.

    ![image](https://user-images.githubusercontent.com/35894891/176419500-b80df927-a01c-42c3-b39f-93e9bb7e8554.png)

- Create a ``Rectangle`` in ``Track mode`` by clicking on ``Track``.

  ![image](https://user-images.githubusercontent.com/35894891/170965613-ce958d91-9032-418a-9add-65bdd8572456.png)
      
- A red guideline will be shown
    
  ![image](https://user-images.githubusercontent.com/35894891/171143541-bf2aa35d-71ab-487c-981f-03e03ffd048b.png)
      
- Click on the left mouse button, expand the rectangle over what you want to select and click again.

  ![image](https://user-images.githubusercontent.com/35894891/171145155-a629d26b-21f4-42f4-906f-40e60b75dc83.png)

- In ``Track mode`` the rectangle will be automatically interpolated on the next frames. 

- If the object starts to change its position, you need to modify the rectangle where it happens.
      <b>It isn't necessary to change the rectangle on each frame</b>, simply update several keyframes
      and the frames between them will be interpolated automatically.
     ![image](https://user-images.githubusercontent.com/35894891/171150304-ca11d723-66f0-479f-b9dd-d21476c6924f.png)

-   When the annotated object disappears or becomes too small, you need to
    finish the track. You have to choose ``Outside Property``, shortcut ``O``.
    
    ![image](https://user-images.githubusercontent.com/35894891/171151873-8cbb49a2-48bf-43fd-8501-9b146c90d6ee.png)

-   If the object isn't visible on a couple of frames and then appears again,
    you can use the ``Merge`` feature to merge several individual tracks
    into one. Click Merge button or press M to apply changes.

    ![image](https://user-images.githubusercontent.com/35894891/170968838-ef104d4f-f749-4703-9ff5-84fce598caf5.png)
    
