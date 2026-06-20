# Bringing the Map to Life: Longitudinal Geodemographic Analysis of the Lisbon Metropolitan Area

Master's thesis - NOVA Information Management School, Universidade NOVA de Lisboa (2026).

## Overview

This repository contains the full Python implementation supporting a longitudinal geodemographic analysis of the Lisbon Metropolitan Area (LMA) across the 2011 and 2021 Portuguese census rounds. The study applies a pooled Self-Organizing Map (SOM) to harmonised statistical-section-level data, producing a shared attribute space from which five geodemographic types are identified via K-Means clustering. Displacement vectors between each section's 2011 and 2021 Best Matching Units quantify both the magnitude and direction of socioeconomic change.

## Key Features

- **Areal harmonisation** - Proportional areal interpolation aligns the 2011 BGRI subsections to the 2021 statistical-section boundaries, enabling direct temporal comparison despite the 2013 administrative reform.
- **Preprocessing sensitivity analysis** - A systematic grid of 32 candidate configurations (5 binary dimensions: scaler, variable set, ILR transformation, scaling scope, PCA) is evaluated on a lightweight SOM to select the optimal pipeline.
- **Pooled SOM training** - A single 50×50 SOM is trained on the concatenated 2011 + 2021 dataset, following the Skupin & Hagelman (2005) strategy, so that both years share a common reference space.
- **Cluster profiling & transition analysis** - Five geodemographic types are characterised through parallel coordinate plots, component planes, and a full transition matrix with chord-diagram visualisation.
- **Trajectory mapping** - Euclidean displacement on the SOM grid is mapped back to geography, revealing the spatial pattern and intensity of neighbourhood change.
- **Interactive dashboard** - A Panel/Bokeh dashboard allows exploration of cluster maps, trajectories, and variable profiles at the section level.

## Data

Census microdata are publicly distributed by the Instituto Nacional de Estatística (INE) through the BGRI dissemination platform:

- **2021 BGRI** - https://mapas.ine.pt/download/index2021.phtml
- **2011 BGRI** - https://mapas.ine.pt/download/index2011.phtml

The raw data files are not included in this repository. Download the shapefiles for the Lisbon Metropolitan Area (NUTS III: 1701) and place them in a `data/` directory before running the notebook.

## Requirements

```
python >= 3.10
geopandas
pandas
numpy
scikit-learn
minisom
scipy
matplotlib
seaborn
bokeh
panel
holoviews
```

Install all dependencies with:

```bash
pip install -r requirements.txt
```

## Repository Structure

```
├── README.md
├── requirements.txt
├── LICENSE
├── thesis_code.ipynb          # Full analysis notebook
└── data/                      # (not tracked) Place BGRI shapefiles here
```

## How to Run

1. Clone the repository.
2. Download the BGRI 2011 and 2021 shapefiles from INE (links above) into `data/`.
3. Install dependencies: `pip install -r requirements.txt`
4. Open and run `thesis_code.ipynb` sequentially.
5. The interactive dashboard launches automatically at the end of the notebook on `localhost`.

## Citation

If you use this code in your research, please cite:

```
[Author]. (2026). Bringing the Map to Life: Longitudinal Geodemographic Analysis
of the Lisbon Metropolitan Area Using Self-Organizing Maps [Master's thesis].
NOVA Information Management School, Universidade NOVA de Lisboa.
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
