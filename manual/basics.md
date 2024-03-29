- [User's guide for the Surv-AI-llance project](../README.md)
    - This section contains [basics information]
        - [Creating a project](#creating-a-project)
        - [Creating an annotation task](#creating-an-annotation-task)
        - [Interface of the annotation tool](#interface-of-the-annotation-tool)
        - [Shortcuts](#shortcuts)

# Creating a project
Go to the project page.
![image](https://user-images.githubusercontent.com/35894891/200163016-94e648ed-6eaa-4e82-8bea-0d5877faba83.png)
Create a project pressing ``+`` button and select ``Create new project`` on the project page.

## Project configuration
![image](https://user-images.githubusercontent.com/35894891/200163191-48c991db-a3e6-4a8a-9dcc-660d3002d438.png)

### Name
The name of the project to be created.

### Labels
See section [Labels](./basics.md#labels-2)

# Creating an annotation task
You can create a task on the task page or on the project page.

- Create an annotation task pressing ``+`` button and select ``Create new task`` on the tasks page.
 ![image](https://user-images.githubusercontent.com/35894891/166926067-d6a6dc51-a73a-4ba3-bfea-e55b0e0a7bbe.png)

- Create an annotation task pressing ``+`` on the project page.
![image](https://user-images.githubusercontent.com/35894891/200164384-ee70d8d6-1344-4fa7-b804-3119e57b8a6d.png)



## Task configuration
![image](https://user-images.githubusercontent.com/35894891/166926907-bcf56a06-0db6-4327-9eec-e2183b895be3.png)

### Name
The name of the task to be created.

### Project selection
Link your task to a project (optional)

### Labels
Only availabe when the project is not linked to a project.
See section [Labels](./basics.md#labels-2)

### Select files
Press tab ``My computer`` to choose some files for annotation from your PC. If you select tab ``Connected file share`` you can choose files for annotation from your network. If you select ``Remote source``, you'll see a field where you can enter a list of URLs (one URL per line). You can also select a ``Cloud storage``.
![image](https://user-images.githubusercontent.com/35894891/170945341-c233d305-aa03-4a36-a1e3-d0eae481b7a6.png)

# Labels
There are two ways of working with labels: ``Constructor`` & ``Raw``

#### The Constructor
The ``Constructor`` is a simple way to add and adjust labels. To add a new label click the ``Add label`` button.
![image](https://user-images.githubusercontent.com/35894891/166927448-85f2fbb9-6148-4271-90ba-2ad3446345c6.png)

You can set a name of the label in the Label name field and choose a color for each label.
![image](https://user-images.githubusercontent.com/35894891/166933036-ef249177-1d44-4d1b-91eb-5aacc5bc3eef.png)

You can add an attribute and set its properties by clicking ``Add an attribute``:
![image](https://user-images.githubusercontent.com/35894891/166932845-ed4a0c97-b2a6-4dab-82a9-cc48291f0353.png)

a) Set the attribute’s name.

b) Choose the type of the attribute:
* ``Select`` — drop down list of value
* ``Radio`` — is used when it is necessary to choose just one option out of few suggested.
* ``Checkbox`` — is used when it is necessary to choose any number of options out of suggested.
* ``Text`` — is used when an attribute is entered as a text.
* ``Number`` — is used when an attribute is entered as a number.

c) Checkbox ``Mutable`` determines if an attribute would be changed frame to frame.

#### The Raw
The ``Raw`` is a way of working with labels for an advanced user. Raw presents label data in json format with an option of editing and copying labels as text. 
![image](https://user-images.githubusercontent.com/35894891/170944919-05f7dd28-f493-467f-80b2-67f19796d573.png)


# Interface of the annotation tool
The tool consists of:
- ``Header`` -  pinned header used to navigate CVAT sections and account settings;
- ``Top panel`` — contains navigation buttons, main functions and menu access;
- ``Workspace`` — space where images are shown;
- ``Controls sidebar`` — contains tools for navigating the image, zoom,
  creating shapes and editing tracks (merge, split, group)
- ``Objects sidebar`` — contains label filter, two lists:
  objects (on the frame) and labels (of objects on the frame) and appearance settings.
  
![image](https://user-images.githubusercontent.com/35894891/199857672-946d4a4b-92c8-470b-b50f-83c909560631.png)

## Basic navigation

1.  Use arrows below to move to the next/previous frame.
    Use the scroll bar slider to scroll through frames.
    Almost every button has a shortcut.
    To get a hint about a shortcut, just move your mouse pointer over an UI element.

   ![image](https://user-images.githubusercontent.com/35894891/170958991-efd8090e-ad52-40d2-9f86-47d93b37b6bb.png)

1.  To navigate the image, use the button on the controls sidebar.
    Another way an image can be moved/shifted is by holding the left mouse button inside
    an area without annotated objects.

    ![image](https://user-images.githubusercontent.com/35894891/170959056-e89dfe25-dc99-4e2c-9634-9f58c97c46d1.png)

1.  You can use the button on the sidebar controls to zoom on a region of interest.
    Use the button ``Fit the image`` to fit the image in the workspace.
    You can also use the mouse wheel to scale the image
    (the image will be zoomed relatively to your current cursor position).

    ![image](https://user-images.githubusercontent.com/35894891/170959093-1b577a9a-9922-4782-baf3-b2214719d818.png)
    

## Shortcuts

Many UI elements have shortcut hints. Put your pointer to a required element to see it.

![image](https://user-images.githubusercontent.com/35894891/200915832-8f3760ef-53da-4757-8573-c745a20231ab.png)

| Shortcut                       | Common                                                                          |
|--------------------------------|---------------------------------------------------------------------------------|
|                                | _Main functions_                                                                |
| ``F2``                         | Open/hide the list of available shortcuts                                       |
| ``F3``                         | Go to the settings page or go back                                              |
| ``Ctrl+S``                     | Go to the settings page or go back                                              |
| ``Ctrl+Z``                     | Cancel the latest action related with objects                                   |
| ``Ctrl+Shift+Z`` or ``Ctrl+Y`` | Cancel undo action                                                              |
| Hold ``Mouse Wheel``           | To move an image frame (for example, while drawing)                             |
|                                | _Player_                                                                        |
| ``F``                          | Go to the next frame                                                            |
| ``D``                          | Go to the previous frame                                                        |
| ``V``                          | Go forward with a step                                                          |
| ``C``                          | Go backward with a step                                                         |
| ``Right``                      | Search the next frame that satisfies to the filters <br> or next frame which contain any objects|
| ``Left``                       | Search the previous frame that satisfies to the filters <br> or previous frame which contain any objects|
| ``Space``                      | Start/stop automatic changing frames                                            |
| `` ` `` or ``~``               | Focus on the element to change the current frame                                |
|                                | _Modes_                                                                         |
| ``N``                          | Repeat the latest procedure of drawing with the same parameters                 |
| ``M``                          | Activate or deactivate mode to merging shapes                                   |
| ``G``                          | Activate or deactivate mode to grouping shapes                                  |
| ``Shift+G``                    | Reset group for selected shapes (in group mode)                                 |
| ``Esc``                        | Cancel any active canvas mode                                                   |
|                                | _Image operations_                                                              |
| ``Ctrl+R``                     | Change image angle (add 90 degrees)                                             |
| ``Ctrl+Shift+R``               | Change image angle (substract 90 degrees)                                       |
| ``Shift+B+=``                  | Increase brightness level for the image                                         |
| ``Shift+B+-``                  | Decrease brightness level for the image                                         |
| ``Shift+C+=``                  | Increase contrast level for the image                                           |
| ``Shift+C+-``                  | Decrease contrast level for the image                                           |
| ``Shift+S+=``                  | Increase saturation level for the image                                         |
| ``Shift+S+-``                  | Increase contrast level for the image                                           |
| ``Shift+G+=``                  | Make the grid more visible                                                      |
| ``Shift+G+-``                  | Make the grid less visible                                                      |
| ``Shift+G+Enter``              | Set another color for the image grid                                            |
|                                | _Operations with objects_                                                       |
| ``Ctrl``                       | Switch automatic bordering for polygons and polylines during drawing/editing    |
| Hold ``Ctrl``                  | When the shape is active and fix it                                             |
| ``Ctrl+Double-Click`` on point | Deleting a point (used when hovering over a point of polygon, polyline, points) |
| ``Shift+Double-Click`` on point| Editing a shape (used when hovering over a point of polygon, polyline or points)|
| ``Right-Click`` on shape       | Display of an object element from objects sidebar                               |
| ``T+L``                        | Change locked state for all objects in the sidebar                              |
| ``L``                          | Change locked state for an active object                                        |
| ``T+H``                        | Change hidden state for objects in the sidebar                                  |
| ``H``                          | Change hidden state for an active object                                        |
| ``Q`` or ``/``                 | Change occluded property for an active object                                   |
| ``Del`` or ``Shift+Del``       | Delete an active object. Use shift to force delete of locked objects            |
| ``-`` or ``_``                 | Put an active object "farther" from the user (decrease z axis value)            |
| ``+`` or ``=``                 | Put an active object "closer" to the user (increase z axis value)               |
| ``Ctrl+C``                     | Copy shape to CVAT internal clipboard                                           |
| ``Ctrl+V``                     | Paste a shape from internal CVAT clipboard                                      |
| Hold ``Ctrl`` while pasting    | When pasting shape from the buffer for multiple pasting.                        |
| ``Crtl+B``                     | Make a copy of the object on the following frames                               |
|                                | _Operations are available only for track_                                       |
| ``K``                          | Change keyframe property for an active track                                    |
| ``O``                          | Change outside property for an active track                                     |
| ``R``                          | Go to the next keyframe of an active track                                      |
| ``E``                          | Go to the previous keyframe of an active track                                  |
|                                | _Attribute annotation mode_                                                     |
| ``Up Arrow``                   | Go to the next attribute (up)                                                   |
| ``Down Arrow``                 | Go to the next attribute (down)                                                 |
| ``Tab``                        | Go to the next annotated object in current frame                                |
| ``Shift+Tab``                  | Go to the previous annotated object in current frame                            |
| ``<number>``                   | Assign a corresponding value to the current attribute                           |




