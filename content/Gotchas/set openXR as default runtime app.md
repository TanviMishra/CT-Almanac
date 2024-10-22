---
tags:
  - gotchas
  - SP
---
### Error: 
set openXR as default runtime app
### Solution [^1]:
1. open `Registry Editor` as admin
2. go to `HKEY_LOCAL_MACHINE\SOFTWARE\Khronos\OpenXR\1`, create whatever keys are missing along the way if needed
3. create a “string value” with the name `ActiveRuntime` and the value `C:\Program Files\Oculus\Support\oculus-runtime\oculus_openxr_64.json` (adjust if your Oculus app is installed elsewhere).
### Documentation:
![[Pasted image 20240821111944.png]]
### Software:
[[Unity]]
### Hardware:
[[Meta Quest 3]]

[^1]: https://community.khronos.org/t/set-openxr-active-in-oculus-noobi/109988