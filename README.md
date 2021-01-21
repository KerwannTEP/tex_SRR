# JuDOKA

Julia Diffusion of Orbits for Keplerian Actions

## INSTALLATION

Install Julia by following the instruction at `https://julialang.org/downloads/platform/`.

## PACKAGES

1) Open the terminal and type

```
$ julia
```

2) Install the following packages:

- `StaticArrays`
- `HypergeometricFunctions`
- `BenchmarkTools`
- `HDF5`
- `DelimitedFiles`
- `Interpolations`
- `ArgParse`
- `SpecialFunctions`
- `Distributions`
- `Plots`

For example, to install the package StaticArrays, one needs to run the command 
```
julia> import Pkg; Pkg.add("StaticArrays") 
```

To exit the Julia terminal, type the command
```
julia> exit()
```
## WARNING !!

**DO NOT INTERRUPT THE DOWNLOADING OF THE PACKAGES !!!!**

## MODIFY THE BACKGROUND FAMILIES

To modify the background of the S-Cluster, open the folder `code/background`
and open the file `inputBath.txt`.
	
Do not change the line 1, which serves as legend.
Starting from line 2, enter the values for each family, one family per line.
Enter the four values, separated by a tabulation.

The numbers describe:
- `gamma`: Cusp power of the family.
- `mass_star[Msun]`: Mass of the family's individuals, which can be stars or BHs (in solar masses).
- `a0[mpc]`: scale factor of the family (in mpc).
- `Mtot(<a0)`: Enclosed mass of the family within the radius a0 (scale factor given previously).

## PLOT A DIFFUSION COEFFICIENT a-cut MAP IN ORBITAL SPACE

To compute a mapping of the diffusion coefficients DRR and DNR at fixed 
semi-major axis, and depending on reduced angular momentum, one needs to open 
`code/tests/Cut.jl`.

Then, one needs to write for which sma `a` one wants to compute DRRjj(a,j). 
Once this is done, save the file and run the command 

```
$ julia Cut.jl
```

within the folder `code/tests`. If one wants to run this with parallelization,
one needs to run the following commands (supposing one is using bash)

```
$ export JULIA_NUM_THREADS=4
$ export JULIA_CPU_THREADS=4
$ julia -p 4 Cut.jl --parallel yes --lmax 10
```

where 4 is the number of parallelized threads. One can check the number of 
threads by opening the Julia terminal and by running the command

```
julia> Threads.nthreads()
```

The resulting file will be created in the folder `code/data` under the name 
`Dump_Diffusion_Coefficients_Cut.hf5`.

Once one has recovered the `Dump_Diffusion_Coefficients_Cut.hf5` file using the latter
method, one can plot the a-cut in orbital space of the relevant coefficients.

### USING JULIA
