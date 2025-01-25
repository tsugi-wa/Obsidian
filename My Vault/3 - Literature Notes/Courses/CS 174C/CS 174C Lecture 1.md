---
Slides: 
Recording: https://bruinlearn.ucla.edu/courses/198870/modules/items/7144928
---
# C174C
## Grading
Assignments 0%, 20%, 20%
Midterm 20%
Team Project 40%
Max 3 day late -10%/day
No output = 0
tiny-graphics.js WebGL 2.0 and starter code
Textbook Computer Animation Rick Parent
Refresh matrix and vector algebra and math physics in class

branch.education

# C174A refresher
- how video game graphics work (backbone steps ^ for every game ever)
- How gpus work
- How ray tracing works
<iframe width="560" height="315" src="https://www.youtube.com/embed/C8YtdC8mxTU?si=8bYn_ZvRSBDWcD0L" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
- graphics = millions of verticies, triangles, colors/textures, etc. virtual sun
- processed 1s and 0s with computer GPU? 
[[c7b1eab729c5f462fbd12e04b85862f2_MD5.jpeg|Open: Pasted image 20250115104051.png]]
![[c7b1eab729c5f462fbd12e04b85862f2_MD5.jpeg]]
## 1. Vertex Shading
- take all meshes/geometric to calculate 2D view screen, ignore rest
- move each vertex and thus triangle into view screen w/ transformations (C174A)[[cfd80a147522479c34105e7ab3b8bb42_MD5.jpeg|]]
![[cfd80a147522479c34105e7ab3b8bb42_MD5.jpeg]]
	- model (x,y,z in relation to obj)
	- world (pos, rot, scale in world)
	- camera (pos, rot, FOV of camera)
	- view screen (2:51) (x,y,z of view screen)
- GPU cores operations specialized for matrix multiplications
## 2. Rasterization
- convert vertex to pixelated screen of display 
- then shade using texture/assigned picture to colored fragment pixels
- ![[9face2e1898b29b29c10299f6d70e77e_MD5.jpeg]]]]
![[28fd27badaa4af4828a9a9781b99837e_MD5.jpeg]]
- depth/z-buffer for finding which fragments overlap others
![[ea552910069cae9debe3f97218cae7a8_MD5.jpeg]]
![[bdcb294d4ec45a3fb32527bc21d1573b_MD5.jpeg]]
	- need to be pixel by pixel to solve intersecting fragments
	- **super sampling anti-aliasing** SSAA: 16 sampling to blur colors btwn bumpy edge
	- ![[a29edf07db117d40447e7c294bdd99e3_MD5.jpeg]]
	- sent in frame buffer --> display
