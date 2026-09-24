# zemax-local-optimization-macro
A ZPL macro for **Ansys Zemax OpticStudio** that logs, analyzes, and visualizes optimization behavior cycle-by-cycle.
## Overview

During lens optimization, it is often difficult to understand **why** the Merit Function is improving, which variables are driving convergence, and when optimization gains begin to plateau.

This macro provides detailed insight into the optimization process by tracking:

- Merit Function value at every optimization cycle
- Merit Function change (ΔMF) between cycles
- Absolute value of each active optimization variable
- Variable change (ΔV) between cycles
- Variable evolution throughout the optimization run

The goal is to help optical designers better understand optimization behavior and make informed decisions about optimization strategy and stopping criteria.

---

## Features

### Merit Function Tracking

The macro records the Merit Function value after each optimization cycle and generates:

- **Merit Function vs Optimization Cycle**
- **Δ Merit Function vs Optimization Cycle**

These plots help visualize:

- Convergence speed
- Optimization efficiency
- Diminishing returns
- Potential stagnation regions

### Variable Monitoring

Using `GETVARDATA`, the macro automatically detects active optimization variables and tracks:

- Current value
- Incremental change per cycle
- Variable location and metadata

Supported variable types include:

- Curvature (ROC)
- Thickness
- Conic Constant
- Glass Index (Nd)
- Abbe Number (Vd)
- Partial Dispersion (dPgF)
- Thermal Coefficient of Expansion (TCE)
- Parameter Values
- Extra Data Values
- Multi-Configuration Operands
- NSC Positions (X, Y, Z)
- NSC Tilts (X, Y, Z)
- NSC Parameters

### Automatic Plot Generation

For each detected variable type the macro automatically generates:

#### Absolute Value Plots

```text
Variable Value vs Optimization Cycle
```

#### Delta Value Plots

```text
Δ Variable Value vs Optimization Cycle
```

These plots reveal:

- Variable sensitivity
- Step-size behavior
- Stabilization trends
- Variables that continue to drive optimization

### Optimization Overview Table

At the end of the run, the macro produces a summary table showing:

- Optimization cycle number
- Recorded value of each tracked variable

---

## Example

The macro is demonstrated using:

**AsphericSinglet_PlotMFEExample.zar**

In this example, optimization progress is analyzed alongside surface curvature evolution.

The results illustrate:

- How curvature adjustments correlate with Merit Function improvements
- Which stages of optimization drive the largest performance gains
- When curvature changes become minimal and convergence begins to plateau

---

## Why Use This Tool?

- Identify which variables contribute most to convergence
- Determine whether optimization is still making meaningful progress
- Detect diminishing returns early
- Better understand optimizer behavior
- Make more informed optimization decisions

---

## Usage

1. Open an OpticStudio system.
2. Ensure at least one optimization variable is active.
3. Run `PlotMFValue_VS_Optimization_cycles.ZPL`.
4. Enter the desired number of optimization cycles.
5. Review the generated plots and optimization summary.

---

## Output

The macro generates:

- Merit Function convergence plot
- Merit Function delta plot
- Variable value plots grouped by variable type
- Variable delta plots grouped by variable type
- Cycle-by-cycle optimization log
- Optimization summary table

---

## Future Improvements

- CSV export of optimization data
- Automated report generation
- Variable sensitivity ranking
- Hammer optimization support
- Interactive visualization using ZOS-API/Python

---

## Author

Developed for the **Ansys Zemax OpticStudio** community to improve visibility into optimization convergence and variable behavior.

