# Milky Way structure: Gaia DR3 × APOGEE-2 DR17

Spatial and kinematic characterisation of the Milky Way's stellar populations, built by cross-matching Gaia DR3 astrometry with APOGEE-2 DR17 high-resolution spectroscopy.

**[Notebook](notebooks/milky-way-structure.ipynb)** · **[Report (PDF)](report/milky-way-structure-report.pdf)**

## Highlights

- **682,284 → 281,612 sources** after documented quality cuts on signal-to-noise, astrometric fit and radial-velocity scatter.
- **Velocity ellipsoid** tilted by a vertex deviation of about **−26.6°**, consistent with asymmetric drift and radial streaming.
- **DBSCAN** on stellar velocities partially recovers the Hercules moving group, and the **rotation curve** between 6 and 12 kpc is flat beyond 8.5 kpc.

## Data and quality cuts

Gaia DR3 astrometry cross-matched with APOGEE-2 DR17 spectroscopy (682,284 sources), filtered to 281,612 high-quality stars:

| Cut | Threshold | Purpose |
|---|---|---|
| Spectroscopic SNR | ≥ 120 | Clean spectra with limited data loss |
| RUWE | < 1.4 | Removes poor astrometric fits and likely binaries |
| VSCATTER | ≤ 0.5 km/s | Stable radial velocities |
| Parallax | > 0, zero-point corrected, 10% or 40% relative error depending on distance | Reliable distances |

The data are not included in the repository. They can be retrieved from the [Gaia Archive](https://gea.esac.esa.int/archive/) and the [SDSS DR17 APOGEE data](https://www.sdss4.org/dr17/irspec/), and cross-matched in TOPCAT.

## Method

1. **Spatial classification.** Stars are assigned to the thin disc, thick disc, halo, bulge and solar neighbourhood using metallicity, Galactocentric coordinates and scale height.
2. **Kinematics.** 3D space velocities (U, V, W) with `astropy` Galactocentric frames, Toomre diagrams, velocity-ellipsoid projections and vector fields.
3. **Clustering.** DBSCAN (ε ≈ 3.5 km/s, `min_samples` = 7) searches for moving groups in the solar neighbourhood.
4. **Rotation curve and Oort constants.** Median azimuthal velocity per radial bin between 6 and 12 kpc, and 2D maps of the Oort constants A, B, C and K.

## Results

- Toomre diagrams show that purely chemical and spatial labels overlap, with thick-disc stars leaking into the halo, so a robust separation also needs kinematic criteria.
- The vertex deviation of the velocity ellipsoid (θ ≈ −26.64°) points to non-axisymmetric streaming in the solar neighbourhood.
- The Oort constant maps confirm local differential rotation and quantify local shear and vorticity.

## Repository structure

```
├── notebooks/milky-way-structure.ipynb    Analysis with saved outputs
└── report/milky-way-structure-report.pdf  Write-up in article format
```

## Reproduce

```bash
pip install -r requirements.txt
jupyter notebook notebooks/milky-way-structure.ipynb
```

## Stack

Python · pandas · NumPy · scikit-learn (DBSCAN) · astropy · Matplotlib · seaborn · TOPCAT

## Context

Graduate coursework, Instituto de Astronomía, UNAM (2026).

## Licence

Code released under the [MIT licence](LICENSE). Report © Luis Ángel Quiroz López.

---

Part of the portfolio of Luis Ángel Quiroz López · [lobby9000.github.io](https://lobby9000.github.io) · [LinkedIn](https://www.linkedin.com/in/llqq) · [GitHub](https://github.com/lobby9000)
