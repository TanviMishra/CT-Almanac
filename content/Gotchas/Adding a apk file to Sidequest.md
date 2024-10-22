---
tags:
  - gotchas
  - SP
---
### Error: 
A task failed. Check the tasks screen for more info. floorplan.apk: /data/local/tmp/_stream.apk could not be installed (INSTALL_FAILED_UPDATE_INCOMPATIBLE: Package com.rockwellgroup.ssa_sample signatures do not match previously installed version; ignoring!)
### Solution:
1. Go to library on Oculus and delete the file manually (in my case com.rockwellgroup.ssa_sample)
2. ADB fix
	1. Run ADB Commands->Enable USB ADB
	2. adb shell pm uninstall com.beatgames.beatsaber
	3. Run Command
### Software:
[[Sidequest]]
