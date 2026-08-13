# Milky Way Structure: Gaia DR3 & APOGEE-2 DR17

This project provides a comprehensive spatial and dynamical characterization of the Milky Way's stellar populations by cross-matching high-precision astrometric data from Gaia DR3 with high-resolution spectroscopic data from APOGEE-2 DR17[cite: 6]. 

## Project Overview

The Milky Way acts as the closest laboratory for Galactic archaeology[cite: 6]. This study is divided into two modules[cite: 6]:
1.  **Spatial Classification:** Assigning stars to canonical components (thin disc, thick disc, stellar halo, bulge, solar neighborhood) using metallicity, Galactocentric coordinates, and scale height[cite: 6]. 
2.  **Dynamical Domain:** Computing 3D space velocities (U, V, W) to explore the kinematic structure through velocity ellipsoid projections, vector fields, rotation curves, and Oort constants[cite: 6].

## Data Cleaning & Selection

To ensure precise distance and velocity measurements, rigid quality cuts were applied to the initial dataset of 682,284 sources, retaining 281,612 high-quality objects[cite: 6]:
*   **Signal-to-Noise Ratio (SNR):** Threshold set to $\ge$ 120 to guarantee clear spectroscopic readings while minimizing data loss[cite: 6].
*   **RUWE:** Astrometric fit quality bounded at $< 1.4$ to exclude binary systems and measurement errors[cite: 6].
*   **Velocity Scatter (VSCATTER):** Filtered to $\le 0.5$ km/s for consistent radial velocity measurements[cite: 6].
*   **Parallax Correction:** Negative parallaxes were dropped, a Zero-Point Correction was applied, and a combined 10%/40% relative error threshold was established depending on stellar distance[cite: 6].

## Key Results & Methodologies

*   **Toomre Diagrams:** Demonstrated that purely chemical/spatial classifications cause overlapping boundaries (e.g., thick disc stars leaking into the halo), requiring kinematic criteria for robust separation[cite: 6].
*   **Velocity Ellipsoid:** UV plane projections exhibited a clear tilt resulting in a vertex deviation of approximately $\theta \approx -26.64^\circ$, indicative of asymmetric drift and radial streaming motions[cite: 6].
*   **Kinematic Clustering:** Applied the **DBSCAN algorithm** ($\epsilon \approx 3.5$ km/s, min_samples = 7) to identify moving groups in the solar neighborhood, partially recovering the classical Hercules group[cite: 6].
*   **Galactic Rotation Curve:** Derived between 6–12 kpc by calculating the median azimuthal velocity ($V_{\phi}$) per radial bin, displaying canonical flatness beyond 8.5 kpc[cite: 6].
*   **Oort Constants:** Two-dimensional maps of constants A, B, C, and K confirmed local differential rotation and evaluated local shear and vorticity[cite: 6].

## Tools & Libraries
*   **Language:** Python
*   **Astronomy Tools:** TOPCAT, `astropy` (SkyCoord, Galactocentric frames)
*   **Data Science Tools:** `pandas`, `scikit-learn` (DBSCAN), `matplotlib`