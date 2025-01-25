---
Slides: 
Recording:
---
# B.E: How Graphics Cards work
<iframe width="560" height="315" src="https://www.youtube.com/embed/h9Z4oGN89MU?si=Ny6MMbhU-QTU2f0o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

How many calculations for gaming?
- 100 mil /sec for Mario 64 from 1996
- 100 bil / sec for Minecraft from 2011
- 36 tril / sec for Cyberpunk 2077
## GPU vs CPU analogy
- cargo capacity = calculations/data processed
- speed of ship = rate of calculations processed
- GPU: massive cargo ship 
	- ~10k cores
	- bulk contents limited to travel between certain ports
	- limited to basic arithmetic calculations (no OS, interface, etc.)
- CPU: jumbo jet airplane
	- ~24 cores
	- more flexible in:
		- cargo (passengers, packages, or containers) aka instructions/programs (OS, networks, hardware/app etc.)
		- destinations (airports)
## GPU hardware architecture
- ==PCB== (printed circuit board) w/ mounted parts
- ==GPU== (brain chip i.e. GA102)
	- 28.3 bil transistors, 10752 cuda cores, 336 tensor cores, 84 RT cores
	- processing cores w/ hierarchical organization of 7 clusters (==GPCs==)
		- further divided into 12 streaming multiprocessers (==SMs==)
			- each containing 4 ==warps==
				- w/ 32 ==Cuda/shading cores==
					- for binary calcs (+, -, etc.) for video games
				- w/ 1 ==tensor cores==
					- for matrix multiplication for geometric transform., NN, AI
			- each containing 1 ==RT core==
				- for RT algorithms
- Nvidia 3080, 3090, 3080ti, and 3090ti all use same GA102 architecture
	- why? remove small defects in highly repetitive design during production and deactivate it.
	- categorized by # of defects: 
		- 3090ti = flawless 10752 cuda cores
		- 3090 = 10496 cores working
		- 3080ti = 10240 cores working
		- 3080 = 8704 cores working (~16 damanged streaming processers)
			- ![[53e634f9cb559f55a3b0ed08227b4666_MD5.jpeg]]
	- also differ by clock speed and amt of graphics memory for GPU (GDDR6X)
### cuda core design
- ~410k transistors per cuda core
	- 50k transistors performs **A x B + C**, or **fused multiply and add (FMA)**, most common operation
		- Half of cuda cores execute FMA using 32-bit floating-point numbers
		- Other half use 32-bit integers or 32-bit floating-point numbers
	- Other sections accommodate negative numbers and perform other simple functions like bit-shifting and bit masking, collecting/queuing/accumulating incoming instructions, ops, and outputted results
- each core: calculator doing 1 multiply and 1 add per clock cycle 
	- i.e. 3090: 2 calculations per second x 10,496 cores x 1.7 gigahertz clock = 35.6 tril calcs/sec
- only 4 Special function units per streaming multiprocessor
	- for more complex operations (division, square root, trig functions) 
![[069d579ab2152e7cffb9b787a88b78be_MD5.jpeg]]
- green: NVLink controller
- sides: 12 graphics memory controllers
- bottom blue: PCIe interface
- 6MB L2 cache: small chunks of scene from GDDR --> GPU
- gigathread engine (manages inside SMs/GPCs)
### card components
- power connector
- PCIe to motherboard
- output ports
- voltage regulator module: takes 12V power --> 1.1 V to GPU
- heatsink and heatpipes to radiator fans of gpu
- graphics memory chips (GDDR6x SDRAM)
	- loading screen moving 3D models of scene from SSD --> GDDR
  	![[bf2f4e5ddcdf1188a04fd6c139fbe8ba_MD5.jpeg]]
	- 24 GDDR chips are loading data quickly to cargo ship like loading cranes (GPU)
		- combined: (bus width = 384 bits a time)
		- total bandwidth = 1.15 TBs/sec vs DRAM of CPU (64 bus width, 64 GBs/sec)
	- GDDR6x + GDDR7: use more than just 0/1 volts (i.e. ternary digits 0, 1, -1)
		- ![[db3c07ab2f82221de6b08d54f748928e_MD5.jpeg]]
		- PAM3: (GDDR7) 11 bits = 7 ternary digits -->  276 bits = 176 ternary digits
		- PAM4 (GDDR6x) but ignore to reduce complexity, improve noise, improve efficiency
