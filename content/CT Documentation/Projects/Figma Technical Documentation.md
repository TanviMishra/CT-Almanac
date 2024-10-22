---
tags:
  - proof-of-concept
---
- [x] Move the templates from Miro to here and see if it is a good fit
	- [x] Try changing headers to see if the styles can be retained
- [ ] Rethink arrows and other visual features
- [ ] figjam/design files sync
- [ ] populate [[Figma vs Miro]]
- [ ] figma plugin
### Version 1
![[Screenshot 2024-08-14 at 18.20.30.png]]
1. Section vs Frames:
	1. Section pros: 
		1. It is better to demarcate the space
		2. Doesn't impact presentation hierarchy
		3. Better for page numbering etc (i.e., no frame conflict will occur)
		4. thought: could also just do without components then
	2. Section cons:
		1. Doesn't allow for seamless reshuffling of pages
		2. Doesn't have any auto layout features
2. Page number plugin
	1. Numerator works janky
	2. Try creating plug-in
		1. https://help.figma.com/hc/en-us/articles/4407260620823--BYFP-1-Overview
3. Footer works ideally
4. Difficulty making tables
5. Autogenerate text/images might be a plus
6. Miro - 
	1. https://www.figma.com/community/plugin/814814551050457760/miro
	2. Could be ideal but ratings suggest it isn't maintained well
7. Arrows solve for now = https://www.figma.com/community/plugin/1296400665621126675/flowify
		1. arrows easier to create manually
8. Interaction flows
	1. some components created
	2. some style variables created
	3. manually drawn arrows
	the effect is a little time consuming but works well
	![[Screenshot 2024-08-19 at 16.20.48.png]]
1. Component:
	1. "Component child" 
		1. can inherit all component properties 
		2. can change inherited property without changing parent
		3. cannot add other things - have to detach for this
![[Screenshot 2024-08-19 at 16.10.36.png]]