## 3. Fragment Shading
- directional lighting via shadows, reflections, camera pos, etc.
	- ambient (background, moonlight)
	- diffuse (light source, aka direction of light and direction of triangle surface (normal)
		- if normal align with light (cosine is 1) maximum light intensity coeff
		- clamped so not reach 0, to account scattered ambient light!
		- [[b4d429f189ed10db8693a14a4e12ee9f_MD5.jpeg]]
		- expensive if lots of light sources so limit range of influence + add ambient
		- [[902db15be36c88ba2d6b181dcaf05559_MD5.jpeg|Open: Pasted image 20250115110530.png]]
![[902db15be36c88ba2d6b181dcaf05559_MD5.jpeg]]
	- specular (metallic shiny etc.)
	- improved blinn-phong: 
![[179d941dbd5f1b81cada909fc523c416_MD5.jpeg]]
### Flat vs Smooth shading
- flat: one normal for each triangle, bad on curved surf:
- [[8ab0d759acf727cd25330dc6dbce8926_MD5.jpeg|Open: Pasted image 20250115110751.png]]
![[8ab0d759acf727cd25330dc6dbce8926_MD5.jpeg]]
- smooth: use one averaged normal for multiple triangles to generate more granular, curved fake normals
- [[0dcfcc648a21c3b5417ebcba408b51a3_MD5.jpeg|Open: Pasted image 20250115110919.png]]
![[0dcfcc648a21c3b5417ebcba408b51a3_MD5.jpeg]]
  [[94a946550fab035d4f954a39a66034d2_MD5.jpeg|Open: Pasted image 20250115110820.png]]
![[94a946550fab035d4f954a39a66034d2_MD5.jpeg]]

Ray Tracing: accurate lighting like in CGI renderings
DLSS: deep learning super sampling, take low res and make high res using CNNs 

Types of CPU tech
- CUDA:  regular gpu rendering pipline as discussed
- DLSS: tensor cores

# Ray Tracing
<iframe width="560" height="315" src="https://www.youtube.com/embed/iOlehM5kNSk?si=PTEetcbMgEJAp1E6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Path Tracing (industry standard)
- only possible with tons of server farms & months in 2017, conceptualized 1986

1. modeling everything with triangles/vertices and material data
2. position in world and adjust light to simulate day
3. add camera and render scene to life

reverse sun-->obj-->camera to focus calculations
insane parallel operation (each pixel independent, calculate same thousand rays for each)
primary ray: camera->obj (avg of the chair's base colors)
[[7983310b5ff5c96610c0a209bcf9a217_MD5.jpeg|Open: Pasted image 20250115112207.png]]
![[7983310b5ff5c96610c0a209bcf9a217_MD5.jpeg]]
## Global illumination (10:07)
but not flat image of base colors only, need to account for gradient of blues on pole based on surface facing window/lamp (direct illumination, primary ray --> shadow rays in direction of each light sources) and bounced light from wall (indirect illumination)

shadow rays: rays sent to light source blocked by other triangles so that means no direct light
[[24f9aa1dcda95494c55fed2c00b5e867_MD5.jpeg|Open: Pasted image 20250115113015.png]]
![[24f9aa1dcda95494c55fed2c00b5e867_MD5.jpeg]]

indirect illumination visualization from the walls to shadow part of pole, aka 1. hit obj realize it is in shadow 2. generate secondary rays perpendicular 3. hit wall 4. wall light can reach light then illuminate pole with color of wall, repeat step 2 until step 3 hits something an
[[9520b323c5db5533b224f3044879f7fd_MD5.jpeg|Open: Pasted image 20250115113319.png]]
![[9520b323c5db5533b224f3044879f7fd_MD5.jpeg]]
[[bf73617112c2e379d3e2db8742169c4b_MD5.jpeg|Open: Pasted image 20250115113121.png]]
![[bf73617112c2e379d3e2db8742169c4b_MD5.jpeg]]

[[fb5c26c7744c772b060a4d4abf85fa00_MD5.jpeg|Open: Pasted image 20250115112729.png]]
![[fb5c26c7744c772b060a4d4abf85fa00_MD5.jpeg]]
[[f8cb65cbc130d59e1d37e1ea68f88683_MD5.jpeg|Open: Pasted image 20250115113756.png]]
![[f8cb65cbc130d59e1d37e1ea68f88683_MD5.jpeg]]

adjust settings:
\# rays per pixel
\# of secondary rays
\# of light sources
x number of pixels = total rays required

## Ray Tracing Tasks (in RT chip)

- **BVH traversal**
bounding box hirearchy (BVH traversal )s with half of triangles
- to speed up finding which triangle one ray hits first (depth) by limiting the triangles to find
- aligned to x,y,z of camera for drastically easier calculations
- [[f8c1c1ad989efd315cadec39ac918cf2_MD5.jpeg|Open: Pasted image 20250115114638.png]]
![[f8c1c1ad989efd315cadec39ac918cf2_MD5.jpeg]]
**Triangle intersection:**
- finds which triangle out of 6 in bounding box is hit by ray first

## in video games (shortcut)

low res dupe of obj in scene created and used for ray tracing in camera
light map of low res and translated to high res version shortcut
[[b1cb3656a3edad7b2d87bba41525bd29_MD5.jpeg|Open: Pasted image 20250115115455.png]]
![[b1cb3656a3edad7b2d87bba41525bd29_MD5.jpeg]]
used in unreal engines
screen space ray tracing: image 3d transformations generated by computations i.e. additional depth map (view screen, depth map, normal map) i.e. C174A
- then use ray tracing on reflective surface (i.e. glass, lake surface) of simplified geometry while rendering the rest in C174A 
- con: can only use data from screen so if tree not in view screen, cannot find tree in lake reflection. or behind camera, cant find reflection