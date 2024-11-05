# Basic-Character-Movement
Decription

This tutorial will showcase how to create a basic moveable object/ character.

# Prerequisites
Before approaching this tutorial, you will need a current version of Unity and a code editor (such as Microsoft Visual Studio Community) installed and ready to use.

This tutorial was created with Unity 2022.3 LTS and Microsoft Visual Studio Community 2022 versions. It should work with earlier or later versions. But you should check the release notes for other versions as the Editor controls or Scripting API functions may have changed. This is as the changes in the updates can cause errors to occur that may have been fixed or changed within different versions of the Unity and Visual Studio softwares.

If you need help installing Unity you can find many online tutorials such as: https://learn.unity.com/tutorial/install-the-unity-hub-and-editor

You will also need to know how to create an empty project, add primitive objects to your scene, create blank scripts, and run projects from within the editor. If you need help with this, there is a short video demonstrating how to do all of these things here:

https://www.youtube.com/watch?v=eQpWPfP1T6g

# Primary Objectives
The primary objective of this tutorial is to create a basic character movement that will be controlled using the arrow keys and the A,S,W,D keys.

# Preview of tutroial results

https://github.com/user-attachments/assets/8d3c28eb-b0e5-4b55-b873-45c0212b6a07

# Getting Started
To start this tutorial, we will need to create a new Unity Project. To the Unity scene we will add a Plane to represent the floor, and a capsule to represent the playable character.

