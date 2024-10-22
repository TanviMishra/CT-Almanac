---
tags:
  - XR
  - R_D
Link: https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Place%20Objects.unity
Built with:
  - AR Foundation
  - Unity
---
==reference: https://www.youtube.com/watch?v=lYDfV-GaKQA ==

> [!Github Link]
> https://github.com/labatrockwell/xr-research/blob/AR/Multi_User_Demo/Assets/Scenes/AR/Place%20Objects.unity
# Function 

This example uses plane detection to place objects on a plane when you tap on your screen.
To use plane detection, you must add an `AR Plane Manager` [^1] to your XR Origin.
Then add the script `PlaceObject.cs`

![[AR Touch Grass.mp4]]
# Details
### Platform Support

![[Screenshot 2024-10-21 at 16.16.38.png]] [^2]
### Trackable Type
As shown in the image, there are 5 trackable types. If ordered by size, they would go: PlaneWithinPolygon < PlaneWithinBounds<PlaneEstimated< PlaneWithinInfinity. [^3]

![[Screenshot 2024-10-21 at 16.06.57.png]]
