see Ch3 and Appendix B.5
interpolation and motion curves

Motion Curves
- software HCI design challenges (ignore)
- keyframing needed
- computer automatically interpolates btwn frames
### Curve form functions (from C174A)
- **explicit**: y=f(x)
	- only one value from one input, no slopes
- **implicit** f(x,y)=0
	- good for model but not tangent vectors/joints
	- good for in-and-out tests, computnig normals from gradient
- **parametric** (x=fx(t), y=fy(t), z=fz(t) for 3D)
	- most convenient for representing motions 
	- **polynomials** of degree L
		- p(t) = a0 + a1 t + a2 t^2 + ... + aL t^L
	- degree 1: 4 coefficients
		- x(t) = at+b
		- y(t) = ct+d
		- ![[9384f3556c4ccfcd146b0cbe4fe5bc25_MD5.jpeg#invert]]
	- degree 2 6 coefficients, parabola/quadratic
		- x(t) = at^2 + 2bt + c
		- y(t) = dt^2 + 2et + f
		- alt notation (rational): 
			- ![[9cda5533b0475692d32f07da1d28e0a7_MD5.jpeg#invert]]
			- P0, P1, P2 are control pts
- generate curves from geometric constraints
	- constraints --> polynomial --> motion curve
	- P0,...PL (control polygon) --> given t --> P(t)
	- ![[6cf88c88dad679006d89e21995ad6c8d_MD5.jpeg#invert]]
		- 
### **bezier curves**
- lerp w/ 3 points (quadratic parabola curve), works with any point and any # of points
- <iframe width="560" height="315" src="https://www.youtube.com/embed/aVwxzDHniEw?si=5Jnc-BaeRZR1pXJ5&amp;start=141" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
- ![[ef4c188316b5fdb586a5567e18e968ff_MD5.jpeg#invert]]
- cubic bezier curve the most common! De Casteljau's Algorithm --> Bernstein Polynomial Form
- <iframe width="560" height="315" src="https://www.youtube.com/embed/aVwxzDHniEw?si=qkoQ99L0PukCEqvu&amp;start=238" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
- ![[9801b7c64c785d5255dcda2dc615c465_MD5.jpeg#invert]]
- ![[fda47e0c31de8956d5f67e0262c0e05e_MD5.jpeg#invertW]]
- ![[365087e1160a6087dc8eecbaf70b756a_MD5.jpeg#invertW]]
- **de asteljau alg**:
	- P(t) = (1-t)^3 P0 + 3(1-t)^2 t P1 + 3(1-t) t^2 P2 + t^3 P3
	- **interpolation**: between P0 and P3
	- **approximation**: between P1 and P2
- all forms (including new matrix form)
	- ![[a53d269bd330fddde5b4769c1dab712c_MD5.jpeg#invertW]]
- derivatives (dP/dt):
	- deriv of Bezier curve always Bezier curve of one degree lower but **different** control points (i.e. control tangents)
	- 1st & 2nd deriv
	- <iframe width="560" height="315" src="https://www.youtube.com/embed/aVwxzDHniEw?si=5k6MLaxVgNJKnDFw&amp;start=378" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
	- ![[fe082c76accecc9bd0f5700351900768_MD5.jpeg#invert]]
	- ![[4e9f9698e9b1b64a743fc0ee0486d1cd_MD5.jpeg#invert]]
	- magnitude of tangent/deriv = speed of the turn
## Custom curves
### Cubic Curve
![[4b7fa17035ae09ec8dc6007df916e897_MD5.jpeg#invert]]
### Hermite Curve
good for specifiying vehicle particular velocity at certain points in space
![[2198f2a7f5525b23a1e82d600f3a8938_MD5.jpeg#invert]]
### COMPARED
![[cb844135a43bb38079e4ac80e4ae44f2_MD5.jpeg#invert]]

### Hermite to Bezier
![[ab54ea5c9f9c01ccfc51b5b300644c10_MD5.jpeg#invert]]
## Splines
![[95c1aff32df82c1607f7458e1935f0fc_MD5.jpeg#invertW]]
- piecewise polynomial function for path
- why splines for paths? up to cubic degree (fast to compute, easy to manipulate, stable, etc.)
- **knots**: end of one polynomial, start of another
- **control points**: knot + associated shapes
- ![[f82328f7e0a6444dfe811e4303caf608_MD5.jpeg#invert]]
### **continuity**
- parametric: 
	- ith derivatives of P (for i=0...k) always exist and continuous for all t in \[a,b]
	- k-smooth / kth order continuity
- geometric: 
	- ith derivative of P to the left == some constant of ith derivative of P to the right
#### parametric
![[4077c2d137ac2d2ad18cafe7545e4056_MD5.jpeg#invertW]]

#### geometric continuity
![[9b8ecc647ead7638cf45e9127e938742_MD5.jpeg#invertW]]
![[21b3042421139a4749ec457f83144f3e_MD5.jpeg#invertW]]
#### COMPARED
![[821467eddbd2c7a4b6cb53d4077770a9_MD5.jpeg#invertW]]