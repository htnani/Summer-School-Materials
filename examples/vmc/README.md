This program computes expectation values (6D integrals) associated with the helium atom.  

Define *r1*, *r2*, and *r12* to be the distances of the electrons from the nucleus and from each other. 

The classic Hylleraas wavefunction for the helium atom is
~~~
   psi(r1,r2,r12) = (1 + 0.5*r12) * exp(-2*(r1+r2))
~~~

We want to compute *<r1>*, *<r2>*, *<r12>* where

~~~
   <f> = integral( f(r1,r2,r12) * psi(r1,r2,r12)^2 dx1 dy1 dz1 dx2 dy2 dz2) / N
~~~

where *N* is the constant that square normalizes *psi*.

This is performed using the Metropolis algorithm that interprets *p=psi^2* as an unormalized probability distribution.  Points are asymptotically sampled from the distribution p() as follows

1. initialize vectors *r1* and *r2* and compute *p=psi^2*, then repeat steps 2 and 3

2. randomly sample new vectors *r1*, *r2* and compute new value of *p*

3. accept the new point with probablilty *min(1,p/pnew)*

Once the population has converged (in this simple example we assume this happens after Neq steps) you can start computing statistics.


The sub-directories contain the following:

* seq --- the original sequential (unvectorized) version

* omp --- the open mp version

* mpi --- the mpi version
