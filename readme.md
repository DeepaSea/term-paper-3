This is submission for term paper on module 3 on coupled map lattices. I have recorded some interesting patterns and structures in my report.

# Coupled Map Lattices

Or (hereafter known as) CML is basically a complex dynamical system. It models behaviour of nonlinear systems. 

## The procedure

- We first choose a set of field variables. This should be a lattice at a macroscopic levevl.
- The dimension of the lattice is chosen to corresppond to the physical space being researched.
- We then break the process of iteration and coupling into multiple independent components as required.
- We then replace each component by a non-linear transformation of the field variables on the lattice and the coupling term, which depends on the neighbouring nodes which depends on the network we are defining.
- Iterate over time.

## Classification


# Mathematical model

The one dimensional nonlinear map is given by $$x'_n(i)=f(x_n(i))$$ where $x'_n(i)$ is a virtual variable for an intermediate step. The laplacian operator for diffusion is given by $$x_{n+1}(i) = (1 - \epsilon)x'_n(i) + \frac{\epsilon}{2} \left\{ x'_n(i+1) + x'_n(i-1) \right\}$$.

This can be written using a compact matrix form. Let's define an adjacent matrix, the elements of which are essentially defined as $$x_{n+1}(i)=(1-\epsilon)f(x_n(i))+\frac{\epsilon}{2}\sum_{j=1}^N A_{ij}f(x_n(j))$$,
where $x_{n+1}$ represents the value x at $i^{th}$ node, at iteration n. $\epsilon$ is the coupling strength and the coupling is encapsulated by the adjacent matrix, A. So just by changing A, I can change the network and the pattern just by changing the matrix A, which gives us complex networks.

### How does the adjacency matrix work?

Let us take a simple example with 4 nodes, and consider that the coupling of $x_n$ is between $x_{n+1}$ and $x_{n-1}$. Now for this matrix, we can easily say that it will have atleast two components in a row. So, we define A as $$A_{i,j} = 1, \;\;\; \text{if j = i - 1 or j = i + 1}$$
and $$A_{ij} = 0, \;\;\; \text{otherwise}$$ So in our 4 x 4 matrix for the above example we get

\begin{pmatrix}
0 & 1 &0&1\\
1&0&1&0 \\
0&1&0&1 \\
1&0&1&0
\end{pmatrix}

And the network looks like this

<div style="text-align: center;">
    <img src="attachment:four_node.png" alt="four node" width="400" height="400"/>
</div>

and the matrix can be represented like this

<div style="text-align: center;">
    <img src="attachment:four_node.png" alt="adjacency matrix" width="400" height="400"/>
</div>

# The map


First, let's consider the consider the above equation with a logistic map we looked at in class $$f(x)=1 - a x^2$$ which will give us very rich variety of patterns depending on the parameter value of a in the logistic map (local non-linearity) and $\epsilon$ for coupling strength as mentioned above.

With changing a and $\epsilon$ we different patterns like:
- Chimera States
- Travelling waves
- Brownian motions of chaotic defects
- Frozen patterns with spatial bifurcation and localized chaos
- Pattern selection after suppression of chaos
- Spatiotemporal intermittency


Another logistic map can be $$f(x) = r x(1-x)$$. This is a prototypical model for chaos. And for phase transition models we can use the logistic map $$f(x)=tanh x$$ where we see that the map has bistable fixed points as local dynamics.

# Different couplings

We can use different procedures for coupling as well, that is my $x_{n+1}$ term. For an open-flow, we use unidirectional coupling given by $$x_{n+1}(i) = (1-\epsilon) f(x_n(i)) + \epsilon f(x_n(i-1))$$. For mean-field-type Global Coupling we have $$x_{n+1}(i) = (1-\epsilon)f(x_n(i)) + \frac{\epsilon}{N}\sum_j f(x_n(j))$$ which has adjacency matrix with is the identity $A_ij = 1, \;\; \text{for all i, j}$

## Coupled Circle Maps

The local map is given by $$f(\theta) = \theta + \omega -\frac{k}{2\pi} sin(2\pi \theta)$$, and the dynamics is defined by the equation $$ \theta_{n+1}(i) = (1-\epsilon) f(\theta_n(i))+\frac{\epsilon}{2} (f(\theta_n(i+1))+f(\theta_n(i-1))) mod 1 $$

# Interesting applications

I will mainly focus here on approach to the turbulence problem using coupled map lattices as I worked on the theory and computation of turbulence in my summer research. So to breifly describe the model for turbulence, we know that we have to use the non-linear Navier-Stokes equation (NSE). We will have a discrete and coupled chaotic system on a lattice. This might give insight on correlation among different parts and relations in dimensions, correlation lengths and Lyapunov exponents.

The dynamics for simple diffusively CML [Kaneko 1984] is given by $$ x_{n+1}(i,j) = (1-\epsilon) f(x_n(i,j)) + \frac{\epsilon}{4}\sum_n(i,j),$$ where $\epsilon \in [0,1]$


# References

[1] https://nonlinearsystems.wordpress.com/2021/03/24/coupled-map-lattice/