- HBM: high bandwidth mem in AI chips
	- stacks of DRAM and uses TSVs (thru silicon vias) to combine as cube for mem
	- HBM3E: 24-36GB total 192GB of high speed mem in 1 AI chip
	- for AI accelerator system for AI datacenter w/ several year backlog!!
## Computational Architecture
- GPUs excel at "embarrassingly parallel" categorized problems (easily divided to parallel tasks)
    - for video game rendering and bitcoin mining.
- GPUs use **SIMD** (**single instruction multiple data**) to solve 
    - i.e. 3D video game, ONE instruction transform model -> world space (each obj, each vertex)
	- object's world space pos  + vertex model space = vertex in world space![[7cb8ce398f8587715bd64f54761bb807_MD5.jpeg]]
	- each calculation independent so can easily parallelized and distrib. to cores
	- includes entire CS174A pipeline + rot/mult/etc transformations

###  matched back to hardware archit.
- 1 instruction completed per **thread**/**CUDA core**.
- warp = 32 **Threads** (all doing same seq of instructions)
	- SIMD (old) vs SIMT (2016-)
		- SIMD = all 32 threads doing same seq of instructions in lockstep like marching troops
		- SIMT: individual threads can process at diff rates w/ own program counter
			- All threads within SM share a 128 kilobyte L1 cache (sharing data btwn threads)
		    - allows better flexibility during warp divergence via data-dependent conditional branching and easier reconvergence for the threads.
		    - ![[6c1bac1167b04cbda85cce5448ef5a1d_MD5.jpeg]]
	- "warp" is derived from weaving and **Jacquard Loom**, punch cards to select specific threads.
- **thread blocks** = multiple warps handled by SM
- **grids** of thread blocks, computed across the overall GPU.
- **Gigathread Engine** manages and schedules thread blocks to the available SMs

## Bitcoin & AI
- GPUs were used for bitcoin mining to perform **SHA-256 hashing alg** in parallel.
    - SHA-256 generates a random 256-bit value ("nonce") --> lottery price 3 bitcoin.
    - Bitcoin mining: finding SHA-256 hash with the first 80 bits all zeroes.
- Today, **ASICs** (application-specific integrated circuits) specialized for bitcoin mining
- **Tensor cores** concurrently perform giant matrix multiplication and addition for NN, AI.
- ![[4430832705d26da79c6d078888845e31_MD5.jpeg]]


# Animation principles
- vision (wide peripheral + high res acuity) vs camera (rectangular uniform camera)
	- foveal vs peripheral density of photoreceptors etc)
	- cool monitors that do eye-tracking variable resolution based on where you look!!!
	- persistence (ghost of bright flash in eye, built in motion blur if high enough fps)
	- i.e. 24fps, cartoon animation (8-12fps) forgiving no uncanny valley
	- interlacing/shown at double fps to reduce flicker
	- gaming: 60Hz, prefer 60-120fps
- motion blur: streaks in fast moving objects for shuttering cameras (strobe effect)
- stop motion: i.e. King Kong 1933 doll + other special effects
- rendering motion blur
	- don't fix not broken (no strobe is great)
	- how to fool human eye? just mimic movie camera
	- integrate light over time instead of capture at split moment for motion blur
- **Animation Principles** for traditional cellophane/layered animation
	- timing, cues/anticipation (movement way, mood/weight, drama/bore/confuse)
	- squash and stretch (physic deformation conserving volume)
	- slow in slow out, etc.
	- staging, secondary motion of appendages, follow-thru
	- arc motion not straight line (splines, polynomial piecewise)
	- exaggeration cartoon physics (coyote and roadrunner)
	- appeal (interesting, attractive, unusual, easy to understand)
- 
# Approaches
## Keyframing and interpolation
- artist specifies everything (keyframes), computer interpolates/smoothening inbetweens
- from traditional disney animation keyposing approach
- straight ahead: rapid, unprediceted (i.e. fire)
- keyframes to capture extreme and plan inbetweens'
- layers: big picture first then details every layer (face, limbs, heads, wrinkles, etc.)
## Kinematics & dynamics
- physics, particles, rigid bodies (bones, ball), articulated figures (joints)
- through physical simulation
## Procedural animation
- automatic rules and simulations to produce animation
- select animation parametsr (pos, angle, size) etc.