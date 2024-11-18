This is submission for term paper on module 3 on coupled map lattices. I have recorded some interesting patterns and structures in my report.

# Coupled Map Lattices

Or (hereafter known as) CML is basically a complex dynamical system. It models behaviour of nonlinear systems. 

## The procedure

- We first choose a set of field variables. This should be a lattice at a macroscopic level.
- The dimension of the lattice is chosen to corresppond to the physical space being researched.
- We then break the process of iteration and coupling into multiple independent components as required.
- We then replace each component by a non-linear transformation of the field variables on the lattice and the coupling term, which depends on the neighbouring nodes which depends on the network we are defining.
- Iterate over time.

## Classification
CML system evolves through discrete time by mapping on vector sequences. These are mappings of two terms: an individual non-linear reaction is occurring and a spatial interaction of variable intensity. The classification is based on the strength of the coupling parameters.

### Weak Coupling

They have minimal interaction between neighboring sites, local dynamics dominate the overall behavior and small perturbations propagate slowly. This has applications in neural modelling, i.e., modeling behaviour of neurons and their interactions (which are weak); gene refulatory networks to simulate the dynamics of gene expression; and,  spatiotemporal chaos which is where we study the emergence of complex patterns and choas in systems with weak spatial coupling.

### Intermediate Coupling
They have moderate interaction between neighboring sites and there is a certain balance between local and global dynamics. We observe formation of coherent structures and wave-like phenomena. This is used in modelling population dynamics like spreading of species. It is used to model chemical reactions and pattern formation.

### Strong Coupling

They have strong interaction between neighboring sites, and there is a global dynamics that dominates the overall behavior and there is rapid synchronization and collective behavior. Some applications are synchronization phenomena like the Kuramoto model, traffic flow, epidemic modelling.


# Mathematical model


The one dimensional nonlinear map is given by $$x'_n(i)=f(x_n(i))$$ where $x'_n(i)$ is a virtual variable for an intermediate step. The laplacian operator for diffusion is given by 

$$x_{n+1}(i) = (1 - \epsilon)x'_n(i) + \frac{\epsilon}{2} \left\{ x'_n(i+1) + x'_n(i-1) \right\}.$$

This can be written using a compact matrix form. Let's define an adjacent matrix, the elements of which are essentially defined as 

$$x_{n+1}(i)=(1-\epsilon)f(x_n(i))+\frac{\epsilon}{2}\sum_{j=1}^N A_{ij}f(x_n(j)),$$

where $x_{n+1}$ represents the value x at $i^{th}$ node, at iteration n. $\epsilon$ is the coupling strength and the coupling is encapsulated by the adjacent matrix, A. So just by changing A, I can change the network and the pattern just by changing the matrix A, which gives us complex networks.

### How does the adjacency matrix work?

Let us take a simple example with 4 nodes, and consider that the coupling of $x_n$ is between $x_{n+1}$ and $x_{n-1}$. Now for this matrix, we can easily say that it will have atleast two components in a row. So, we define A as 

$$A_{i,j} = 1, \;\;\; \text{if j = i - 1 or j = i + 1}$$

and 

$$A_{ij} = 0, \;\;\; \text{otherwise}$$ So in our 4 x 4 matrix for the above example we get

\begin{pmatrix}
0 & 1 &0&1\\
1&0&1&0 \\
0&1&0&1 \\
1&0&1&0
\end{pmatrix}

And the network looks like this

<div style="text-align: center;">
    <img src="images/four_node.png" alt="Game of Life Animation" />
</div>

and the matrix can be represented like this

<div style="text-align: center;">
    <img src="images/adjacency_matrix.png" alt="Game of Life Animation" />
</div>




<!-- <div style="text-align: center;">
    <img src="attachment:four_node.png" alt="adjacency matrix" width="400" height="400"/>
</div> -->

# The map

First, let's consider the consider the above equation with a logistic map we looked at in class
 $$f(x)=1 - a x^2$$ 
 
 which will give us very rich variety of patterns depending on the parameter value of a in the logistic map (local non-linearity) and $\epsilon$ for coupling strength as mentioned above.

With changing a and $\epsilon$ we different patterns like:
- Chimera States
- Travelling waves
- Brownian motions of chaotic defects
- Frozen patterns with spatial bifurcation and localized chaos
- Pattern selection after suppression of chaos
- Spatiotemporal intermittency

