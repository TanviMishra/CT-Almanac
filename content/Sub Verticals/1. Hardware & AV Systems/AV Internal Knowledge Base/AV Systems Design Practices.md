---
tags:
  - AV
Created by:
  - Aaron
---
### Hardware Control
[[Single point of control]] – Ideally there is one point for technicians to control hardware instead of several. For example, if there are Q-Sys and Crestron ([[Hardware Control]]) on a project, one system should have one touchscreen that provides control access to both.

### Redundancy / Failover
In order to balance cost, energy consumption, project lifespan, and uptime, I generally recommend:  
1. [[Media Servers]]: Primary media server with redundant [[PSU]]'s, Backup digital signage player, cold spare media server (stays off but installed in the rack, and connected to the video matrix or AV over IP infrastructure). Whenever possible I try to match media server specifications with the most demanding needs. Generally I will then recommend one cold spare for every four primary media servers.  
2. LED Processors: Generally recommend backup processors throughout 
3. Video Distribution
4. [[Monitoring Cameras]]
5. Building Tie-in's
6. Fire-Alarm tie-in – via Crestron processor or [Advantech Adam I/O](https://www.advantech.com/en-us/products/iot-ethernet-i-o-modules-adam-6000-6200/sub_gf-5197)
7. [[BMS]] tie-in via BACnet (high heat load front-end equipment) 
8. Security Appliance / VPN
### Back End Equipment  

Should be kept in equipment racks rooms rather than millwork or out in the space as much as possible. Consider AV transport and network-based control to front-end equipment from the rack room instead of edge devices installed behind front-end equipment. This allows for easier service and keeps the most equipment in a climate, access-controlled area. 

 [[PDU]]'s - Specify switchable-by-outlet 

Specify Metered-by-outlet as much as possible – this is a low cost way to begin to add energy monitoring on projects. This can drive our own research, or help the client track their energy consumption.

### Custom Servers

> [!NOTE]
> is custom servers same as media server in which case is this content better moved
> 

> [!NOTE]
> what is the difference between [[Servers]], [[Media Servers]] and custom servers

Begin with server-class chassis – There are a few options that support graphics cards. A lot of server models do not. [Some only support headless graphics cards.](https://www.dell.com/en-us/shop/servers-storage-and-networking/poweredge-xr12-rack-server/spd/poweredge-xr12/pe_xr12_14827_vi_vp?configurationid=49fd39ac-dff4-4009-b0ea-0edd14a3515b) 
	[Dell 7960 Rack](https://www.dell.com/en-us/shop/desktop-computers/precision-7960-rack-workstation/spd/precision-r7960-workstation/xctopr7960us_vp) 
	[Dell iDRAC Enterprise](https://www.dell.com/en-us/lp/dt/open-manage-idrac) 
	[Intel vPro](https://www.intel.com/content/www/us/en/architecture-and-technology/vpro/overview.html) 

[~~Dell 7920 Rack~~](https://www.dell.com/en-us/shop/desktop-computers/precision-7920-rack-workstation/spd/precision-7920r-workstation) Discontinued 
[~~Dell 3930 Rack~~](https://www.dell.com/en-us/shop/workstations-isv-certified/precision-3930-rack-workstation/spd/precision-3930r-workstation#configurations_section) Discontinued  

[Nvidia qualified server list – Filtered to Quadro](https://www.nvidia.com/en-in/data-center/data-center-gpus/qualified-system-catalog/?start=0&count=50&pageNumber=1&searchTerm=&filters=eyJmaWx0ZXJzIjpbXSwic3ViRmlsdGVycyI6eyJudmlkaWFHUFUiOlsiUlRYIDUwMDAiLCJSVFggNTAwMCBBZGEgR2VuZXJhdGlvbiIsIlJUWCA2MDAwIiwiUlRYIDYwMDAgQWRhIEdlbmVyYXRpb24iLCJSVFggQTYwMDAiLCJSVFggQTU1MDAiLCJSVFggQTUwMDAiLCJSVFggQTQ1MDAiXSwiR1BVQ29ubmVjdGl2aXR5IjpbIlBDSWUgR2VuIDQiXSwibWF4R1BVUGVyTm9kZSI6WzIsMyw0LDUsNl19LCJjZXJ0aWZpZWRGaWx0ZXJzIjp7fSwicGF5bG9hZCI6W119) 

Need to do more research on: 
	HPE ProLiant 
	Fujitsu  
	Supermicro  
	ASRock Rack  
	BOXX RAXX 

**Prefererences**
1. Redundant [[PSU]]'s whenever possible
2. Prefer [[ECC]] RAM  
3. [[OOB]] whenever possible. KVM redundancy as well as monitoring via Dell's iDRAC Enterprise or similar  
4. [NVIDIA Quadro cards](https://www.nvidia.com/en-us/design-visualization/solutions/quadro-display-desktop-management/) (currently A5000, A6000, possibly A4500)  
	Quadro Cards can spoof EDIDs, utilize mosaic, quadro sync II,  [Nvidia Mosaic](https://www.nvidia.com/en-us/design-visualization/solutions/nvidia-mosaic-technology/) [Nvidia Omniverse](https://www.nvidia.com/en-us/omniverse/ecosystem/) [Quadro Sync II](https://www.nvidia.com/en-us/design-visualization/solutions/quadro-sync/)  
5. RAID 10 on drives

Multiple [[NIC]]'s can be helpful for supporting multiple [[VLAN]]'s

[Notchmarks GPU list](https://manual.notch.one/0.9.23/en/docs/notchmarks/) is a good starting point 

### Recommended Project Equipment Manufactures 
[[0. AV Systems Equipment]] contains a table of all equipment. Specific equipment notes (e.g., projectors) have a more detailed breakdown of the models and additional theoretical(?) notes

1. Network Switches – Netgear AV Line or Cisco Business 350 
2. [[Media Servers]]: Dell 7920 / 7960 series rack 
3. Touch Screens / HMI's: Maple Systems  
4. [[Video Matrices]]: Lightware 
5. [[Audio]] DSP: Q-Sys 
6. [[Architectural Lighting]]: Pharos 
7. [[Monitoring Cameras]]: Axis 
8. [[Digital Signage Players]]: BrightSign 
9. Large [[Projectors]]: Panasonic  
10. Small [[Projectors]]: Epson LightScene (similar chassis to the discontinued Panasonic Space Player) 
11. VE'd [[Projectors]]: Epson 

### Recommendations for Tech: 

> [!NOTE]
> moved from [[AV Systems Onboarding]] by Tanvi, check with Aaron is this is a good fit

Generally 
1. **everything** we specify on projects should be [[UL]]/[[ETL]] listed and [[FCC]] certified. 
2. we prefer equipment from known manufacturers who have been around for 10 years or more.

To consider:
1. How long will support, replacements, parts be available for the device? 
2. What warranty is included? 
3. Has our AV Integrator worked with it before? 

Installation environment - [IP Ratings](https://en.wikipedia.org/wiki/IP_Code) and [NEMA ratings](https://www.siemon.com/en/home/support/compliance/nema-ratings-and-ip-equivalents)

#### UL Listed equipment (North America Installs) 

– Language from [[UL]]: Federal [[OSHA]] requirements mandate that all electrical equipment in the workplace be “certified” or subjected to a complete and thorough evaluation before use. 

[[ETL]] Listed devices are considered UL listed because ETL follows UL created standards. ETL does not create their own standards, they just provide device testing and certification based on standards by others.

