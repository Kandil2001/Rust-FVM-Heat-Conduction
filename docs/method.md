# Numerical Method

This project solves a small steady 2D heat-diffusion problem on a structured grid.

The update rule is intentionally simple. Each non-boundary cell is updated from the average of its four neighbours:

```text
T_new(i,j) = 0.25 * [T(i+1,j) + T(i-1,j) + T(i,j+1) + T(i,j-1)]
```

A fixed hot chip region is kept in the middle of the domain, while the outer boundary is kept cold.

This is not a full CFD solver. It is a first Rust scientific-computing project, inspired by finite-difference/finite-volume ideas used in heat-transfer and CFD courses.

## Output files

The program writes all outputs to the `results/` folder:

- `temperature.csv`
- `residuals.csv`
- `summary.txt`
- `temperature.svg`
- `residuals.svg`

The SVG files can be opened directly in a browser or viewed on GitHub.
