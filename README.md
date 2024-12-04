[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)


# MuographBeta: muon tomography library

![logo](./images/muograph_logo.png)


This repository provides a library for muon scattering tomography and muon transmission tomography data analysis. 

## Overview

As a disclaimer, this library is more of an aggregate of muon tomography algorithms used throughtout PhD research rather than a polished product for the general public. As such, this repo targets mostly muon tomography reaserchers and enthousiasts.

Users can find ready to use scattering density algorihms as well as samples of simulated data.

While curently being at a preliminary stage, this library is designed to be extended by users, whom are invited to implement their favorite reconstruction, material inference or image processing algorithms.

![image](./images/mst_image_example.png)

## Installation

### As a dependency

### For development

Clone the repository locally:

```bash
git clone git@github.com:MaximeLagrange/muograph.git
cd muograph
```

For development usage, we use [`poetry`](https://python-poetry.org/docs/#installing-with-the-official-installer) to handle dependency installation:

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

To get started, you need Poetry's bin directory in your `PATH` environment variable. Add  the export command to your shell's configuration file. For bash, Add it to the `~/.bashrc` file. For zsh, add it to the `~/.zshrc` file.

```bash
export PATH="$HOME/.local/bin:$PATH"
```

then reload the configuration file:

```bash
source ~/.bashrc # or source ~/.zshrc
```

Poetry should now be accessible:

```bash
poetry self update
```

Muograph requires `python >= 3.10`. This can be installed with e.g [`pyenv`](https://github.com/pyenv/pyenv).

```bash
curl https://pyenv.run | bash
pyenv update
pyenv install 3.10
pyenv local 3.10
```

Install the dependencies:

```bash
poetry install
poetry self add poetry-plugin-export
poetry config warnings.export false
poetry run pre-commit install
```

Finally, make sure everything is working as expected by running the tests:

```bash
poetry run pytest muograph/test/
```

For those unfamiliar with poetry, basically just prepend commands with `poetry run` to use the stuff installed within the local environment, e.g. `poetry run jupyter notebook` to start a jupyter notebook server. This local environment is basically a python virtual environment. To correctly set up the interpreter in your IDE, use `poetry run which python` to see the path to the correct python executable.


## Examples

A few examples to introduce users to the package can be found in the `tutorial/` folder. They are provied as Jupyter notebooks:

 - `00_Volume_of_interest.ipynb` shows how to define a voxelized volume of interest, later used by the reconstruction algorithms.
 - `01_Hits.ipynb` demonstrates how to load muon hits, and simulate detector spatial resolution and/or efficiency effects.
 - `02_Tracking.ipynb` shows how to convert muon hits into muon tracks usable for image reconstruction purposes.
 - `03_Tracking_muon_Scattering_tomography.ipynb` combines incoming and ougoing tracks to compute features relevant to muon scatering tomography.
 - `04_POCA.ipynb` takes the user through the computation of voxel-wise density predictions based on the Point of Closest Approach.
 - `05_Binned_clustered_algorithm.ipynb` demonstrates the Binned Clustered Algorithm, with and without muon momentum information.
 - `06_Angle_statistical_reconstruction.ipynb` shows the Angle Statistical Reconstruction algorithm, with and without muon momentum information.

