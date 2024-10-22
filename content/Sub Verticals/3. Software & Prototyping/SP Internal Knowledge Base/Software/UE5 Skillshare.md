---
tags: []
---
Built using [[Unreal]]
[Initial Tutorial](https://docs.google.com/document/d/1yGZ4nVnt8NaQWXXr3Gb3LZUer9XF80CQnS4whtjceI4/edit?usp=sharing)
[Miro](https://miro.com/app/board/uXjVKgDuxjY=/)

###### Plugins
edit -> plugins
Water (experimental)
Movie Render Queue
Movie Render Queue Passes
Volumetrics
Landmass

###### Asset store
find the asset, select the version of UE that is compatible, add to cart, add to project
most marketplace assets have a tutorial on how to import it into our own file

###### Landscape
Selection mode -> landscape -> can sculpt

window -> place actors -> selection mode -> water body ocean

blueprint -> landscape custom brush landmass-> makes a spline
(add a new layer so you're not working on the water layer)
in properties - edit falloff, blur, curl noise

save everything (not just the level) -> cntrl + alt + shift + s 

adding quixel assets

for directional light turn "cast ray chase shadow" off

water body ocean -> wave source -> double click to get editor for the waves
 for still water: settings in miro
###### Glass
if you want thickness, make the material two-sided
add quixel materials as high quality
###### Foliage
go to foliage tab
add all trees to your foliage sections
select a few, change density, adjust brush size and add foliage
MAI - master material

###### Sequence
cinematics - camera actor