Another logistic map can be 
$$f(x) = r x(1-x).$$ 

This is a prototypical model for chaos. And for phase transition models we can use the logistic map $$f(x)=tanh x$$ where we see that the map has bistable fixed points as local dynamics.

# Some interesting patterns with different parameters

## Bifurcation diagram
Let's first consider the widely used logistic map

$$x_{n+1}=rx_n(1-x_n).$$ 

The bifurcation diagram of this is shown here

<div style="text-align: center;">
    <img src="images/bifurcation_from_0.png" alt="Game of Life Animation" />
</div>

for ```R = np.linspace(2.5,4,100000)```
<div style="text-align: center;">
    <img src="images/bifurcation_2.5_4.png" alt="Game of Life Animation" />
</div>

for ```R = np.linspace(3.5,4,100000)``` we have,

<div style="text-align: center;">
    <img src="images/bifurcation_3.5_4.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/bifurcation_neg.png" alt="Game of Life Animation" />
</div>



## CML of simulations equations

### Quadratic Logistic Map
$$f=1-ax^2$$

- Pattern selection with suppression of chaos

<div style="text-align: center;">
    <img src="images/suppression_of_chaos.png" alt="Game of Life Animation" />
</div>

- A random periodic patches in a chaotic behaviour

<div style="text-align: center;">
    <img src="images/quad_random_chaos_period.png" alt="Game of Life Animation" />
</div>

- Frozen pattern

<div style="text-align: center;">
    <img src="images/quad_frozen.png" alt="Game of Life Animation" />
</div>

- Just chaos
<div style="text-align: center;">
    <img src="images/chaos_quad.png" alt="Game of Life Animation" />
</div>

Other patterns
<div style="text-align: center;">
    <img src="images/looks_like_chimera.png" alt="Game of Life Animation" />
</div>



### Logistic chaos map
- Frozen pattern

<div style="text-align: center;">
    <img src="images/quad_random_chaos_period.png" alt="Game of Life Animation" />
</div>

Others
<div style="text-align: center;">
    <img src="images/small_e_log.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/peirodic_with_chaos.png" alt="Game of Life Animation" />
</div>

# Different couplings

We can use different procedures for coupling as well, that is my $x_{n+1}$ term. For an open-flow, we use unidirectional coupling given by


$$x_{n+1}(i) = (1-\epsilon) f(x_n(i)) + \epsilon f(x_n(i-1))$$

For mean-field-type Global Coupling we have 

$$x_{n+1}(i) = (1-\epsilon)f(x_n(i)) + \frac{\epsilon}{N}\sum_j f(x_n(j))$$

which has adjacency matrix with is the identity $A_ij = 1, \;\; \text{for all i, j}$


## Phase transitions

For this we use the function that has bistable fixed points like 

$$f(x)=tanh(x)$$

<div style="text-align: center;">
    <img src="images/phase_periodic.png" alt="Game of Life Animation" />
</div>

for low coupling strength $\epsilon = e$ 


<div style="text-align: center;">
    <img src="images/phase_lowe.png" alt="Game of Life Animation" />
</div>

## Coupled Circle Maps

The local map is given by 


$$f(\theta) = \theta + \omega -\frac{k}{2\pi} sin(2\pi \theta)$$

 and the dynamics is defined by the equation 
 
 $$ \theta_{n+1}(i) = (1-\epsilon) f(\theta_n(i))+\frac{\epsilon}{2} (f(\theta_n(i+1))+f(\theta_n(i-1))) mod 1 $$

<div style="text-align: center;">
    <img src="images/circlemap_small_e_w.png" alt="Game of Life Animation" />
</div>


<div style="text-align: center;">
    <img src="images/random_circle.png" alt="Game of Life Animation" />
</div>



# Interesting applications

I will mainly focus here on approach to the turbulence problem using coupled map lattices as I worked on the theory and computation of turbulence in my summer research. So to breifly describe the model for turbulence, we know that we have to use the non-linear Navier-Stokes equation (NSE). We will have a discrete and coupled chaotic system on a lattice. This might give insight on correlation among different parts and relations in dimensions, correlation lengths and Lyapunov exponents.

