# Schwarzschild Black Hole Accretion Disk

## Overview

This project presents a **numerical study of an accretion disk around a Schwarzschild (non-rotating) black hole**. The main objective is to investigate how the physical properties of the disk vary with radial distance from the black hole.

The model calculates the radial profiles of:

* Effective temperature
* Surface density
* Mid-plane density
* Radiative flux
* Cumulative luminosity

The calculations are performed using Python and standard numerical methods.

---

## Physical Model

For a Schwarzschild black hole, the gravitational radius is

$$
r_g = \frac{GM}{c^2},
$$

and the innermost stable circular orbit (ISCO) is

$$
r_{\mathrm{ISCO}} = 6r_g.
$$

The radiative flux from the thin accretion disk is modeled as

$$
F(r)=
\frac{3GM\dot{M}}{8\pi r^3}
\left(
1-\sqrt{\frac{r_{\mathrm{ISCO}}}{r}}
\right).
$$

The effective temperature is calculated using the Stefan–Boltzmann relation:

$$
T_{\mathrm{eff}}(r)
=
\left(
\frac{F(r)}{\sigma_{\mathrm{SB}}}
\right)^{1/4}.
$$

The disk scale height is estimated from

$$
H=\frac{c_s}{\Omega_K},
$$

where the Keplerian angular velocity is

$$
\Omega_K=\sqrt{\frac{GM}{r^3}}.
$$

An alpha-disk prescription is used to estimate the viscosity and surface density.

---

## Numerical Method

The calculations are performed on a logarithmically spaced radial grid extending from just outside the ISCO to approximately \(1000r_g\).

The cumulative luminosity is obtained numerically from

$$
L(r)=
\int_{r_{\mathrm{ISCO}}}^{r}
4\pi r'F(r')\,dr'.
$$

The numerical integration is performed using the `cumulative_trapezoid` method from **SciPy**.

---

## Example Parameters

The example model uses:

| Parameter             |                              Value |
| --------------------- | ---------------------------------: |
| Black hole mass       |                      \(10M_\odot\) |
| Black hole type       |                      Schwarzschild |
| ISCO                  |                           \(6r_g\) |
| Accretion rate        | \(0.1L_{\mathrm{Edd}}/(\eta c^2)\) |
| Radiative efficiency  |                     \(\eta=0.057\) |
| Alpha parameter       |                     \(\alpha=0.1\) |
| Mean molecular weight |                       \(\mu=0.62\) |
| Outer radius          |                        \(1000r_g\) |

---

## Software and Libraries

The project uses:

* **Python**
* **NumPy** – numerical calculations
* **SciPy** – numerical integration
* **Pandas** – data handling and CSV/Excel output
* **Matplotlib** – visualization
* **Jupyter Notebook** – interactive computational environment

---

## Project Structure

```text
Schwarzschild_Accretion_Disk/
│
├── schwarzschild_accretion_disk.ipynb
├── accretion_disk_data.csv
├── accretion_disk_data.xlsx
│
├── 01_temperature.png
├── 02_surface_density.png
├── 03_midplane_density.png
├── 04_flux.png
├── 05_luminosity.png
└── 06_cumulative_luminosity.png
```

---

## Results

The project generates radial profiles showing how the physical properties of the accretion disk change with distance from the black hole.

The expected behavior includes:

* The disk temperature is highest in the inner region.
* The radiative flux decreases strongly with increasing radius.
* The surface density and mid-plane density vary systematically with radius.
* The cumulative luminosity increases outward as more of the disk emission is included.

---

## Data Output

The calculated quantities are saved in a CSV file containing variables such as:

```text
Radius
Radius in gravitational radii
Flux
Effective temperature
Scale height
Surface density
Mid-plane density
Luminosity
Cumulative luminosity
```

These data can be used for further analysis and visualization.

---

## Future Improvements

This model can be extended by including:

* General relativistic corrections
* The Novikov–Thorne relativistic disk model
* Radiation pressure
* Gas pressure
* Realistic opacity laws
* Vertical disk structure
* Relativistic temperature corrections
* Spectral energy distribution modeling
* Comparison with observational X-ray data

---

## Author

**Krishna Prasad Adhikari**

M.Sc. Physics
Assistant Professor of Physics
Tribhuvan University, Nepal

---

## Purpose

This project is developed as a **computational astrophysics study of accretion-disk physics** and demonstrates the application of numerical methods to astrophysical systems.

It is intended for learning, research development, and further extension toward more realistic relativistic accretion-disk models.
