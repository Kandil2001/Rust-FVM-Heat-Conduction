# 2D Heat Diffusion Solver in Rust

![Rust](https://img.shields.io/badge/language-Rust-orange.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen.svg)

This is a small 2D heat-diffusion solver written in Rust. I made it to practise using Rust for numerical simulation and to understand how a complete solver can be built without external libraries.

The case is simple: a hot rectangular chip is placed in the middle of a colder domain. The solver updates the temperature field until the solution converges.

<p align="center">
  <img src="results/temperature.svg" alt="Temperature field" width="720">
</p>

## Problem setup

- Grid: `80 × 50`
- Outer boundaries: `300 K`
- Central chip: `360 K`
- Maximum iterations: `30,000`
- Convergence tolerance: `1.0e-6 K`

The temperatures are currently set as constants at the top of [`src/main.rs`](src/main.rs).

## Numerical method

For the cells outside the chip and the boundaries, the steady 2D heat equation is solved using the Jacobi method:

```text
T_new(i,j) = 0.25 × [T(i+1,j) + T(i-1,j) + T(i,j+1) + T(i,j-1)]
```

The residual is the largest temperature change in one iteration:

```text
residual = max |T_new - T_old|
```

The calculation stops when the residual becomes smaller than the tolerance.

More details are in [`docs/method.md`](docs/method.md).

## Run the solver

Install Rust, then run:

```bash
git clone https://github.com/Kandil2001/rust-heat-diffusion-solver.git
cd rust-heat-diffusion-solver
cargo run --release
```

The release mode is recommended because it runs much faster than the debug build.

### GitHub Codespaces

When `cargo` is not available in the Codespace, install Rust first:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source "$HOME/.cargo/env"
cargo run --release
```

## Results

For the current setup, the solver converges in `3,701` iterations.

<p align="center">
  <img src="results/residuals.svg" alt="Residual history" width="760">
</p>

The program saves everything inside the `results` folder:

| File | Content |
|---|---|
| `temperature.csv` | Temperature at every grid cell |
| `residuals.csv` | Residual for every iteration |
| `summary.txt` | Main settings and final values |
| `temperature.svg` | Temperature-field image |
| `residuals.svg` | Convergence image |

The CSV files can be opened in Python, MATLAB, or Excel. The SVG images can be viewed directly on GitHub or in a browser.

## Repository structure

```text
rust-heat-diffusion-solver/
├── Cargo.toml
├── LICENSE
├── README.md
├── docs/
│   └── method.md
├── results/
└── src/
    └── main.rs
```

## Notes

This is a learning project, not a complete physical model of a real processor. It currently uses fixed temperatures, a uniform grid, constant material behaviour, and does not include convection or radiation.

I kept the solver dependency-free so the numerical method and the Rust implementation stay easy to follow.

## Possible next steps

- Add physical dimensions and thermal conductivity
- Add insulated or heat-flux boundary conditions
- Compare Jacobi with Gauss–Seidel and SOR
- Add command-line inputs
- Add parallel versions for larger grids

## License

This project is available under the [MIT License](LICENSE).

## Author

Ahmed Kandil