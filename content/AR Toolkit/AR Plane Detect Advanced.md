---
tags:
  - XR
  - R_D
Link: https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Photon/Lobby/Lobby%20Place%20Object.unity
Built with:
  - AR Foundation
  - PUN2
  - Unity
---


> [!Link]
> https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Photon/Lobby/Lobby%20Place%20Object.unity
# Prerequisites

1. `Network Manager New Script` - returns true when the room is joined
2. `Networked Image Anchor Script` - hides the object container till the image is found
# Function

==Refer to this project for== 
1. ==choosing between multiple objects== 
2. ==plane detection==

This sketch lets multiple players place objects on detected planes. They can choose between three objects - spheres, capsules and cubes. Each player's objects have a unique color.

# Details
### Object Selection

From `Button Clicker.cs` using buttons to change which object should be drawn. For photon initialising objects, you need to pass a string instead of the object prefab. So, clicking on the button just changes a string. In this example, the 3d objects are saved as "Torus", "Sphere", "Cube" in `Assets/Photon Prefabs`

```
void Start()  
{  
    torus.onClick.AddListener(delegate {TaskWithParameters("Torus"); });  
    sphere.onClick.AddListener(delegate {TaskWithParameters("Sphere"); });  
    cube.onClick.AddListener(delegate { TaskWithParameters("Cube"); });  
}  
  
void TaskWithParameters(string message)  
{  
    shape = message;  
}
```

![[AR Multiplayer Plane Detect Multiple Objects.png|500]]
### Player Color

Using ActorNumber to set the color of the objects

```
private Color SetPlayerColor()  
{  
    int playerId = PhotonNetwork.LocalPlayer.ActorNumber;  
    float r = (playerId * 0.3f) % 1f;  
    float g = (playerId * 0.5f) % 1f;  
    float b = (playerId * 0.7f) % 1f;  
    return new Color(r, g, b);  
}
```


![[AR Multiplayer Plane Detect Different Colors.png|500]]
# Next Steps:
1. using the image anchor similar to in [[AR Drawing]] for colocation.

[^1]: [AR Plane Manager Component Resource](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.1/manual/features/plane-detection/arplanemanager.html)
[^2]: https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.1/manual/features/plane-detection/platform-support.html
[^3]: https://discussions.unity.com/t/difference-between-plane-trackabletypes/731041/3