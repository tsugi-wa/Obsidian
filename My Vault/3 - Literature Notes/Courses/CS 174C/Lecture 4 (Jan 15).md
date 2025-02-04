
Toy Story behind the scenes :
- fur, weather, clothing animated at the end via physics simulation AFTER posing animation (sometimes exaggerated)
- virtual lights strategically placed for mood, tone, etc.

 **rotation representations** (all have pros/cons, we prioritize interpolation for smooth animations)
## **Rotation matrix (CS C174A)**  
- ![[221010f486dfa9bc3ee5d5009c265cea_MD5.jpeg#invert]]
- det(R) = +1
## **Fixed angle (POV of world)** vs **Euler angle (POV of obj)**
- order of x,y,z combination rotations all ok to achieve any orientation
- ==Euler angle: z-x-y  equivalent to Fixed angle: y-x-z (proof in textbook)==
	- **GIMBAL LOCK: loss of rot degree of freedom.**  when 2nd ordered axis rotated 90 like in 1st parent ordered axis
		- weirdness when interpolating Euler angles for animation bc yaw changes plane of rot. 
		- trying to minimalize rotation when interpolating btwn two orientations, but may have weird behavior with euler. 
		- soln: reorient euler axis order (x,y,z) to minimze chance of gimbal lock

	- ![[57f36b553d93fab8408b764fc126af92_MD5.jpeg#invert]]
	- Guerrilla CG project tutorial of Eulers.
	- <iframe width="560" height="315" src="https://www.youtube.com/embed/zc8b2Jo7mno?si=SGQjZOb8d0jVhEYW&amp;start=18" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 
## **Axis-angle** (alternative) 
- rotate quad around vector u counterclockwise to angle Beta
- <iframe width="560" height="315" src="https://www.youtube.com/embed/z8S1axQbBkk?si=tNOPigvi-fmsvW_Q&amp;start=306" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
	- vproja = u
	- c = P
	- s = Q
- equivalent rotation transf. matrix? R_u(beta) = 
	1. rotate by y axis via theta to align u with xy plane
	2. rotate by z axis via neg phi to align with x axis
	3. x-roll around x by angle beta
	4. undo step 2 rotate by z
	5. undo step 1 rotate by y
	- ![[800e33496f64b5a97fd4bc5acca500f0_MD5.jpeg#invert]]
## **Quaternion**  (see B.3.4)
- x,y,z is a point
- t is rotation around 	
- still has drawbacks like gimbal lock, cannot do animation curve instead TCB\
- <iframe width="560" height="315"  src="https://player.vimeo.com/video/2649637?badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479#t=271.843" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media"></iframe>
### first in 2D
- complex numbers plotted on graph (x=real, y=imaginary)
- convert a+ib format into polar coords using Euler's formula  (cos(theta) + i sin(theta)) = e^(i theta)
- <iframe width="560" height="315" src="https://www.youtube.com/embed/HozImwsr2ho?si=354081l5EFIrTin7" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
- ![[660bcc16f0dca55ce56b7e5018e966ce_MD5.jpeg#invertW]]
### extrapolated to 3D
2d vs 3d:
![[e226842d08c8a9f4169d939b84b71714_MD5.jpeg]]
use 3 imaginary numbers (i,j,k) instead of just i
- aka: q=a+bi==+cj+dk==
- i^2 = j^2 = k^2 = -1
- ij = -ji = k
- jk = -kj = i
- ki = -ik = j
- properties
- q = [a,b,c,d] = [s,x,y,z] = [s,v]
- [s1, v1] + [s2,v2] = [s1+s2, v1+v2]
- [s1, v1] \[s2,v2] = \[s1s2 - v1.v2, s1v2 + s2v1 + v1 x v2]
	- scalar result: s1s2 - v1.v2  (subtract more when the two are very similar)
	- vector result: s1v2 + s2v1 (weighted avg) + v1 x v2 (vector normal to either one)
- (q1q2)q3 = q1(q2q3)
- q1q2 != q2q1
- |q| = sqrt(s^2 + x^2 + y^2 + z^2)
- other properties
- identity: q(1,0,0,0)
- inverse:  q^-1 = (1/|q|)^2 * (s,-v)
	- thus q^-1 q = qq^-1 = (1,0,0,0) identity
	- like matrix:  (pq)^-1 = q^-1 p^-1 
- conjugate of q = q^* = (s, -v)

###  **usage in 3D orientation:**
Unit quaternions (|q(s,x,y,z)|=1)
- inverse of unit quaternions == its conjugate
- general form:  q=(cos(theta), sin(theta) **v**)   where v is unit vector
	- |q| = sqrt(cos^2 theta  + sin^2 theta * 1) = sqrt(cos^2 theta + sin^2 theta) = sqrt(1) = 1 
	- equivalent to an orientation: rotate by 2 x theta around v (**axis of rotation**)
		- q=-q when interpreted as orientation
- ==rotate vector u by quaternion q?==
	- q = (s,x,y,z) = (s,**v**)
	- point(vector) u = (x,y,z), then u-vector = (0, x,y,z)
	- u' = Rot(u) = q u-vector q^-1
		- https://eater.net/quaternions/video/intro
		- To rotate around z counterclockwise in 270 degrees? **double cover (any orientation has two representations) **
		- https://eater.net/quaternions/video/doublecover
			- first adjust q = cos(theta)sin(theta)(ai + bj + ck)   so that unit vector coincides with z (a=0, b=0, c=1)
			- then set theta to desired degrees/2 = 135 degrees:   q=cos(135)sin(135)(0i + 0j + k) = -0.71+0.71k
			- equivalent to that is q=cos(-45)sin(-45)(0i+0j+k) = 0.71+0.71k
		- https://eater.net/quaternions/video/stereo4d
			- when just manipulating one point with one quaternion (qu)
			- changing scalar to 1 makes point go to origin, but decreasing scalar moves point down in the direction that the other compensating vector is growing (i for x, j for y, k for z)
			- with scalar=1 and changing two vectors (i.e. i and j) it will rotate the point along the other vector's direction (i.e. k or z axis) around origin
		- https://eater.net/quaternions/video/quatmult at 5:04
			- demonstrating how order matters in multiplying quaternions, i.e. opposite directions of rotation (RHR for first q, LHR for second q)
		- https://eater.net/quaternions/video/rotation at 1:30
			- first q to 90 degrees warps the sphere but rotates the desird y-axis (bj=1j)
			- second q with -90 degrees warps the plane back into sphere while still rotating desired axis
			- ![[Pasted image 20250203152135.png#invertW]]
- ==successive rotations==
	- ![[Pasted image 20250204084741.png#invert]]
	- rotations by -q instead of q = same thing (**double-cover**).
		- q=(theta, v), so q'=(-theta, -v)=(2pi-theta, -v):
		- q = \[cos(theta/2), sin(theta/2)v]
		- q' = \[cos((2pi-theta)/2), sin((2pi-theta)/2)(-v)]
		- q' = \[cos(pi-theta/2), -sin(pi-theta/2)v]
		- q' = \[-cos(theta/2), -sin(theta/2)v]
		- turning counterclkwise around j vector (y axis) equivalent to looking at y axis in opposite direction (-j vector) and turning clkwise 45 degree
		- ![[976f7d3d98ccc1400acdfdd58212c5de_MD5.jpeg]]
	- equivalence w/ axis-angle:  (theta, v) in axis-angle (rotate by theta around v) == R(theta,v) = q = \[cos(theta/2), sin(theta/2)v]
### Interpolating Quaternions
- linear   
	- convex: q = lerp (q1, q2, t) = (1-t)q1 + tq2   t in range \[0,1] ![[0dd884e61d87f42b761eec417d83ffa1_MD5.jpeg]]
	- spherical (path along sphere): btwn two thetas NOT quaternions:
		- theta = q1 * q2
		- slerp(q1, q2, t) = sin((t-1)theta)/sin(theta) q1 + sin(t theta)/ sin(theta) q2![[24651241fbabdb582b0e97aa5fb75c98_MD5.jpeg]]
		- issues: need to renormalize to unit quaternion after calculation
		- first order discontinuity at keyframes (next lecture)
			- need polynomial interpolations (along unit sphere) for smooth results
			- ==see on Spherical Linear Interpolation (Slerp) with demos==
- non-linear
## - **Exponential map**
- three params: 
- specify angle/axis of rotation v1,  magnitude/amt of rotation v2, 
- best for physics simulation (going between angles)
- n times 2pi singularity (blows up) and numerically unstable if rotate by tiny angles (|v| close to zero) see ==Grassia 1998== for solution (reversed notation \[v,s])
- ![[ef419bd408dd5460f55a2b232d11c4d0_MD5.jpeg]]

## Pros and cons:

|                 |                                                     |                                                                 |                                                                                                         |                                                                                                               |
| --------------- | --------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Representation  | Description                                         | Uses                                                            | Advantages                                                                                              | Disadvantages                                                                                                 |
| Rotation Matrix | 3x3 orthonormal submatrix of a 4x4 matrix           | Final drawing, internal representation, transformations         | Direct transformation, easy concatenation, easy inverse.                                                | Difficult for interpolation, roundoff errors, needs 9 parameters.                                             |
| Fixed Angle     | Ordered rotations around world coordinate axes      | Object orientation.                                             | Intuitive, compact, easy to implement                                                                   | Gimbal lock, difficult interpolation, non-intuitive incremental rotations, not suitable for smooth animation. |
| Euler Angle     | Ordered rotations around local object axes          | Object orientation in display, user interfaces, motion curves.  | Intuitive, compact.                                                                                     | Gimbal lock, difficult interpolation, not suitable for smooth animation.                                      |
| Axis-Angle      | Axis vector and rotation angle                      | Rotating objects around an arbitrary axis                       | Intuitive, minimal representation.                                                                      | Difficult to concatenate rotations, interpolation requires interpolating axis and angle separately.           |
| Quaternion      | 4-tuple (scalar and 3D vector)                      | Internal representation, smooth animation, avoiding gimbal lock | Avoids gimbal lock, good for interpolation, easy concatenation, unit quaternions equiv. to orientations | Less intuitive, can have flipping issues, more computationally complex.                                       |
| Exponential Map | 3D vector, direction is axis and magnitude is angle | Physics simulation                                              | Compact, continuous at origin, well-formed derivatives.                                                 | Singularities, difficult to concatenate rotations.                                                            |


