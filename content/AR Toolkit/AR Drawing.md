---
tags:
  - XR
  - R_D
Link: https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Photon/Lobby/Lobby%20AR%20Draw.unity
Built with:
  - AR Foundation
  - PUN2
  - Unity
---
> [!Github Link]
> https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Photon/Lobby/Lobby%20AR%20Draw.unity

# Prerequisites

1. `Network Manager New Script` - returns true when the room is joined
2. `Networked Image Anchor Script` - hides the object container till the image is found

# Function

==Refer to this project for== 
1. ==drawing in AR==
2. ==syncing across Photon using classes==
3. ==Using image anchor for colocalisation

This sketch lets players draw in AR and see a shared view of each others work in real-time.
# Details

### Drawing Panel

==Reference: [https://medium.com/antaeus-ar/how-to-create-ar-draw-doodling-in-unity3d-ar-foundation-233b0e0f921e](https://medium.com/antaeus-ar/how-to-create-ar-draw-doodling-in-unity3d-ar-foundation-233b0e0f921e) ==

In this example, we draw on a UI panel that is attached to the XR Origin. So as the camera moves, the drawing is resolved in 3D.  The image shows an event trigger attached to the Panel which triggers the drawing start / stop function from `Networked AR Draw.cs`. It works in desktop and mobile applications.

![[Screenshot 2024-10-21 at 18.15.31.png|400]]

![[AR multiplayer draw panel.png|500]]
### Photon Sync
This example uses a **class** to contain some of the characteristics of each line so that players can draw them correctly. 
1. Each line has an ActorNumber and lineID which can be used to identify the line whenever the line needs to be updated
2. Each line has a color so that players can differentiate between their lines.

```
public class LineIdentifier : MonoBehaviour  
{  
    public int lineID;  
    public int actorNumber;  
    public Color actorColor;  
  
    public void Initialize(int id, int actor)  
    {        lineID = id;  
        actorNumber = actor;  
        actorColor = SetActorColor();  
    }  
    public Color SetActorColor()  
    {        int playerId = actorNumber;  
        float r = (playerId * 0.3f) % 1f;  
        float g = (playerId * 0.5f) % 1f;  
        float b = (playerId * 0.7f) % 1f;  
        return new Color(r, g, b);  
    }
}
```

In this example, the objects are not **initialised** using PhotonNetwork.Instantiate. Instead, players are sent a new list of lines every time someone draws a line and all players update the lines locally. This is done because all players will have to create and draw the line relative to the anchor and will thus have different x,y,z coordinates.

![[Multiplayer AR Drawing Sync.png|500]]
### Image Anchor

**PunRPC** is used to draw all the lines and the coordinates of the lines are sent relative to the image anchor. Players send each other the relative position of line from image anchor. Players receive the relative position, convert it to the world position and the draw it.

```
private void CreateNewLine(Vector3 startPosition)  
{  
    _currentLineID++; //every player has a different _currentLineID - aka local var not updated on network  
    Vector3 localStartPosition = lineParent.InverseTransformPoint(startPosition);  
    _photonView.RPC("CreateLineOnAllClients", RpcTarget.All, PhotonNetwork.LocalPlayer.ActorNumber, _currentLineID, localStartPosition);  
}
```
![[Multiplayer AR Draw Sync.png]]

![[AR multiplayer draw colocated.png|500]]
# Next Steps
1. Users can change brush color and shape