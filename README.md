# Online Learning for Geomagnetic Storm Forecasting

This final-year project compares online and batch learning methods for predicting
geomagnetic storm intensity (Dst).

## Repository layout

| Path | Purpose |
| --- | --- |
| `Storm_building/StormDataset.ipynb` | Prepares the derived storm datasets from OMNI solar-wind data. |
| `Testing/batch_build.ipynb` | Trains and evaluates the batch-learning baseline. |
| `Testing/Online_build.ipynb` | Trains and evaluates the online-learning model. |
| `Analysis/analysis.ipynb` | Compares the saved batch and online experiment results. |

The versioned `storm_dataset_96.csv` and result files are the data required to
run the training and analysis notebooks. They are included so the published
experiments can be inspected without rebuilding the raw dataset.

## Setup

Use Python 3.11 or a compatible TensorFlow-supported Python version, then from
the repository root create an environment and install the dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Open Jupyter from the repository root so the relative paths in the notebooks
resolve correctly:

```bash
jupyter notebook
```

Run the notebooks in this order when reproducing the workflow:

1. `Storm_building/StormDataset.ipynb` (only when rebuilding the dataset)
2. `Testing/batch_build.ipynb`
3. `Testing/Online_build.ipynb`
4. `Analysis/analysis.ipynb`

## Raw source data

`Storm_building/StormDataset.ipynb` expects
`Storm_building/omni2_all_years.dat.txt`, which is deliberately not tracked
because it is approximately 181 MB. Download the OMNI high-resolution data
from [NASA OMNIWeb](https://omniweb.gsfc.nasa.gov/) and save it at that path
before rebuilding the derived datasets.

## Generated files

Training notebooks write CSV and pickle result files into `Testing/`. The
published result files used by the analysis notebook are versioned; additional
locally generated outputs are ignored to keep commits focused on source and
reproducible reference results.
