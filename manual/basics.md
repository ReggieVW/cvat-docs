- [User's guide for the Surv-AI-llance project](../README.md)
    - This section contains [basics information]
        - [Creating an annotation task](#creating-an-annotation-task)
        - [Interface of the annotation tool](#interface-of-the-annotation-tool)

# Creating a project
![image](https://user-images.githubusercontent.com/35894891/200163016-94e648ed-6eaa-4e82-8bea-0d5877faba83.png)
Create a project pressing ``+`` button and select ``Create new project`` on the project page.

### Name
The name of the project to be created.

# Creating an annotation task
![image](https://user-images.githubusercontent.com/35894891/166926067-d6a6dc51-a73a-4ba3-bfea-e55b0e0a7bbe.png)
Create an annotation task pressing ``+`` button and select ``Create new task`` on the tasks page.

### Name
The name of the task to be created.

## Basic configuration
![image](https://user-images.githubusercontent.com/35894891/166926907-bcf56a06-0db6-4327-9eec-e2183b895be3.png)

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
The ``Raw`` is a way of working with labels for an advanced user. Raw presents label data in json format with an option of editing and copying labels as a text. 
![image](https://user-images.githubusercontent.com/35894891/170944919-05f7dd28-f493-467f-80b2-67f19796d573.png)

<b>Select files</b>. Press tab ``My computer`` to choose some files for annotation from your PC. If you select tab ``Connected file share`` you can choose files for annotation from your network. If you select ``Remote source``, you'll see a field where you can enter a list of URLs (one URL per line).
![image](https://user-images.githubusercontent.com/35894891/170945341-c233d305-aa03-4a36-a1e3-d0eae481b7a6.png)


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




