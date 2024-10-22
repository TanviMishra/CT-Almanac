---
tags:
  - XR
  - R_D
---
> [!NOTE]
> Read [[AR Build Settings]] first.
> Projects: [[AR Image Detection]], [[AR Plane Detect]]
> 
#### Basic AR scene elements [^1]

A basic AR scene contains the following GameObjects and components:
- **AR Session** GameObject
    - [AR Session component](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.0/manual/features/session.html)
    - [AR Input Manager component](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.0/api/UnityEngine.XR.ARFoundation.ARInputManager.html)
- **XR Origin (Mobile)** GameObject
    - [XR Origin component](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.0/api/UnityEngine.XR.ARFoundation.ARSessionOrigin.html)
    - **CameraOffset** GameObject
        - [AR Camera Manager component](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.0/manual/features/Camera/camera-components.html#ar-camera-manager-component)
        - [AR Camera Background component](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.0/manual/features/Camera/camera-components.html#ar-camera-background-component)
#### AR packages
The AR provider plug-ins supported by Unity include:
- [Apple ARKit XR Plug-in](https://docs.unity3d.com/Packages/com.unity.xr.arkit@5.0) on iOS
- [Apple visionOS XR Plug-in](https://docs.unity3d.com/Packages/com.unity.xr.visionos@1.0/manual/index.html) on visionOS
- - [Google ARCore XR Plug-in](https://docs.unity3d.com/Packages/com.unity.xr.arcore@5.0) on Android
- [OpenXR Plug-in](https://docs.unity3d.com/Packages/com.unity.xr.openxr@1.7/manual/index.html) for any AR device with an OpenXR runtime, including HoloLens 2 and others
- [PolySpatial visionOS packages](https://docs.unity3d.com/Packages/com.unity.polyspatial.visionos@latest) for the Apple Vision Pro device

![[Screenshot 2024-09-04 at 11.29.57.png]] [^2]
### Sources:

[^1]: [AR development in unity](https://docs.unity3d.com/Manual/AROverview.html)
[^2]: [AR Foundation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@5.0/manual/index.html)
[^3]: [AR tutorial for beginners using unity 2022](https://www.youtube.com/watch?v=gpaq5bAjya8)
