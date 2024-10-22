---
tags:
  - XR
  - R_D
---

> [!Recommended Notes]
>More info: [[AR Build Settings]], [[AR Basic Scene Setup]]
> Projects: [[AR Drawing]], [[AR Multiplayer Objects]], [[AR Plane Detect Advanced]]

# Helper scripts
These are a couple of scripts to make it easier to jump into multiplayer work. 
## Network manager
Add `Network Manager New.cs` script to your XR Origin.
This script handles entering and leaving a room.
bool `_roomJoined` keeps track of whether the player has joined the room and can be accessed by other scripts. E.g.,

```
void Update()  
{  
    if (networkManagerScript._roomJoined)  
    {        
	    ContinueDrawing();  
    }
}
```

## Image Anchor
Add `Networked Image Anchor.cs` script to your XR Origin.
This script handles image tracking. When an image is tracked it changes the it toggles on the parentContainer, moves and rotates it to match the image anchor

```
private void Update()  
{  
    foreach (var trackedImage in trackedImageManager.trackables)  
    {        
	    if (trackedImage.trackingState == TrackingState.Tracking)  
        {             
            parentContainer.transform.position = trackedImage.transform.position;  
            parentContainer.transform.rotation = trackedImage.transform.rotation;  
            _anchorFound = true;  
            break; // Use the first tracked image found  
        }  
    }    
    
    if (_anchorFound == true)  
    {        
	    findingAnchorText.SetActive(false);  
        parentContainer.SetActive(true);  
    }    
    else  
    {  
        findingAnchorText.SetActive(true);  
        parentContainer.SetActive(false);   
    }  
}
```

bool `_anchorFound` keeps track of the image anchor and can be accessed by other scripts.

```
void Update()  
{  
    if (_networkedImageAnchorScript._anchorFound && networkManagerScript._roomJoined)  
    {        
	    ContinueDrawing();  
    }
}
```

`_anchorFound` can also be toggled on when building for PC and the PC app should run smoothly without needing to find image anchor.
## Multiplayer Lobby

If you have a lobby, you can just add the `Lobby Manager.cs` script to any game object. It takes in button inputs and loads the corresponding scene name. 

![[Screenshot 2024-10-22 at 15.58.18.png]]

