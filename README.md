# Rust Heat Diffusion Solver

A compact **Rust scientific-computing project** that implements a simple 2D heat-diffusion solver and exports numerical and visual results.

The project solves a simple 2D steady heat-diffusion problem with:

- cold outer boundaries,
- a hot chip region in the middle,
- iterative solution until convergence,
- CSV output for numerical data,
- SVG output images for quick visualisation.

The project is intentionally simple and readable. It focuses on the core workflow behind numerical simulation software: discretise the domain, iterate to convergence, save results, and visualise the solution.

## Repository name

Suggested GitHub repository name:

```text
rust-heat-diffusion-solver
```

Suggested short GitHub description:

```text
Compact Rust implementation of a 2D heat-diffusion solver for scientific-computing practice and thermal simulation workflows.
```

Suggested topics:

```text
rust, scientific-computing, heat-transfer, numerical-methods, finite-difference, finite-volume, thermal-management
```

## Why I made this

I built this project to practise Rust in a technical context close to my background in CFD, heat transfer, and numerical methods.  
The problem is kept deliberately small so that the implementation stays understandable and can be extended later toward more advanced thermal or CFD cases.

## What the code does

The solver creates a 2D grid and iteratively computes the temperature field.

- Boundary temperature: 300 K
- Hot chip temperature: 360 K
- Solver: simple Jacobi iteration
- Convergence criterion: maximum temperature change per iteration

After running, all results are saved in the `results/` folder.

## Project structure

```text
rust-heat-diffusion-solver/
├── Cargo.toml
├── README.md
├── LICENSE
├── docs/
│   └── method.md
├── results/
│   └── .gitkeep
└── src/
    └── main.rs
```

## Run in GitHub Codespaces

This is the easiest option because it avoids the Windows `link.exe` problem.

1. Create a new GitHub repository.
2. Upload the project files.
3. Click **Code**.
4. Open **Codespaces**.
5. Create a new codespace.
6. In the terminal, run:

```bash
cargo run --release
```

The output will appear in:

```text
results/
```

## Run on Windows

After installing Rust with `rustup`, run:

```powershell
cargo run --release
```

If Rust reports that a linker is missing, install the Microsoft C++ Build Tools with the **Desktop development with C++** workload, then restart the terminal and run the command again.

## Output files

After a successful run, the program writes:

```text
results/temperature.csv
results/residuals.csv
results/summary.txt
results/temperature.svg
results/residuals.svg
```

The `.csv` files can be opened in Excel.  
The `.svg` files can be opened in a browser and are displayed directly by GitHub.

## Example output

The temperature image shows the hot chip region in the centre and the diffusion of heat toward the cold boundaries.

```text
results/temperature.svg
```

The residual image shows the solver convergence history.

```text
results/residuals.svg
```

## Future improvements

- Add grid-independence comparison.
- Add a bottom heat-flux boundary condition.
- Add material properties such as copper and aluminium.
- Compare the output with the original MATLAB model.
- Extend the solver to a convection-diffusion case.

## CV line

**Rust Heat Diffusion Solver — Rust, Numerical Methods, Scientific Computing**  
Implemented a compact 2D heat-diffusion solver in Rust with grid-based discretisation, iterative convergence monitoring, CSV export, and SVG visualisation of temperature and residual fields.
