# Ambient Population from Telecommunications Infrastructure

Code, data, and replication materials for **"Estimating Ambient Population from Telecommunications Infrastructure with Applications to Crime in São Paulo, Brazil."**

The paper proposes a novel, fully replicable measure of *ambient population* — the number of people present in a given area at a given time, regardless of where they live — built entirely from publicly available telecommunications infrastructure data. Most crime research normalizes crime counts using residential (census) population, which implicitly assumes that exposure to victimization coincides with where people sleep at night rather than where they actually spend their day. This measure offers an alternative that requires no agreements with private telecom operators and no access to mobile Call Detail Records (CDRs), making it usable in data-constrained settings across the Global South.

## Authors

João Luiz Becker, J. P. Correia, Eduardo Francisco, Bruno Pantaleão, and Roberto Speicys — FGV-Analytics, Escola de Administração de Empresas de São Paulo (FGV-EAESP).

## What's in this repository

This repo provides the materials needed to understand, reproduce, or extend the paper's analysis:

- **Ambient population estimates**, to be released as a shapefile (`.shp`) at the H3 hexagon level (resolution 8) for the municipality of São Paulo, so the measure can be used directly in other GIS or spatial-analysis workflows without rebuilding it from raw antenna data
- **Code** for constructing the ambient population measure from raw Anatel antenna records, validating it against formal employment data, and applying it to crime data from SSP-SP

## The ambient population measure

The measure is built from antenna location and frequency-band data published by Anatel (Brazil's national telecommunications regulator). Each antenna's coverage area is buffered, intersected with an H3 hexagonal grid, and weighted by the typical simultaneous user capacity associated with its frequency band — lower bands (700–850 MHz) cover more area at lower capacity per cell, while higher bands (1800–3500 MHz) cover less area at higher capacity. Summing these weighted coverage fractions across all antennas intersecting a hexagon produces an estimate of ambient population for that hexagon.

The measure is validated against formal employment records (RAIS) at multiple spatial scales and against an independent population-distribution dataset from IPEA's Access to Opportunities Project, and is then applied to geocoded cellphone theft and robbery records to show how the choice of population denominator reshapes spatial crime patterns and hotspot maps.

### Shapefile release

The ambient population estimates for São Paulo will be released here as a shapefile, with one polygon per H3 hexagon and the corresponding ambient population estimate as an attribute. This is intended to let other researchers and practitioners use the measure directly — as a crime-rate denominator, a covariate, or an exposure measure for other spatial analyses — without needing to reprocess raw Anatel data.

*(Shapefile and accompanying data dictionary forthcoming — check back or watch this repo for updates.)*

## Citation

If you use this measure, the code, or the data in your own work, please cite the paper:

```bibtex
@article{becker_ambient_population,
  title   = {Estimating Ambient Population from Telecommunications Infrastructure with Applications to Crime in São Paulo, Brazil},
  author  = {Becker, João Luiz and Correia, J. P. and Francisco, Eduardo and Pantaleão, Bruno and Speicys, Roberto},
  journal = {Working Paper},
  year    = {2026}
}
```

(Update the entry above once the paper is published or posted to a preprint server.)

## Data sources

| Source | Used for |
|---|---|
| Anatel | Antenna locations and frequency bands |
| IBGE Census (2022) | Resident population baseline |
| RAIS | Formal employment density (validation) |
| IPEA Access to Opportunities Project | Independent population validation |
| SSP-SP | Geocoded cellphone theft and robbery records |

## License

*(Add a license — e.g. MIT for code, CC-BY for data — once decided.)*

## Contact

Questions about the method, data, or code can be directed to the corresponding author.
