# MEEGLET
> Morlet wavelets for M/EEG analysis, [ˈmiːglɪt]

This package provides a lean implementation of Morlet wavelets [@morlet_wave_1982] *designed for power-spectral analysis of M/EEG resting-state signals* [@hipp2012large;@bomatter2023].

- Distinct [frequency-domain parametrization of Morlet wavelets](background/0_tour.html#power-spectral-density-in-units-of-µv²oct)
- Established [spectral M/EEG metrics](background/0_tour.html#overview-on-implemented-meeg-spectral-metrics) share same wavelet convolutions
- Harmonized & tested [Python](api/wavelets.html) and [MATLAB](matlab/matlab_functions.html) implementation [(numerically equivalent)](./api/wavelets.html#more-unit-tests-and-validation)
- Comprehensive [mathematical documentation](background/1_background_wavelets.html)


```python
import matplotlib.pyplot as plt
from meeglet import define_frequencies, define_wavelets, plot_wavelet_family

foi, sigma_time, sigma_freq, bw_oct, qt = define_frequencies(
    foi_start=1, foi_end=32, bw_oct=1, delta_oct=1
)

wavelets = define_wavelets(
    foi=foi, sigma_time=sigma_time, sfreq=1000., density='oct'
)

plot_wavelet_family(wavelets, foi, fmax=64)
plt.gcf().set_size_inches(9, 3)
```

## Documentation
|                         |                                                                      |
|:------------------------|:---------------------------------------------------------------------|
| [Background](background/index.html) | overview on scope, rationale & design choices            |
| [Python tutorials](tutorials/index.html) | M/EEG data analysis examples                        |
| [Python API](api/index.html) | Documentation of Python functions and unit tests                |
| [MATLAB functionality](matlab/index.html) | MATLAB documentation and data analysis example     |

Use the left sidebar for navigating conveniently!

## Installation

Please clone the software, consider installing the dependencies listed in the \`environment.yml.

Then do in your conda/mamba environment of choice:

``` bash

pip install -e .
```

Soon a Python package will be available on the PyPi.

## Citation

When using our package, please cite our two reference articles:

Python implementation and covariance computation.

``` bibtex
@article {bomatter2023,
    author = {Philipp Bomatter and Joseph Paillard and Pilar Garces and Joerg F Hipp and Denis A Engemann},
    title = {Machine learning of brain-specific biomarkers from EEG},
    elocation-id = {2023.12.15.571864},
    year = {2023},
    doi = {10.1101/2023.12.15.571864},
    publisher = {Cold Spring Harbor Laboratory},
    URL = {https://www.biorxiv.org/content/early/2023/12/21/2023.12.15.571864},
    eprint = {https://www.biorxiv.org/content/early/2023/12/21/2023.12.15.571864.full.pdf},
    journal = {bioRxiv}
}
```

General methodology, MATLAB implementation and power-envelope correlations.

``` bibtex
@article{hipp2012large,
  title={Large-scale cortical correlation structure of spontaneous oscillatory activity},
  author={Hipp, Joerg F and Hawellek, David J and Corbetta, Maurizio and Siegel, Markus and Engel, Andreas K},
  journal={Nature neuroscience},
  volume={15},
  number={6},
  pages={884--890},
  year={2012},
  publisher={Nature Publishing Group US New York}
}
```

## Related software

M/EEG features based on Morlet wavelets using the more familiar time-domain parametrization can be readily computed is sevaral major software packages for M/EEG analysis:

- [FieldTrip](https://www.fieldtriptoolbox.org/)
- [BrainStorm](https://neuroimage.usc.edu/brainstorm/)
- [MNE](https://mne.tools/stable/index.html)
- [MNE-Connectivity](https://mne.tools/mne-connectivity/stable/index.html)
