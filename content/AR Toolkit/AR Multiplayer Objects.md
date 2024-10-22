---
tags:
  - XR
  - R_D
Link: https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Photon/Lobby/Lobby%20Cube%20Changer.unity
Built with:
  - PUN2
  - AR Foundation
  - Unity
---
> [!Github Link]
> https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Photon/Lobby/Lobby%20Cube%20Changer.unity

# Prerequisites

1. `Network Manager New Script` - returns true when the room is joined
2. `Networked Image Anchor Script` - hides the object container till the image is found

# Function

==Refer to this project for== 
1. ==instantiating multiplayer objects== 
2. ==syncing characteristics across multiplayer objects==

This sketch automatically spawns 10 cubes randomly around the image anchor. When you click on a cube it changes color for all users. The host can hit refresh to respawn cubes.

# Details
### Instantiation
refer to [[AR Multiplayer Basics#Photon Initialisation]] for more details

This code (from `Networked Image Anchor.cs`)checks for the player that is the MasterClient (host) and instantiates the cube across the network. i.e., one player creates the cubes for all other players as well.

```
private void Update()  
{  
    if (_networkManagerScript._roomJoined == true && _cubeDrawn == false)  
    {        
	    if (PhotonNetwork.IsMasterClient)  
        {            
	        for (int i = 0; i < 10; i++)  
            {                
	            GameObject cube = PhotonNetwork.Instantiate(Path.Combine("Photon Prefabs", "Sync Color Cube"), targetRandomPosition , Quaternion.identity, 0);  
            }            
            _cubeDrawn = true;  
        }    
	}
}

```

==ADD VIDEO==
### Color Changing

The cubes have the `Networked Colour Changer.cs` script attached. When you click a cube, it changes the color and using PunRPC, sends the new values to all other players. The cube color then updates across other players as well. 

```
private void colorCalls()  
{  
    // Change the color locally  
    Color randomColor = GenerateRandomColor(_renderer.material.color);  
    ChangeColor(randomColor);  
    
    // Send color update to other clients (if owner)  
    _photonView = GetComponent<PhotonView>();  
    _photonView.RPC("ChangeColorOnAllClients", RpcTarget.AllBuffered, randomColor.r, randomColor.g, randomColor.b);  
}

```

The above code shows how a random color is generated and sent to all other clients as its rgb values to all other players. GenerateRandomColor(), ChangeColor(), ChangeColorOnAllClients() are user-defined functions.

![[AR Multiplayer Color Change Tests.png|500]]

### Image Anchor
Players' views are synced by dropping an anchor where the image is. In this example (found in `Networked Image Anchor.cs`), the container for the cube inherits the same position and rotation of the image anchor. Thus ensuring the cubes spawn at the anchor.

```
foreach (var trackedImage in trackedImageManager.trackables)  
{  
    if (trackedImage.trackingState == TrackingState.Tracking)  
    {        
	    // Set the position and rotation to match the tracked image  
        parentContainer.transform.position = trackedImage.transform.position;  
        parentContainer.transform.rotation = trackedImage.transform.rotation;  
        _anchorFound = true;  
        InstantiateObjectAtParent();  
        break; // Use the first tracked image found  
    }  
}

```

In the image below, 'Drama' book is the anchor (indicated by a brown quad). As you can see, the anchor is not in the same spot in both images. So there is a slight discrepancy between the location of cubes for both. 

![[AR Multiplayer Color Change Shared View.png|500]]

# Next Steps
1. Use local cloud anchors as a way of ensuring more accurate colocation