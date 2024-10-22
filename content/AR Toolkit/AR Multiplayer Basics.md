---
tags:
  - XR
  - R_D
Built with:
  - AR Foundation
  - PUN2
  - Unity
---

> [!Recommended Notes]
> [[AR Multiplayer Scene Setup]]
> 

Using [[Unity]], ARFoundation and PUN2 and make a multiplayer AR experience. PUN2[^1] enables networking capabilities.
# Initialisation

There are two methods of instantiation for multiplayer objects depending on the use case.
### Photon instantiation 

**Better used if all players see the object at the same location relative to themselves.** In the examples, it is used when only one player (MasterClient) is responsible for instantiation.

Read [[AR Multiplayer Scene Setup#Photon instantiation]] for more documentation on PhotonNetwork.Instantiate.

This is used on [[AR Multiplayer Objects]] since all objects are instantiated from the MasterClient

### PunRPC instantiation

**Better used if all players see the object at different locations relative to themselves.** It is used whenever there is an image anchor relative to which objects are created. This method is a little more cumbersome to set up. 

Players instantiate objects locally and then use PunRPC to pass the transform parameters and any identifiers to the other players. All players then receive the data and instantiate their local object.

Read [[AR Multiplayer Scene Setup#Photon sync (PunRPC)]] for more documentation on PunRPC.

This is used on [[AR Drawing]] since all objects are instantiated locally

![[Multiplayer AR Draw Sync.png]]

# Ownership 

Ownership determines which player has control over a specific in-game object. 
### IsPhotonViewMine: 
This boolean property is attached to a PhotonView component. It tells you whether the current player owns the object. If `IsPhotonViewMine` is true, you can safely modify the object's properties locally, as these changes will be synchronized to other players.
### RPC Target
When calling a Remote Procedure Call (RPC), you can specify the `RPC Target`. This determines who should receive and execute the RPC.

![[Screenshot 2024-10-22 at 14.21.06.png]]
In the context of a multiplayer AR experience, you might use ownership and RPC targets to implement features like:
- **Object placement:** When a player places a virtual object, the ownership is assigned to them.
- **Interaction:** When a player interacts with an object (e.g., picking it up or using it), an RPC is sent to the object's owner to update its state.
- **Synchronization:** To ensure that all players see the same object states, RPCs can be used to broadcast changes in position, rotation, or other properties.
# Synchronisation

### Remote Procedure Calls 

This allows players to trigger actions on other players' devices. Imagine using a PunRPC to paint a virtual mural on a real wall – the action would be called on your device, then transmitted to other players using PUN2, making the mural appear on their AR views as well.

for more information read [[AR Multiplayer Scene Setup#PunRPC]]

### OnPhotonSerializeView

reference: https://www.youtube.com/watch?v=dQ-Y33T92wU

This function synchronizes the state of your in-game object across the network. This is crucial for constantly updating other players about the position and rotation of objects in the AR space. For example, using OnPhotonSerializeView on a virtual paintbrush would continuously send its location data, ensuring everyone sees the brush moving in real-time.

# Colocalisation
One of the challenges with Mixed Reality has been colocalisation i.e., people located in the same space and having a shared view [^2]. This is a solved problem in AR and therefore easier to tackle & implement in our own projects.

A couple of ways to do this in AR include
1. Using Cloud Anchors [^3] - 
	1. Download AR Core Extension [^4]
	2. Create AR Core API [^5]
2. Using Image Anchors - more documentation in [[AR Multiplayer Scene Setup#Image Anchor]]
3. Geolocation

# Time continuity
tbd

# Sources
[Multiplayer AR — why it’s quite hard](https://medium.com/6d-ai/multiplayer-ar-why-its-quite-hard-43efdb378418)
[PUN Course Build a Multiplayer Augmented Reality Game with Unity with Tevfik Ufuk DEM?RBA?, IRONHEAD Games](https://guttitech.com/phpfusion/articles.php?article_id=3167&rowstart=4) 
[PUN AR Implementation](https://github.com/Jentuuh/AR-Multiplayer-Escape-Room?tab=readme-ov-file)
[Cheat code](https://gist.github.com/ssshake/86b4da6c31258a7188f7fef3dbaf1d26)

[^1]: https://doc.photonengine.com/pun/current/getting-started/pun-intro
[^2]: https://www.youtube.com/watch?v=y6UQMmMX5hU
[^3]: [Cloud Anchors](https://developers.google.com/ar/develop/cloud-anchors)
[^4]: https://developers.google.com/ar/develop/downloads
[^5]: https://developers.google.com/ar/develop/authorization?platform=unity-arf#api-key-unity