![image](https://github.com/user-attachments/assets/acf9d0b9-9cad-479d-b816-67c8ad6909bb)![image](https://github.com/user-attachments/assets/a2553329-ee27-4e43-be49-3f40597590fe)

For this tutorial in the images shown throughout, the Player is shown as the green capsule, the red capsule will be used to represent other objects that you may want within the scene. Before any coding or changes to the Unity scene it is best to run the scene to ensure there are no underlying problems with the scene itself prior to the tutorial that may affected.

# Moving the character
Looking at the Unity scene, and selecting the capsule on the right hand side of the screen in the Inspector Window, we can see a the properties of the capsule. At the top of the Inspector window shows the attributes of the Transform  component of the capsule.
![image](https://github.com/user-attachments/assets/1fc638d7-4de4-48d6-81ca-aa8fb04e86c1)

The transform component is used to show where an object is (in this case the capsule) within the scene, and maintaining and or chaning its position. To maintain the position of the capsule, we do not have to add an input. to change the position of the capsule we can alter the values within the position boxes of the transform components. this will change where the capsule is within a specific axis.
![image](https://github.com/user-attachments/assets/a2553329-ee27-4e43-be49-3f40597590fe)![image](https://github.com/user-attachments/assets/baf98287-29ab-44eb-82f3-c1ad04f638d3)

This image shows how the position is changed in the x axis by changing the value of the x in the Inspector Window.
This means that to move the player, all we have to do is create a script that allows for the gameObjects' transform to change depending on the input.

# Scripting Player Movement
First we must select the Player capsule, in the Inspector Window select create and add new script and name it PlayerMovement. When writing scripts, the Name of a script must be written out in one word, with capital letters to indicate a space. This means PlayerMovement will show in the Inspector Window as Player Movement.

![image](https://github.com/user-attachments/assets/a9020ef4-3ad8-4256-91bb-b7bc320f9400)

We will then double click the script added, and that should load up Microsoft Visual Studio (or any other coding software on your device). This is what will appear. The green text within the images of the script is just to help to understand the script means and what certain lines/ segments mean, as simple as possible.

![image](https://github.com/user-attachments/assets/08ebb3bd-df01-48b7-a1de-953244919ae5)
- using [insert system] means that it  can refer to that specific system and its properties when coding using references made to a specific system.
- public means that this class can be accessed from other scripts.
- class means that what follows is a class definition.
- : means this class inherits functions and variables from another class
- Monobehaviour refers Unity supplied class that attaches directly to GameObjects, which we base a new class onto.
- void refers to a function can return normally without the need of a value.
- start means that it is enabled just before any of the Update methods are called the first time, when the Monobehaviour is enabled.
- update means a function that gets called every frame if the MonoBehaviour is enabled.

![image](https://github.com/user-attachments/assets/7f8c8028-9eee-46fd-9ad0-17ef91b3166c)
- Rigidbody refers to a component you can add to a gameObject that allows for a physics-based way to control the movement and position of a GameObject.
- rb is what it will be called within the script. this means that when we type in rb that the Rigidbody will be referenced.
- [SerializedField] helps to make the private variables accessible within the Unity editor without making them public, as well as helps to make serialize any private variable.
- GetComponent means that when this action or statement is refered to that unity will detect this component from the object that the script is applied onto and use it to complete that certain action. In this case it means that when rb is mentioned that at the start of the scene that unity will get that component, and use it in the void update statement to move using the Rigidbody component on the capsule/ player.
- float refers to a numerical value that can be assigned (whole or decimal).
- MoveSpeed what the float (previous point) will be refered to within the code. This means that when y = x * MoveSpeed, that y is equal to the value of x multiplied by the MoveSpeed/ float which is 10 in the script.
- horInput refers to the total value calculated of the Input by the user on the horizontal axis multiplied by the MoveSpeed.
- verInput refers to the total value calculated of the Input by the user on the vertical axis multiplied by the MoveSpeed.
- GetAxiRaw("-") refers to the axis (Horizonal or Vertical) which uses the world's x and z axis using the Left and Right, and a and d keys.
- rb.velocity, it refers the velocity vector of the rigidbody.  it represents the rate of change of the rigid body per frame.
- new just means new
- Vector3 refers to the position using all 3 axis x, y, z which can be represented on a 3d space.

  ![image](https://github.com/user-attachments/assets/0eadee11-1914-44d2-8ca0-683320df5707)

Before we load the scene and press play, we add the Rigidbody component. This will be used within the script to move the player in a 3d axis.

https://github.com/user-attachments/assets/b6b95205-8e89-4cde-bfd1-039488a3523e

This is what should happen when playing the scene in Unity. To fix this problem, we will edit the Rigidbody component we added onto the player.

https://github.com/user-attachments/assets/00158657-6cf7-41c2-bfad-ea62fde3d77d

The Rigidbody also allows the object to utilise gravity within Unity seen in the video above, as the object falls.
    
  ![image](https://github.com/user-attachments/assets/c0f04f74-cba7-4090-8aa7-07c03b27fbac)
  
This means that the rotation is frozen of the y and z axis. This allows for the capsule to move without the object move around without problems for now and later on when adjusting the script. The main reason we do this is to avoid the problems with the mesh's (objects in this case capsule's) collider. 
  
  ![image](https://github.com/user-attachments/assets/efdc8604-66a6-4f14-828b-f51d8760df52)
This is as when you move if the collider moves it can affect the character moves, which can affect how the character jumps and or interacts with other objects within the scene. This just helps to avoid any complications which may occur further in the project. This problem is shown in the image above (image shows the capsule collider), and once you fall/ collpase onto the side it is quite hard to get into the proper position for the other mechanics to work, if it is position orientated. One example of this is if there is an empty object onto the bottom of the playable character that detects the ground to jump. If the player is on its side, the empty object is unable to detect the "ground" and causes the player unable to jump anymore and the player will have a hard time to get back onto its original postion. By freezing the player rotation, it means that the player is unable to fall over and mess with mechanics of the player. 

https://github.com/user-attachments/assets/04b687c3-36b6-4f0b-b9c9-e8204cef3113

This video shows what happens when you freeze the rotation on the y and z axis on the Rigidbody component.

To customise the results of the script you can adjust the number of the float in the script higher to increase the movement speed and lower to decrease the movement speed, as well as change the mass within the Rigidbody component to make the character fall and or jump faster, as well as act more realistically when simulating/ building the game.
