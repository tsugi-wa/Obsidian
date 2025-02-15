## Historical Significiant Computer Animations (Ch1 of textbook)
1st computer animation:
- 1961 Sweden "Rendering of a planned highway" on BESK vacuum tube computer (vector graphics on CRT display)
- 1972 3D computer graphics from University of Utah
	- 1st computer vision thesis Roberts from MIT
	- 1st computer graphics thesis from Ivan Sutherland from MIT (Ed Catmull, later founder of Pixar)
	- ![[929f1645f96c3ca50ba2d419ca552b6e_MD5.jpeg#invert]]![[89133a399597a3532c0112917ed2eaa6_MD5.jpeg#invertW]] 
	- convert 3D model of hand/face with labeled polygons into 3D model that can be puppetted w/ cosine interpolation
- 1980 Pixar b4 Pixar (George Lucas, Star Wars later, Ed Catmull)
	- famous Utah teapot model, freeflying camera of terrain
	- ball particle effects, shark in land
- 1984 Pixar's (LUCASFILM) Andre & Wally B. (first involving characters)
	- used Cray supercomputer & VAX digital equipment, revolutionary
- 2007 documentary: "The Pixar Story" bailed out by Steve Jobs, John Lasseter and Ed Catmall
	- art challenges tech, tech inspires art
	- 1986 "Luxo Jr." nominated animated short film award. 1st CGI one, 
		- entirely hand-positioned (by ex-Disney animator John), i.e. vibrating wires of lamps NOT physics em.
	- 1987 "Red's Dream" midst of Moore's law
		- cartoon physics of clown fall after realizing
	- 1988 "Tin Toy" 1988 academy award animated short film
		- inspiration for toy story (1995)
		- first attempt to animate human (baby), extremely difficulty
	- 1989 "Knick Knack"
		- uses Ray tracing (render-man pkg) last animated short by Lasseter
	- 1997 "Geri's Game"
		- first time using physics (jacket is sim. cloth) for Jan Pinkava

## C174A math review (in Ch2 and referenced Appendix B sections)
### **vectors** (n-tuples): bold lowercase
- vs **scalars**: italic lowercase
- **magnitude** = |v| = sqrt(x_1^2 + x_2^2 + ... + x_n^2)
- **normalized vector** = v/|v| to get **unit vector** (|v|=1)
- **addition**: x+y (only if x and y same length)
- **mult. w/ scalar:** ax
- **properties** same as addition
#### **linear combination of m vectors**: 
- w = 2**v1**  + .... +  6**vm**
- **affine comb.** all coefficients add up to 1
- **convex comb.** all coefficients are non-negative
- **linear independent vectors v1...vm :** if a1 **v1** + .. + am **vm** = 0  iff all coefficients=0
- **base vectors/generators:**
- N-D space, needs min. N vectors (**basis of vector space**) to generate all (i.e. R^3, i, j, k) 
- **standard unit vectors**  (i.e. R^3, i, j, k) 
	- represent all other vectors in space as linear combination of basis vectors
#### ==**dot product**== 
- **w** dot **v** = scalar (sum of all scalars in w times v)
	- **ab=ba**, (s **a**)**b** = s(**ab**) , |**b**|^2 = bb
	- ==**a b** = **|a||b|** cos(theta)==  aka how close they are
		- perpendicular: dot product=0
		- obtuse: <0    acute: >0
		- ==**projection of vector on another vector**==
		- ![[c0b011a4cf72e7136ceb98162c45b42a_MD5.jpeg#invert]]
		- decompose u into two components (parallel to v and perpendicular to v)
		- parallel-to-v component of u = projection of u onto v
		- perpend-to-v component of u = u - parallel component
#### ==**cross product**== 
- only R^3, outputs a vector **orthogonal** to both inputs
- ![[67d9342b39e82b8bcdeb87e396f6b4d4_MD5.jpeg#invert]]
- i→j→k→i   mnuemonic: follow arrow = positive result, else neg:      i x j = k     i x k = -j       j x k =i
- thus antisymmetric:   a x b = -b x a
- linearity:  a x (b+ c) = a x b + a x c
- homogeneity:   (sa) x b = s(a x b)
- orthogonal output:   (a x b)a = (a x b)b = 0
- ==|a x b| = |a||b| sin(theta)== aka how different they are
	- usage: find ==area==
	- ![[b8e739208c0859b3ad971ef950ef6c43_MD5.jpeg#invert]]

## Matrices (txtbook 2.2)
- bold Upper-case i.e. **A_i_j**
- **zero** matrix, **identity** matrix, **symmetric** matrix (A_i_j = A_j_i for all in A_n_n, OR A = A^T)
- **inverse** of a matrix:  ==MM^-1 = M^-1 M = identity matrix==
- properties (weird order mattering)
	- AB != BA
	- f(AB) = (fA)B
	- ==(AB)^T =B^T A^T==
	- ==(AB)^-1 = B^-1 A^-1
- ==**dot product**==
	- a dot b = a^T b
	- ![[fc16a5c5dc4a06ee2f71a061e1c0667b_MD5.jpeg#invert]]
### **homogeneous representation:** vector v (dir, no pos) vs point P (pos, no dir) in space
- Q-P = v
- P+v = Q
- thus:  vector add 4th dimension:  v=0,  P=1
- **coordinate system**:  3 vectors (**a,b,c**) + point (origin) = ==\[**a b c** O]== = 4 x 4 homogenous matrix
	- P-O = vector combination of a,b,c (from origin to P)
	- aka P = O+vector combination
	- so wrt the coord sys =
		- vector: ==\[**a b c** O] \[v1 v2 v3 0]^T==
		- point: \[**a b c** O] \[p1 p2 p3 1]^T
#### **affine transformations (all coefs add up to 1)**
- all compositions of affine transfr. = affine transf.
- any 3D affine transf. can be performed as series of elementary transf.
- 
- **![[21b95fc8074fb59c64ee91eb7cdacea5_MD5.jpeg#invert]]
- **orthonormal matrices:** all col and row vectors of matrix are unit vectors & orthogonal to each other
	- aka M^-1 = M^T
#### **change of basis w/ transformations**
- ![[bad16d3269234328ce7dbb28e544ef72_MD5.jpeg#invert]]
