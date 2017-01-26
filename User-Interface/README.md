# User Interface

Starting with Unity 4.6, they added a newer UI system, that is much more efficient than the previous one. While starting with a new project, you would most likely want to stick to the new UI methods. However, if you take a look at older tutorials or older projects you might want to take a look at [a guide for older GUIs](older-ui.md) and see what that's about.

:exclamation: _NOTE: You may have to manually include the line ```using UnityEngine.UI;``` (especially in MonoDevelop) to use these items in codes if MonoDevelop is being fussy._

## [UI Canvas](http://docs.unity3d.com/Manual/class-Canvas.html)
This is the root component for all rendering of UI objects. All UI elements need to be placed in a _Canvas_. 

![](http://docs.unity3d.com/uploads/Main/GUI_Rect_Tool_Button.png)

Layout of the canvas is handled with the RectTool , which the [Unity Documentation](http://docs.unity3d.com/Manual/UIBasicLayout.html) goes in to detail on how to place UI items.

### Hiding
To hide a canvas in script you can do something like this:

```cs
  Canvas myCanvas = GameObject.Find("CanvasName").GetComponent<Canvas>();
  myCanvas.enabled = false;
```

to show the canvas again, just change it to 

```cs
  myCanvas.enabled = true;
```

### Render Modes
There are 3 modes to display the _Canvas_ items.

* **Screen Space - Overlay** - The elements will be overlayed on the scene. If the scene is resized or resolution is changed, the _Canvas_ is changed.
* **Screen Space - Camera** - Similar to the overlay mode, but the items are rended as if they are a certain distance infront of the camera
* **World Space** - The canvas will act just as it were any other object in the scene. Sometimes referred to as a "diegetic interface".

### Event System
Unity is kind enough to add an EventSystem to your Heirarcy if you include a UI Canvas to your project. The Event System is a way of sending events based on input between scripts.

## Visual Components

### [UI Text](http://docs.unity3d.com/Manual/script-Text.html)
Used as a label for things. You can change the text very easily in code with something like this:

```cs
using UnityEngine;
using UnityEngine.UI;
using System.Collections;

public class GameController : MonoBehaviour {
	public Text myLabel;

	// Use this for initialization
	void Start () {
		myLabel.text = "Hello World!";
	}
}
```

### [UI Image](http://docs.unity3d.com/Manual/script-Image.html)
Displays an image. This image has to be a _Sprite (2D or UI)_. You can use the whole image, or you can (nine-slice)[http://www.unityrealm.com/unity-9-slice-advantages/] the image. Use the documentation to dive deeper into what you can do with an image.

### [UI Raw Image](http://docs.unity3d.com/Manual/script-RawImage.html)
Similar to UI Image, except the image does not have to be a Sprite, hence Raw Image. This is useful if you want to load images from websites or servers, without having to worry about converting them.

### [UI Mask](http://docs.unity3d.com/Manual/script-Mask.html)
Not really a UI component per se, but it is often used with components to set an area to that is visible, and the rest to be clipped. 


## Interactive Components
### [UI Button](http://docs.unity3d.com/Manual/script-Button.html)
In the **Inspector view**, you can click on the **On Click()'s +** button to add a call to some code when the button is clicked. If you inlcude a Game Controller class, and have that added to an Empty Object in the Heirarchy, then you can select your Game Controller as the target object and then select a method to perform when a button click occurs.

### [UI Toggle](http://docs.unity3d.com/Manual/script-Toggle.html)
Like a radio button or check box.

### [UI ToggleGroup](http://docs.unity3d.com/Manual/script-ToggleGroup.html)
A Toggle Group is not shown in the Hierarchy's create option. You should create an Empty Object in your Canvas and then go into the menu or use the _Add Component_ button and select Component -> UI -> Toggle Group. Then for your UI Toggles, you can specify the **Group** object. 

* *Allow Switch Off* - If enabled, all the toggles in the group can be switched off, otherwise one will always be selected.

_NOTE: Make sure you change the Toggles in the group so that only one or none of the toggles are selected by default._

### [UI Slider](http://docs.unity3d.com/Manual/script-Slider.html)
To create a vertical slider, change the Direction option to either _Top to Bottom_ or _Bottom to Top_

### [UI ScrollBar](http://docs.unity3d.com/Manual/script-Scrollbar.html)
Similar to a UI Slider, but for scrolling an area such as a canvas or image.

### [UI DropDown](http://docs.unity3d.com/Manual/script-Dropdown.html)
For presenting a choice of options.

### [UI InputField](http://docs.unity3d.com/Manual/script-InputField.html)
Used for getting input in the form of text

### [UI ScrollRect](http://docs.unity3d.com/Manual/script-ScrollRect.html)
Often used for when a group of UI elements might take up more area than can be displayed. Often used in conjuction with the UI Scroll Bar.

