This guide will help you set up a Windows PC to use as a video content source in a production setting. 

Disclaimer: Since the main goal of this configuration is to prevent interruptions to media software, some of these settings may come at the expense of normal functionality, OS security, or energy usage.   

Phrases in <mark style="background: #ADCCFFA6;">blue</mark> can be executed by opening the start menu and typing the phrase.  

Phrases < <mark style="background: #FFF3A3A6;">in yellow tags</mark> > are project-specific. 

## Step 1: Delete all files and reinstall Windows 

It's highly recommended to start with a fresh copy of the operating system. 

<mark style="background: #ADCCFFA6;"> Start > “Reset this PC”</mark> 

#### Installing Windows - Out-of-box experience (OOBE) 
< <mark style="background: #FFF3A3A6;">SERVER USERNAME</mark> > for user name 
< <mark style="background: #FFF3A3A6;">SERVER PASSWORD</mark> > for password 
Choose ‘Offline Account’  
Turn off all tracking / ad preferences  
Leave email blank for registration   

- <mark style="background: #FFB8EBA6;">Windows 11</mark> - On the “Oops, you’ve lost internet connection” or “Let’s connect you to a network” page, use the Shift + F10 keyboard shortcut to open command prompt 
- Type OOBE\BYPASSNRO and press enter. The PC will restart and OOBE will start again 
## Step 2: Windows Setup 

Rame the PC: <mark style="background: #ADCCFFA6;">Start > “View PC name” </mark>
Click “Rename this PC” 
Enter < <mark style="background: #FFF3A3A6;">SERVER NAME</mark> > for PC Name 
#### Network 
<mark style="background: #ADCCFFA6;">Start > “Network Connections”</mark> 
TCP/IPv4 Network settings for each NIC: 

| IP Address:           | <mark style="background: #FFF3A3A6;">< SERVER IP ADDRESS > |
| --------------------- | ---------------------------------------------------------- |
| Subnet mask:          | <mark style="background: #FFF3A3A6;">< SUBNET MASK >       |
| Default Gateway:      | <mark style="background: #FFF3A3A6;">< GATEWAY >           |
| DNS Server:           | <mark style="background: #FFF3A3A6;">< DNS PRIMARY >       |
| Alternate DNS Server: | <mark style="background: #FFF3A3A6;">< DNS SECONDARY >     |

Typical DNS Server: 8.8.8.8 
Typical Alternate DNS Server: 8.8.4.4 

*Example TCP/IPv4 Network settings for a private AV network:*  

| IP Address:           | <mark style="background: #FFF3A3A6;"><192.168.0.101>   |
| --------------------- | ------------------------------------------------------ |
| Subnet mask:          | <mark style="background: #FFF3A3A6;">< 255.255.255.0 > |
| Default Gateway:      | <mark style="background: #FFF3A3A6;">< 192.168.0.1 >   |
| DNS Server:           | <mark style="background: #FFF3A3A6;">< 8.8.8.8 >       |
| Alternate DNS Server: | <mark style="background: #FFF3A3A6;">< 8.8.4.4 >       |
#### NAS (If Applicable to the Project) 
<mark style="background: #ADCCFFA6;">Start > “File Explorer”</mark>
Right click on “This PC” and select “Map Network Drive…” 

| Drive:  | Z:           |
| ------- | ------------ |
| Folder: | < NAS PATH > |
Make sure “Reconnect at sign-in” is checked  

#### Auto Login 
<mark style="background: #ADCCFFA6;">Start > “Registry Editor” </mark>
Navigate to group: 
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon  
<mark style="background: #ADCCFFA6;">Right Click > New > String Value </mark>  
Make the following string values in the Winlogon folder:  

|                 |              |                                                                 |
| --------------- | ------------ | --------------------------------------------------------------- |
| Value Name:     | Type:        | Value Data                                                      |
| AutoAdminLogon  | String Value | 1                                                               |
| DefaultUserName | String Value | <mark style="background: #FFF3A3A6;">< SERVER USERNAME ></mark> |
| DefaultPassword | String Value | <mark style="background: #FFF3A3A6;">< SERVER PASSWORD ></mark> |
#### Disable Windows Updates 
<mark style="background: #ADCCFFA6;">Start > "Group Policy" </mark> 

Navigate to: 
Computer Configuration > Administrative Templates > Windows Components>Windows Update 

Set “Configure Automatic Updates” to Disabled  

Computer Configuration > Administrative Templates > Windows Components>Microsoft Defender Antivirus  

Set “Turn off Microsoft Defender Antivirus” to Enabled 

Note that MsMpEng.exe will try to prevent this. You may need to stop the process first. 
#### Allow “Realtime” Priority 

<mark style="background: #ADCCFFA6;">Start > "Local Security Policy"</mark>  

Navigate to: 
Local Policies > User Rights Assignment > Increase Scheduling Priority  