The dynamics for simple diffusively CML [Kaneko 1984] is given by 


$$ x_{n+1}(i,j) = (1-\epsilon) f(x_n(i,j)) + \frac{\epsilon}{4}\sum_n(i,j),$$ 


where $\epsilon \in [0,1]$

## Lyaponov exponent of the logistic map

The plot is shown below

<div style="text-align: center;">
    <img src="images/lyapunov_log_map.png" alt="Game of Life Animation" />
</div>

### Why CMLs for Turbulence Modeling?

CMLs provide a simplified framework to study the complex dynamics of turbulent flows. They can capture the essential features of turbulence, such as energy cascade, intermittency, and spatial correlations. CML simulations are computationally less demanding compared to traditional numerical methods like Direct Numerical Simulation (DNS) or Large Eddy Simulation (LES). This makes them suitable for exploring a wide range of parameter space and conducting sensitivity analysis. They also provide qualitative insights into the mechanisms of turbulence, such as the formation and evolution of coherent structures.

### Limitations

The quantitative accuracy may be limited, especially for high-Reynolds-number flows and as CMLs are discrete there might be affects of this on the accuracy of the simulation.


# Coupled map lattice model for convection
https://www.researchgate.net/publication/222266069_Coupled_map_lattice_model_for_convection

The paper mentioned above proposes a CML model for convection, which consists of Eulerian and Lagragian procedures. Simulations of the model reproduce wide-ranged phenomena in Benard convection experiments. It is designed to study the Rayleigh–Bénard convection (RBC), a classical system used to explore chaos, pattern formation, and turbulence in fluid dynamics. The model captures a range of experimental RBC behaviors like formation and oscillation of convective rolls, routes to chaos, bifurcation and quasi-periodic states, spatiotemporal initermittency in the large aspect ratio systems, soft  and hard turbulence.

The results show that it agrees with experimental results across various Rayleigh numbers, aspect ratios, and Prandtl numbers.

### The mathematical model used in my code

I used similar functions from the paper but in one dimension. The velocity

Energy with the following parameters:


<div style="text-align: center;">
    <img src="images/energy.png" alt="Game of Life Animation" />
</div>


<div style="text-align: center;">
    <img src="images/the_velocity.png" alt="Game of Life Animation" />
</div>


-  Additional data from a project I did where I worked on the effects of compressibility on turbulent fluctuations. The code is written in matlab for compressible and incompressible Navier-Stokes equation. I have attached the velocity and vorticity plot below for compressible flows.


<div style="text-align: center;">
    <img src="images/velocity_xy.jpeg" alt="Game of Life Animation" />
</div>



<div style="text-align: center;">
    <img src="images/vorticity.jpeg" alt="Game of Life Animation" />
</div>



In a compressible flow, on increasing the viscosity of the flow in 2D we get turbulent plots. And we can also see the density plot of this for more insight. Here are the plots for a certain conditions of resolution 1024.
<div style="text-align: center;">
    <img src="images/1024_run5_07194_vorticity.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/1024_run5_07194_ek.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/1024_run5_07194_ekt.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/1024_run5_07194_omega.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/1024_run5_07194_pal.png" alt="Game of Life Animation" />
</div>

<div style="text-align: center;">
    <img src="images/1024_run5_07194_rho.png" alt="Game of Life Animation" />
</div>

# Conclusion

I had a lot of fun working on this term paper. The applicaitons of this is remarkably wide.

# References

[1] Coupled map lattice model for convection: https://www.researchgate.net/publication/222266069_Coupled_map_lattice_model_for_convection

[2] Spatiotemporal intermittency in coupled map lattices: https://academic.oup.com/ptp/article/74/5/1033/1835343

[3] Coupled map lattices: https://en.wikipedia.org/wiki/Coupled_map_lattice#Further_reading

[4] Pattern formation in coupled map lattices with the circle map, tanh map, and Chebyshev map: https://manasataramgini.wordpress.com/2017/11/26/pattern-formation-in-coupled-map-lattices-with-the-circle-map-tanh-map-and-chebyshev-map/

[5] More basics: http://www.scholarpedia.org/article/Coupled_maps

[6] Logistic map: https://en.wikipedia.org/wiki/Logistic_map