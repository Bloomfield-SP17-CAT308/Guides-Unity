# Some Unity Scripting

When you create a new script from Unity, you get a basic shell of the script. It ends up looking like of the create script:

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

// Class Section:
public class BasicScript : MonoBehaviour {

    // Use this for initialization
    void Start () {

    }
    
    // Update is called once per frame
    void Update () {

    }
}
```

Here's what's happening:

* **"Using" Section** - This is the libraries that the script will be using
* **"Class" Section** - Every script contains a script. Your script name is the same as your class. Each class should be unique.
* **Class content** - In the basic script that Unity generates for you there are two methods:
	* **Start()** -  Called when the script starts to run
	* **Update()** - Called every frame

## Other Methods

Here are a couple other methods that are common in Unity C# scripts

* ``` void Awake () ``` - Called when the script is first called, even if you turn the script off for that Game Object.
* ``` void FixedUpdate () ``` - This is called everytime the physics is updated. All physics calculations are done in "one go", to help keep the simulation realistic.

## Variables

If you want to have the Unity Editor allow for modifying your class variables from your script, you need to declair them as "public"

```cs
public class BasicScript : MonoBehaviour {
    public int showsUpInUnityEditor = 91;
    int doesNotShowUpUnUnityEditor = 123;

    // Use this for initialization
    void Start () {
    
    }
    