1. Double click “Increase Scheduling Priority” to show Properties 
2. Click “Add User or Group…” 
3. Type < <mark style="background: #FFF3A3A6;">SERVER USERNAME</mark> > into the text field (“Enter the object names to select”) 
4. Click “Check Names” to verify 

## Step 3: Windows Configuration 

<mark style="background: #ADCCFFA6;">Start > "Developer Settings"</mark> 
Click apply to turn on all settings for Explorer, Remote Desktop and Powershell.  

<mark style="background: #ADCCFFA6;">Start > "Timezone" </mark>
Set < PROJECT TIMEZONE >.  

<mark style="background: #ADCCFFA6;">Start > "Power Settings"</mark> 
Set all triggers to ‘Never’  

<mark style="background: #ADCCFFA6;">Start > "Active Hours" </mark>
6am to 11pm 

<mark style="background: #ADCCFFA6;">Start > "Windows update delivery settings"</mark>  
Turn off "Allow Downloads from other PCs"  

<mark style="background: #ADCCFFA6;">Start > “UAC”</mark> 
Set Never notify (move the slider all the way down)  

<mark style="background: #ADCCFFA6;">Start > “Services"</mark> 
Open the Properties for "Windows Search", then Stop and Disable it.  

<mark style="background: #ADCCFFA6;">Start > “Adjust Performance"</mark> 
Adjust for best performance 
Re-enable "Show window contents..."  

<mark style="background: #ADCCFFA6;">Start > "Show transparency in Windows"</mark> 
Turn off transparency effects 

<mark style="background: #ADCCFFA6;">Start > "Background Apps"</mark> 
Turn off “Let apps run in the background” 

<mark style="background: #ADCCFFA6;">Start > "Notifications"</mark> 
Turn all notifications off 
Disable "Show me the Windows welcome experience..."  

<mark style="background: #ADCCFFA6;">Start > "Xbox networking"</mark> 
Navigate to “Xbox Game Bar”, then turn off Game Bar 

<mark style="background: #ADCCFFA6;">Start > "Startup"</mark> 
Turn off OneDrive, Cortana, Skype, Windows Security Icon  

<mark style="background: #ADCCFFA6;">Start > "Uninstall"</mark> 
Uninstall Skype, Office, Xbox Live  

<mark style="background: #ADCCFFA6;">Start > “Taskbar Settings” </mark>
Search > Hidden 
News and interests > Turn off 
Disable “Show Cortana button” 
Disable “Show Task View button” 
Unpin Microsoft Store 
Unpin Mail 

<mark style="background: #ADCCFFA6;">Start > ‘Check for Updates’</mark> 
Consider doing one final round of windows updates. 

#### Taskbar  
Search bar > **Hidden** 
News and interests > **Turn off**  
**Disable** “Show Cortana button”  
**Disable** “Show Task View button” Unpin Microsoft Store from taskbar Unpin Mail from taskbar  

## Step 4: Display Configuration 
#### EDID Lock 
This keeps the server unaware of any video issues or disconnects. Make sure the server is connected to the production video device. (e.g. the Video Matrix). If the connected video device is changed you may need to repeat the instructions: 

<mark style="background: #ADCCFFA6;">Start > "NVIDIA Control Panel"</mark> 
Navigate to Workstation > View system topology  

For each production output connected to the GPU: 
1. Click on “EDID (Monitor)” 
2. Select the relevant display and click “Export EDID” 
3. Store the EDID file in Documents/EDIDs 
4. Switch to the “Load” tab 
5. Browse to the newly created EDID file 
6. Check the box for the relevant display 
7. Click “Load EDID” 

#### Nvidia Mosaic (If Applicable to the Project) 
This is only necessary in multi-output configurations. Mosaic will present multiple displays as one virtual display to Windows with optional bezel correction. 

<mark style="background: #ADCCFFA6;">Start > "NVIDIA Control Panel" </mark> 
1. Navigate to Workstation > Set up Mosaic 
2. Click “Create new configuration” 
3. Set up the displays according to the intended final mapping 

Note that Mosaic will “disconnect” any non-mosaic displays after finishing the configuration (your GUI/KVM output, for example). This can be fixed by navigating to the Windows display settings, selecting the disconnected display and setting it back to “Extend Desktop…” 

## Step 5: BIOS Configuration 
#### Set PC to automatically boot after power loss  

Dell iDRAC: 
<mark style="background: #ADCCFFA6;">Start > “Powershell”</mark> 
ssh [root@idrac.local](mailto:root@idrac.local) 
racadm>> set BIOS.SysSecurity.AcPwrRcvry On 
racadm>> jobqueue create BIOS.Setup.1-1 
#### Other Hardware: 
The location and exact name of this setting will vary based on your hardware. 
Boot to BIOS via the keyboard. This can be either F1, F2, DEL, Enter then F1, or F10. 
Set to: Restore on AC Power Loss.  

Boot from RTC