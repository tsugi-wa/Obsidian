defining social justice is tough - ongoing? b4 readings?
tied with states/society/status so more recent ? 
a right or protection for everyone from some state
- otherwise, technically "oppressed"
**Oppression:**
becomes internalized (i.e. black ppl not comfortable performing without blackface

spatial justice: outcome + proces
- political and socioeconomic locating/organizing of space
- if country trying to increase injustice, leads to collapse/world wars??? (edward w. soja) what bout China, north korea?
- gentrification: why bad? driving out ppl, pushing costs of housing, 
- space socially produced/changed i.e. university space vs mcdonalds
- [[e87b61624844d5391f5bb9c5774c0208_MD5.zip|Open: ne_10m_urban_areas.zip]]
![[e87b61624844d5391f5bb9c5774c0208_MD5.zip]]


ex: list of places is gazetteer
sort id
publication id
title
buried date
contents
notes
location_url

location id: https://www.geonames.org/5368361/los-angeles.html 
the 5368361
https://www.getty.edu/research/tools/vocabularies/tgn
https://whgazetteer.org/search/
https://www.openstreetmap.org/relation/207359
[[b3902a0e5e40f96955a3e987592577c8_MD5.jpeg|Open: Pasted image 20241010154938.png]]
https://pleiades.stoa.org/
linked open data LOD: not just simple maps, ecology, images, etc.
how though? 
- addresses in data - either geocode or reconciliation
**reconciliation: **
- annotate images etc
- recogito.pelagios.org
![[b3902a0e5e40f96955a3e987592577c8_MD5.jpeg]]

## Lecture 3
LiDAR apps like TOR, airplane measure spaces
vs Photogrammetry - aerial lightup
https://docs.google.com/presentation/d/1WqrVh-MVQOjhwPkFLuTwTtKKTxGiRZLV4V7oDPmoZxo/edit#slide=id.g222e7f52f09_3_0


[[dc559df36a4fc63cb61c61bd7b7731fd_MD5.jpeg|Open: Pasted image 20241017155152.png]]
![[dc559df36a4fc63cb61c61bd7b7731fd_MD5.jpeg]]

[[c30c72d014a1ab14644c8c2efc085f8f_MD5.jpeg|Open: Pasted image 20241017155506.png]]
![[c30c72d014a1ab14644c8c2efc085f8f_MD5.jpeg]]

[[518866deed416c59ce4986af0aa7681d_MD5.jpeg|Open: Pasted image 20241017155605.png]]
![[518866deed416c59ce4986af0aa7681d_MD5.jpeg]]

[[4571b3b07b47f2fd63b2b2902638bb49_MD5.jpeg|Open: Pasted image 20241017155625.png]]
![[4571b3b07b47f2fd63b2b2902638bb49_MD5.jpeg]]choose ESRIShapefile instead of GJSON
[[3e5c4ad2e7365ee5fbdfca6c42ec08ab_MD5.jpeg|Open: Pasted image 20241017155800.png]]
![[3e5c4ad2e7365ee5fbdfca6c42ec08ab_MD5.jpeg]]
output: ^

Join -> + -> join layer, field, target field (id to id) -> joined field (check it ) -> check all fields you want to keep -> export (save to disk not RAM)

[[feb47ff39856e79d3ccf61caed802dd8_MD5.jpeg|Open: Pasted image 20241017161935.png]]
![[feb47ff39856e79d3ccf61caed802dd8_MD5.jpeg]]
[[7d76818370de96e78af3015d7e5b3ba1_MD5.jpeg|Open: Pasted image 20241017162056.png]]
![[7d76818370de96e78af3015d7e5b3ba1_MD5.jpeg]]
4326 -> 3857 (google projection)

[[fcad3af836e36411e241d672bfc4b481_MD5.jpeg|Open: Pasted image 20241017162409.png]]
![[fcad3af836e36411e241d672bfc4b481_MD5.jpeg]]
[[185359c8aa954f796fe7ca01f4c61534_MD5.jpeg|Open: Pasted image 20241017162423.png]]
![[185359c8aa954f796fe7ca01f4c61534_MD5.jpeg]]
specify desired buffer size and unit type
i.e. 100 mile buffer: each point is fixed at 100 mile radius:
[[42b381b4e1b6b18c3ba4a36f9afff5bd_MD5.jpeg|Open: Pasted image 20241017162522.png]]
![[42b381b4e1b6b18c3ba4a36f9afff5bd_MD5.jpeg]]

parmeters join -> buff - > intersect

Example of other possibility tools: Whittle down to specific state or county by intersecting with that county shp file. 
[[71b92da871eebc0ac2c75c551c022796_MD5.jpeg|Open: Pasted image 20241017163602.png]]
![[71b92da871eebc0ac2c75c551c022796_MD5.jpeg]]

to filter CAlifonria only
[[879ef8f0b232978eea3994b1b07d8acb_MD5.jpeg|Open: Pasted image 20241017163849.png]]
![[879ef8f0b232978eea3994b1b07d8acb_MD5.jpeg]][[073412ce8dc243e26caf5471431e937d_MD5.jpeg|Open: Pasted image 20241017163926.png]]
![[073412ce8dc243e26caf5471431e937d_MD5.jpeg]][[f75cfb592cafbe49636adeb5ade759a6_MD5.jpeg|Open: Pasted image 20241017163940.png]]
![[f75cfb592cafbe49636adeb5ade759a6_MD5.jpeg]][[13882d874ef19a3a9c16425113ee3edc_MD5.jpeg|Open: Pasted image 20241017163956.png]]
![[13882d874ef19a3a9c16425113ee3edc_MD5.jpeg]]
click edit pencil in california layer, select state provinces shp, click california, ctrl+C, select cali again, Ctrl+V, then click floppy disk to save layer. 

[[fdb7a5c78207bc0d41c74d0bd0c7abcf_MD5.jpeg|Open: Pasted image 20241017164029.png]]
![[fdb7a5c78207bc0d41c74d0bd0c7abcf_MD5.jpeg]]

Then to intersect
[[7409bc6641b03cdb64fcd948eeb84044_MD5.jpeg|Open: Pasted image 20241017164521.png]]
![[7409bc6641b03cdb64fcd948eeb84044_MD5.jpeg]]
or [[bd2752e09e6cf49a8cfa6d7a248f45d6_MD5.jpeg|Open: Pasted image 20241017164609.png]]
![[bd2752e09e6cf49a8cfa6d7a248f45d6_MD5.jpeg]]
[[c32724a8f963dff24142fd8124836197_MD5.jpeg|Open: Pasted image 20241017164624.png]]
![[c32724a8f963dff24142fd8124836197_MD5.jpeg]]
output:
[[0cf3838fdf64a175da25397822a1b328_MD5.jpeg|Open: Pasted image 20241017164630.png]]
![[0cf3838fdf64a175da25397822a1b328_MD5.jpeg]]

## Lecture 5

[[fe4a02a4d326c8b389eeb07f8e848811_MD5.jpeg|Open: Pasted image 20241024160103.png]]
![[fe4a02a4d326c8b389eeb07f8e848811_MD5.jpeg]]

in attribute table to see row:
[[0bc717b9894d2cc11fed7310f12213f5_MD5.jpeg|Open: Pasted image 20241024160422.png]]
![[0bc717b9894d2cc11fed7310f12213f5_MD5.jpeg]]
[[e89b070f79ab6658147526e5899bce64_MD5.jpeg|Open: Pasted image 20241024160535.png]]
![[e89b070f79ab6658147526e5899bce64_MD5.jpeg]]

calculate area of each row and add to attribute table
if you want specific units project to different ES25 first then $area:
[[f4628444bd0e766928d9b0354bda4bae_MD5.jpeg|Open: Pasted image 20241024160734.png]]
![[f4628444bd0e766928d9b0354bda4bae_MD5.jpeg]]

buffer -> parammeters tab --> dissolve result checked --> Run --> combine all segments smoothly

right click shape file --> Filter --> 

"building" NOT IN ('yes', 'farm')
"highway" NOT IN ('footway', 'path', 'unclassified', 'track') AND "highway" IS NOT NULL



# Lecture 6
"Truthful" vs "Factual"
- disco sales rocketing at year? invest now!
- Choropleth maps (color gradient)
	- good for predefined regions/states, immediate visual cue
	- assumes uniformity across region
- Proportional Symbol Maps
	- puts points on geographic center of region not where population/data really is
- heat maps
- dot density
- cartography - distorted maps to represent values (i.e. resized countries)
- flow maps



## Exporting maps in qgis
Project -> New Print Layout -

[[b1d7e7f3d8b0a2539840911de7ca180e_MD5.jpeg|Open: Pasted image 20241031155154.png]]
![[b1d7e7f3d8b0a2539840911de7ca180e_MD5.jpeg]]
[[1925faa731156cafb0d15ae50825f1e3_MD5.jpeg|Open: Pasted image 20241031155217.png]]
![[1925faa731156cafb0d15ae50825f1e3_MD5.jpeg]]
to update to original map
[[cdfa2580f847982bded383ddb33d0ada_MD5.jpeg|Open: Pasted image 20241031155554.png]]
![[cdfa2580f847982bded383ddb33d0ada_MD5.jpeg]]
can change to miles
and add legend too
to edit properties:
[[34a7d4b2d26aee3b10c78881670ad2e7_MD5.jpeg|Open: Pasted image 20241031160413.png]]
![[34a7d4b2d26aee3b10c78881670ad2e7_MD5.jpeg]]

[[6803152395300ed3f48b840aebabb59d_MD5.jpeg|Open: Pasted image 20241031160645.png]]
![[6803152395300ed3f48b840aebabb59d_MD5.jpeg]]
[[a5e12b69d92c4c9d4f18fe0c03c80775_MD5.jpeg|Open: Pasted image 20241031160937.png]]
![[a5e12b69d92c4c9d4f18fe0c03c80775_MD5.jpeg]]
can use inkscape to adjust all borders, icons, text label size, etc

### qgis2web
[[4c5254ae2d7d24b6d0c6815ab837c5c7_MD5.jpeg|Open: Pasted image 20241031161704.png]]
![[4c5254ae2d7d24b6d0c6815ab837c5c7_MD5.jpeg]]