    // Update is called once per frame
    void Update () {
    
    }
}
```

## Useful methods

* ```Debug.Log ( <message> ); ``` -  Helps you print information to the console while the game is running.

## Useful Classes

These class will come up often, which are used in this guide:

```Vector3``` - A class for storing 3D positions and directions. Also has helpers in it to do some standard math.
```Quaternion``` - Represents rotations, more on that later.


## Input

Best practices in Unity state that you should specify your controls through the Input Manager. Here, you can set all the axes you need input on and the user will be able to customize their controllers if need be. To change you inputs, you can select from the menu **Edit -> Project Settings -> Input**. Under each axis, you will have some options that come into play based on what you set:

**Gravity** - The speed in which the axis falls back to 0
**Dead** - The size of the dead zone
**Sensitivity** - The speed in which the value moves toward the target value

```Input.GetAxis ("Axis Name");``` - Returns a float between -1 and 1. This will give you the value of the "Axis Name" as defined in **Edit -> Project Settings -> Input**. 

```Input.GetAxisRaw ("Axis Name");``` - Returns a float that is either -1, 0, or 1. This only returns absolute values, there is no in-between.

As with an axis, you can also check buttons, the same way:

```Input.GetButton ("Button Name");``` - Returns a boolean. If the button is being held down this will be true

```Input.GetButtonDown ("Button Name");``` - Returns a boolean. When the button is first pressed down, this will be true

```Input.GetButtonUp ("Button Name");``` - Returns a boolean. When the button is released, this will be true

Unity has an Input class which has a lot of methods for getting controllers/keys/mouse input besides using these specified axes.

```Input.GetKey ( [ KeyCode or "Button Name" ]);``` - Returns a boolean. If the key is being held down this will be true

```Input.GetKeyDown ( [ KeyCode or "Button Name" ] );``` - Returns a boolean. When the key is first pressed down, this will be true

```Input.GetKeyUp ( [ KeyCode or "Button Name" ] );``` - Returns a boolean. When the key is released, this will be true

For mouse use, for buttonNumber the values are: 0 - left button, 1 - right button, 2 - middle button

```Input.GetMouseButton (buttonNumber);``` - Returns a boolean. If the mouse button is being held down this will be true

```Input.GetMouseButtonDown (buttonNumber);``` - Returns a boolean. When the mouse button is first pressed down, this will be true

```Input.GetMouseButtonUp (buttonNumber);``` - Returns a boolean. When the mouse button is released, this will be true

For acceleromiters, like in phones and tablet, you can use:

```Input.GetAccelerationEvent(index);``` - Returns an AccelerationEvent, which contains a Vector3 with the value of acceleration and the deltaTime since the last measurement, 

While this shows up in the Input class, the following is only useful for showing the names of Joysticks:

```Input.GetJoystickNames();``` - Returns a list of Joysticks

## Changing objects

To change objects in script, you can do the following 

```transform.localScale = new Vector3 (1.0f, 0.5f, 1.0f);``` - adjust the scale of the object by 0.5 units on the Y axis, both the Z and Z will stay "normal". 

```transform.position = new Vector3 (10.0f, 10.0f, 10.0f);``` - Changes position of the object to 10,10,10

To change the rotation, the easiest way to do so is with the Rotate().

```transform.Rotate(new Vector3 (0.0f, 0.0f, 5.0f));``` - Rotates an object on the Z axis

```transform.rotation = new Quaternion ();``` - Rotates back to 0,0,0

To rotate to a particular position, you need to use a little [Quatarnions](http://docs.unity3d.com/ScriptReference/Quaternion.html) magic:
```cs
Quaternion fromRotation = transform.rotation;
Quaternion toRotation = Quaternion.Euler (10.0f, 10.0f, 10.0f);
transform.rotation = Quaternion.Lerp (fromRotation, toRotation, 1.0f);
```

## Randomness

Want a random number? Try this:

```Random.value``` - Returns a float - random number between 0.0 and not exactly 1

```Random.Range(0.0f, 20.0f)``` - Returns a random number between the values you set. If you don't use a decimal, the numbers will be integers.

## Lights

Want to modify a light? It's easy to do:

```light.intensity = Random.Range (0.0f, 8.0f);``` - Changes the intensity of a light. WARNING: may cause seisures if you run this in an Update()!

## Targeting Game Objects

By default, if you try these commands, you can only do it on the current Game Object. You could also make a public Game Object variable in a class, like a game controller class, and perform these command on that:

```cs
public GameObject objectToManipulate;
```
...

```cs
objectToManipulate.transform.Rotate(new Vector3 (10.0f, 10.0f, 10.0f));
```

## Prefabs

* **Prefab** - A reusable Game Objects that you create
* **Instance** - One of the actual objects in a scene
* **Instantiate** - Process of creating an Instance
* **Inheritance** - How the Prefab is linked to all the instances

If you make changes to the Prefab, it will propagate through all the instances of it in your game. You can tell which ones are Prefabs in the Hierarchy view because they are a blue color instead of black.

To create a Prefab, in the Project tab, right-click **Create -> Prefab**. Then drag in something from the Hierarchy view into that created Prefab. 

To create an instance of the Prefab, just drag the Prefab from the Project tab into the scene.

If you want to stop an instance of a Prefab from being linked to the Prefab, from the menu you can select **GameObject -> Break Prefab Instance**.

Now you can create your object through code using the Instantiate (); method. To do so:

1. Create a Prefab

2. Create an empty game object and call it ***SpawnPoint***

3. Create this spawner script, which will create a new prefab in the same spot that it was built in when you press backspace, and at the location of the ***SpawnPoint*** when you press the spacebar:

	```
	using UnityEngine;
	using System.Collections;
	
	public class Spawner : MonoBehaviour {
	    public GameObject prefab;
	
	    void Update () {
	        if (Input.GetKeyDown (KeyCode.Backspace)) {
	            Instantiate (prefab);
	        } else if (Input.GetKeyDown (KeyCode.Space)) {
	            Instantiate (prefab, this.transform.position, this.transform.rotation);
	        }
	    }
	}
	```

4. Attach the script to ***SpawnPoint***

5. Drag the prefab you want to the “Prefab” field under ***SpawnPoint***’s script

## Collision

Collision requires a collider. By default, the basic shapes in Unity have them. You can modify the size of them if you need, or add custom collision maps.

Colliders provide a few Triggers to help you do things. Once you turn them on with the "Is Trigger" checkbox, you can do things like:

```void OnTriggerEnter ( Collider other )``` - Called when the object first enters the trigger

```void OnTriggerStay ( Collider other )``` - Called every update the object is in the trigger

```void OnTriggerExit ( Collider other )``` - Called when an object leaves a trigger

All of these have a parameter passed that is the object that enter/is in/left the trigger.

## Rigidbody

To change a rigidbody's speed, you can do:

```rigidbody.velocity = new Vector3 (13.4f, 0.0f);``` - This will make it move 13.4 units on the X and 0 on the Y.

You can also change other aspects of the rigidbody, remeber the options in the Inspector View? They are just variables: 

```cs
rigidbody.mass = 1;
rigidbody.drag = 0;
rigidbody.angularDrag = 0.05;
rigidbody.useGravity = true;
rigidbody.isKinematic = false;
rigidbody.interpolation = RigidbodyInterpolation.None;
rigidbody.collisionDetectionMode = CollisionDetectionMode.Discrete;
rigidbody.constraints = RigidbodyConstraints.None
```

**NOTE 1**: interpolation and collisionDetectionMode use an Enums to have you choose what you want. MonoDevelope will help you make the selection of the options.

**NOTE 2**: constraints is integer, using bit fields where you have to use a bitwise or "|" to join together which axis you want to freeze. If you want to freeze the Y axis for postion and freeze rotation on the X axis would need to do the following:

```cs
rigidbody.constraints = RigidbodyConstraints.FreezePositionY | RigidbodyConstraints.FreezeRotationX;
```

## Looking Ahead

To figure out if an object is in front of you, you can raycast. There are 12 different ways to call Physics.Raycast. This one looks 10 units in front of an object:

```cs
bool objectThere = Physics.Raycast (transform.position, transform.forward, 10.0f);
```

This will allow you to tell which object you hit (and destroy it!!)

```cs
RaycastHit objectHit;
if (Physics.Raycast (transform.position, transform.forward, out objectHit)) {
    Debug.Log ("Destory " + objectHit.collider.gameObject.name + "!!!!");
    Destroy (objectHit.collider.gameObject);
}
```

## Game Controller

No, we're not an XBox 360, PS4, WiiMote or XBox One controller, these are often referred to as that main script in your project. This is what will contain the logic for your game and keep track of all the elements of it. 


## Finding GameObjects with scripts

There are several ways to find GameObjects in Unity:

### [GameObject.Find](http://docs.unity3d.com/ScriptReference/GameObject.Find.html)
The easiest way to find a particular object, however, it may be slower than using the FindWithTag version. If you want to find a GameObject by name, you can use the following in code:

```cs
GameObject.Find("nameOfObjectToFind");
```

If you need to find an object and get the specific class of that object you can specify the Class you need with this:

```cs
GameObject.Find("nameOfObjectToFind").GetComponent<Class>();
```

So if you wanted to find a Button named ClickyClicky in my scene and store it to a variable I could do:

```cs
Button myButton = GameObject.Find("ClickyClicky").GetComponent<Button>();
```

### [GameObject.FindWithTag](http://docs.unity3d.com/ScriptReference/GameObject.FindWithTag.html)

This can find **one** object with a tag that was chosen in the editor. If it cannot find one, then it will return ```null```

This is the faster way, and should be used if you are setting up your scripts to find the GameController instead of having to drag-and-drop the GameController to all your assets.

### [GameObject.FindGameObjectsWithTag](http://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)

This returns a array of Game Objects that have been tagged in the editor. If it cannot find one, then it will be an empty.

```cs
GameObjects[] myTaggedItems = GameObject.FindGameObjectsWithTag("Respawn");
```

## Removing GameObjects

Sometimes you need to remove objects from the scene. This can be accomplished with a call to Destroy!

```cs
Destroy(gameObject);
```

if you want to remove the current item, then do this:

```cs
Destroy(this.gameObject);
```

## Resource Folder
This is a special folder in your Assets folder. If you have a folder named Resources, you can easily load files using, replacing Class with they actual class type you need:

```cs
Resources.Load<Class>("filenameWithoutExtensions");
```

If you are loading an image name ShinyMetal.jpg as a texture, then it would look like:

```cs
Texture myTexture = Resources.Load<Texture>("ShinyMetal");
```

All items in the Resources folder will be included in your build, so it may make your final executable larger. You may have multiple Resources folders, say one in Images, one in Materials. To learn more about it, take a look at the Unity [Script Reference for Resources](http://docs.unity3d.com/ScriptReference/Resources.html)

Similarly, there is another special folder called "[StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html)", which when included, all assets inside that folder will be bundled with your project when you build it. It is commonly used to store files like movies .


