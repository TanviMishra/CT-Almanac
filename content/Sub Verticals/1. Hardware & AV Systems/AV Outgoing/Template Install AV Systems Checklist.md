1. AV integrator goes through this and checks everything off. 
2. Then the Rockwell Systems Designer confirms every item on site. 
3. Anything outstanding becomes a punch list item to be issued to the AV integrator or other appropriate trade.  

Once all items are clear, the Software and Media Design teams can head to site with confidence that they can do their work. 
### Equipment Rack
- [ ] All cables are tidy and labeled 
- [ ] Rack Room is below 77 degrees F, HVAC, CRAC or CRAH unit is operational 
- [ ] Rack Elevations match Equipment Racks 
- [ ] Rack room is clean and dust free 
### VPN
- [ ] VPN can be accessed remotely 
- [ ] All VPN accounts have been created 
- [ ] Monitoring Cameras can be accessed over VPN 
- [ ] All Servers can be accessed over VPN 
- [ ] NAS can be accessed over VPN 
- [ ] KVM can be accessed over VPN 
- [ ] KVM is stable when used over VPN 
### KVM
- [ ] All Media Servers can be accessed via KVM 
- [ ] Software Server can be accessed via KVM 
- [ ] Utility Server can be accessed via KVM 
- [ ] Local KVM Console is operational 
### Hardware Control
- [ ] Status page: Screen lock and timeout function correctly 
- [ ] Status page: Server status is accurate 
- [ ] Status page: Fire alarm relay status is accurate 
- [ ] Schedule page: "Turn everything on now" button works correctly 
- [ ] Schedule page: "Turn everything off now" button works correctly 
- [ ] Schedule page: "Active time" settings work correctly 
- [ ] Schedule page: "Active days" settings work correctly 
- [ ] Audio page: Audio level controls work correctly 
- [ ] Audio page: Audio levels reset to default in the morning 
- [ ] Routing page: Server status reported correctly 
- [ ] Routing page: Routing status reported correctly 
- [ ] Power page: All power controls work correctly 
- [ ] Power page: PoE reset triggers correct behavior 
- [ ] Touchscreen frontend is stable 
- [ ] UI layout and labels are correct 
- [ ] UI is free of visible bugs 
- [ ] UI is accessible via virtual touchscreen on Utility PC and mirrors physical touchscreen 
- [ ] Fire alarm relay triggers correct behavior 
### Media Servers
- [ ] All servers have Internet access 
- [ ] All servers have correct video routing 
- [ ] All servers have correct Windows configuration 
- [ ] All servers connect to NAS shared folder on startup 
- [ ] All drives are configured correctly 
### Other AV Hardware
- [ ] All networked devices have correct IPs 
- [ ] DHCP Server is active 
- [ ] All cameras are mounted correctly 
- [ ] All cameras are accessible over the network 
- [ ] Video Matrix is accessible via designer software on the Utility PC 
- [ ] UPS is accessible over network 
- [ ] UPS can manage power for every device 
- [ ] Energy monitor and PDU is configured correctly 
- [ ] NAS has been configured and is available as a Windows file share 
### Failover
- [ ] MSVR-01 heartbeats are detected 
- [ ] (sensor server) SSVR heartbeats are detected 
- [ ] MSVR-01 failure causes switch to backup 
- [ ] MSVR-01 recovery causes switch to MSVR-01 
- [ ] MSVR-01 video sync is detected 
- [ ] MSVR-01 video sync loss causes switch to backup 
- [ ] "Reset Status" button sets server back to "Online" status 
- [ ] Failover behavior stops when set to "Disabled" 
- [ ] Failover behavior resumes when set to "Enabled" 
- [ ] Failover media is loaded correctly  
- [ ] Failover media is mapped correctly 
### Front End Displays
- [ ] Pixel map is implemented correctly 
- [ ] Pixel mask is implemented correctly 
- [ ] Media server video signal is free of glitches 
- [ ] Color profiles are neutral. Color displays correctly 
### Front End Audio
- [ ] All speakers have correct routing  
- [ ] No distortion at high levels  
- [ ] No distortion at high or low frequencies 
- [ ] Any maximum audio level requirements required by AHJ cannot be exceeded  
### Sensors
- [ ] All sensors are mounted in the correct orientation  
- [ ] All sensors are accessible from the sensor server 
- [ ] All sensors are configured to their correct IP address 
- [ ] All sensors have matching firmware version