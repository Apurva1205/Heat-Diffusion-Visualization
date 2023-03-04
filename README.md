# Heat-Diffusion-Visualization
###########1D:


The heat equation describes the diffusion of heat in a medium over time and is given by:

∂T/∂t = α ∂^2T/∂x^2

where T is the temperature, t is time, x is the position, and α is the thermal diffusivity.

The code starts by defining the variables such as the length of the domain, the number of grid points, the grid spacing, the time step, the number of time steps, the thermal diffusivity, and the initial temperature. It then defines the temperature array T and the matrix A for the finite difference method.

The finite difference method discretizes the heat equation in space and time using the second-order central difference approximation. The discretized equation can be written as:

T^(n+1)i = T^n_i + α Δt/Δx^2 (T^n{i+1} - 2T^n_i + T^n_{i-1})

where T^(n+1)_i is the temperature at position i and time step n+1, T^n_i is the temperature at position i and time step n, and Δt and Δx are the time step and grid spacing, respectively.

The matrix A is constructed using the coefficients of the discretized equation. The boundary conditions are also applied by setting the first and last elements of the temperature array to zero.

The heat equation is then solved by iterating over the number of time steps using the dot product of the matrix A and the temperature array T. The boundary conditions are applied again at each time step.

Finally, the temperature profile is plotted using the matplotlib library. The x-axis represents the position, and the y-axis represents the temperature. The title of the plot indicates that this is a 1D heat equation.









#########This code defines two functions to solve the 1D and 2D heat equations using finite differences.

The 1D heat equation solver function, solve_1d_heat_equation, takes in five arguments: L (length of the domain), nx (number of grid points), alpha (thermal diffusivity), nt (number of time steps), and T0 (initial temperature distribution).

Inside the function, the grid spacing dx is calculated as L/nx, the grid points x are defined using np.linspace, the time step dt is set to 0.01, the initial time t is set to 0.0, the temperature array T is initialized as a numpy array of zeros with size nx+1, the boundary conditions are set (i.e., T[0] and T[-1] are both set to 0), and the initial condition T0 is assigned to T[1:-1].

Next, the matrix Ax is defined using a for loop. Ax is a numpy array of zeros with size (nx+1, nx+1) and is used to solve the finite difference equations. The for loop fills in the matrix Ax using the formula for the finite difference method.

Finally, there is a time loop that solves the heat equation using the finite difference method. In each iteration of the loop, Tn is set to T.copy(), b is calculated using the finite difference formula, and then T is updated using np.linalg.solve with Ax and b. The boundary conditions are set again, and the temperature distribution is plotted using plt.plot.

The 2D heat equation solver function, solve_2d_heat_equation, takes in seven arguments: Lx (length of the domain in the x direction), Ly (length of the domain in the y direction), nx (number of grid points in the x direction), ny (number of grid points in the y direction), alpha (thermal diffusivity), nt (number of time steps), and T0 (initial temperature distribution).

Inside the function, the grid spacings dx and dy are calculated as Lx/nx and Ly/ny, respectively. The grid points x and y are defined using np.linspace. The time step dt is set to 0.01, the initial time t is set to 0.0, the temperature array T is initialized as a numpy array of zeros with size (nx+1, ny+1), and the boundary conditions are set (i.e., T[0, :], T[-1, :], T[:, 0], and T[:, -1] are all set to 0). The initial condition T0 is assigned to T[1:-1, 1:-1].

Next, the matrices Ax and Ay are defined using numpy arrays of zeros with size (nx+1, nx+1) and (ny+1, ny+1), respectively. The finite difference equations are solved using a time loop similar to the 1D case. The temperature field is plotted every 100 time steps using matplotlib's plot_surface function to create a 3D surface plot.





