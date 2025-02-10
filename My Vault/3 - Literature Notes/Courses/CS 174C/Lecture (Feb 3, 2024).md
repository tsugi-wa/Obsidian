Particles
- mass, velocity ,acceleration, color, age, temperature, orientation
**Fields: **
- region of space/domain, where each pt mapped to value(s)
- ie. temperature in room, get temp at that point
- i.e. vector space, local wind in room
- i.e. within a block has associated matrix of elasticity

basic particle animation:
- velocity field v(x,t) x=point in space, t=time
- delta t = simulation time step = 1/30 sec if 30fps
-  get next pos of particle x(t) by integrating over time step
	- Forward Euler integration:
		- use definition of derivative to solve for new pos
		- ![[95515a82429b7256fae48fa572fabd4d_MD5.jpeg]]
		- v(x(t),t) = cur velocity of cur pos in vector field x dt + cur pos to move us 
- velocity fields
	- pre-designed (explosions, vortices swirl around center)
	- noisy (smooth rand # field not independently random)
	- simulation (interpolate velocity from computed grid i.e. fluid stir/slosh, smoke)
- seeding particles
	- where to add them?
		- at single point source
		- randomly on surface or within volume
		- where there aren't many particles
	- when?
		- beginning
		- \# per frame
		- when insufficient particles somewhere
	- other attributes? velocity? i.e. in relation to explosion
- drawing/rendering
	- multiple per pixel?
		- emit or absorb light? i.e. fire embers
		- alpha-blending, shadows, depth-order, etc.
	- anti-aliasing: smooth particle edges
	- radius particles: Kernel function, other behavior i.e. Gaussian additive w/ 2 close particles
- motion blur
	- line between positions instead of dot? i.e. open shutter time
	- alpha blending, or use spline curve
	- particle radius? burning? reduces in size? 