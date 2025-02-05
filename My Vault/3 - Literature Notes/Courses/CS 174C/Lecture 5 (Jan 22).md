see Ch3 and Appendix B.5
interpolation and motion curves
## Motion Curves
- software HCI design challenges (ignore)
- keyframing needed
- computer automatically interpolates btwn frames
### Curve form functions (from C174A)
- explicit: y=f(x)
	- only one value from one input, no slopes
- implicit f(x,y)=0
	- good for model but not tangent vectors/joints
	- good for in-and-out tests, computnig normals from gradient
- parametric (x=fx(t), y=fy(t), z=fz(t) for 3D)
	- most convenient for representing motions 
	- **polynomials** of degree L
		- p(t) = a0 + a1 t + a2 t^2 + ... + aL t^L
	- degree 1: 4 coefficients
		- x(t) = at+b
		- y(t) = ct+d
		- [[screenshot of parametric curves]]
	- degree 2 6 coefficients, parabola/quadratic
		- x(t) = at^2 + 2bt + c
		- y(t) = dt^2 + 2et + f
		- alt notation (rational): 
			- [[screenshot of notation]]
			- P0, P1, P2 are control pts
- generate curves from geometric constraints
	- constraints --> polynomial --> motion curve
	- P0,...PL (control polygon) --> given t --> P(t)
	- [[video embed of Freyer Holmer "The Beauty of Bezier Curves]]
	- **bezier curves**
		- lerp: 
	- **de asteljau alg**