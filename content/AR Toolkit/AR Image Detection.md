---
tags:
  - XR
  - R_D
Link: 
Built with:
  - AR Foundation
  - Unity
---
> [!Github Link]
> https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Image%20Tracker.unity

==reference: https://www.youtube.com/watch?v=OwpRSF7X9sI ==
# Function

This example uses image tracking to detect images.

![[AR Image Tracking.mp4]]

# Details

Add an `AR Tracked Image Manager` to your gameObject (or XR Origin) and create a Reference Image Library (Create > XR > Reference Image Library). 

```
foreach (var trackedImage in trackedImageManager.trackables)  
{  
    if (trackedImage.trackingState == TrackingState.Tracking)  
    {        
    // Set the position and rotation of the client to match the tracked image  
        transform.position = trackedImage.transform.position;  
        transform.rotation = trackedImage.transform.rotation;  
    }  
}
```

Image tracking is used in multiplayer projects to create and access an image anchor. More details can be found in [[AR Multiplayer Basics]] or `Networked Image Anchor.cs`.