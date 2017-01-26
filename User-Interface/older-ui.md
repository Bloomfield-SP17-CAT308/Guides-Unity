# GUI

### Displaying
Anytime you want to render a GUI element in Unity it must be called on the method OnGUI(). During this method, you can call other methods or classes to help you display GUI elements. For simple tasks, just showing a label or a button, this would be easy. However, complex UIs may require a lot of planning an sometime be broken down one or more methods to help construct the UI.

## GUI Elements
The GUI system for Unity has a lot of options and elements:

* **GUI.Box** - Draws a box
* **GUI.Label** -  A simple text element
* **GUI.DrawTexture** - Draws a image. If you want to load an asset from your project, create a folder called "Resources" and place the art work in that folder. This way you can call Resources.Load<Texture>("filenameWithoutExtension"); to be able to load the texture in code. 
* **GUI.Button** - A button element, that clicks and responds.
* **GUI.RepeatButton** - A button element, that returns a press the whole time you press down on it.
* **GUI.HorizontalSlider** - A horizontal slider element
* **GUI.VerticalSlider** - A vertical slider element
* **GUI.HorizontalScrollbar** - A horizontal scrollbar like you would see on a window
* **GUI.VerticalScrollbar** - A vertical scrollbar like you would see on a window
* **GUI.SelectionGrid** - Creates a grid of buttons
* **GUI.Toolbar** - Creates a row of buttons
* **GUI.TextField** - A text input field for one line of text
* **GUI.PasswordField** - A text input field for one line of text that is masked
* **GUI.TextArea** - A text input field for multiple lines of text
* **GUI.Toggle** - A checkbox element
* **GUI.Window** - If you want to contain all your items in a window, this is your element!
* **GUI.DragWindow** - Can be added to a GUI.Window, to allow the user to drag and move the window
* **GUI.BeginGroup** / **GUI.EndGroup** - Allows you to group elements 
* **GUI.BeginScrollView** / **GUI.EndScrollView** - Allows you to group elements, where you may need to scroll to see all elements.

## Appearance
You can change the look by one of two ways:

* **GUIStyle** - Allows you to adjust the style of a GUI element, independent of any other asset
* **GUISkin** - Allow you to reconfigure the look of all the GUI elements if you choose to.

