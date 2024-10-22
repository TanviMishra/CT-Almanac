# PhotonNetwork.Instantiate

photon instantiate[^1] is similar to unity initialisation except
1. It takes a string (e.g., "MyPrefabName"). Place the prefab in `Assets > Resources` and pass the prefab's name as the string.
2. The prefab must have a photon view attached to it.

syntax[^2]:  `PhotonNetwork.Instantiate(string, location, rotation, custom properties);` 

```
PhotonNetwork.Instantiate("MyPrefabName", new Vector3(0, 0, 0), Quaternion.identity, 0);
```
# PunRPC

Some specifications of using RPC:
1. The function name is passed as a string (e.g., "RPC function") and the function parameters are passed as variables.
2. RPC function variables have to be PUN serialisable [^3].
3. The GameObject that the script is attached to must also have a photon view.

syntax[^4]: `photonView.RPC("RPC function", RpcTarget.All, [variable1], [variable2]...)`

```
//RPC Fn Call
_photonView.RPC("CreateLineOnAllClients", RpcTarget.All, PhotonNetwork.LocalPlayer.ActorNumber, _currentLineID, localStartPosition);

//Function
private void CreateLineOnAllClients(int actorNumber, int lineID, Vector3 localStartPosition)  
{  
    GameObject newLine = Instantiate(linePrefab, Vector3.zero, Quaternion.identity)
}
```

The function call can be defined using rpcTarget to specify who will receive the information. `RpcTarget.All`, `RpcTarget.OthersBuffered` are used frequently.

![[Screenshot 2024-10-22 at 14.21.06.png]]

# Sources


[^1]: [Player instantiation](https://www.youtube.com/watch?v=BKPDAeCMGj4)
[^2]: https://doc.photonengine.com/pun/current/gameplay/instantiation
[^3]: https://doc.photonengine.com/pun/current/reference/serialization-in-photon
[^4]: https://doc.photonengine.com/pun/current/gameplay/rpcsandraiseevent