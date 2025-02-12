# LED-Driven Opsin Isomerization Computation

This repository provides tools for modeling and analyzing opsin isomerization under LED illumination. It includes utilities for loading spectral data, computing isomerization matrices, optimizing LED power distributions, and interactive visualization tools.

## Features
- Load and visualize **LED** and **photoreceptor spectra**.
- Compute **isomerization rates** under different LED settings.
- Optimize **LED power distributions** to achieve specific opsin responses.
- Interactive tools for **exploring isomerization effects** in real time.

## Installation
This project requires Python 3 and several scientific libraries. Install dependencies with:
```bash
pip install numpy scipy matplotlib plotly tqdm pillow
```

## File Structure
- `colors_utils.py` – Contains core utility functions for spectral analysis, isomerization computation, and optimization.
- `Color Processing Examples.ipynb` – Jupyter notebook demonstrating how to use the provided utilities.


## Usage
### 1. Interactive LED Intensity Exploration
```python
from colors_utils import interactive_Ptot_slider

interactive_Ptot_slider()
```

### 2. Load Spectral Data
```python
from colors_utils import prSpectrums, ledSpectrums

opsin_data = prSpectrums("./PhotoReceptorData.pkl", plot=True)
led_data = ledSpectrums("./IlluminationData.pkl", plot=True)
```

### 3. Compute Isomerization Matrix
```python
from colors_utils import get_isomerisation_matrix

isomerisation_matrix = get_isomerisation_matrix(
    selected_opsins=["Scones", "Mcones"],
    selected_leds=["Blue", "Green"],
    opsinDATA_path="./PhotoReceptorData.pkl",
    ledDATA_path="./IlluminationData.pkl"
)
```

### 4. Optimize LED Power Mix
```python
from colors_utils import get_mix_color

target_isomerisation = {"Scones": 1e5, "Mcones": 5e4}
led_powers = get_mix_color(target_isomerisation, mix_type="balance")
print(led_powers)
```

### 5. Plot Isomerization Results
```python
from colors_utils import plot_isomerisations

Ptot_list = [[1, 2, 3], [2, 3, 4]]
selected_LEDs = [["Blue", "Green", "Red"], ["Blue", "Red"]]
plot_isomerisations(Ptot_list, selected_LEDs)
```

## Contributing
If you would like to improve this repository, feel free to submit a pull request or open an issue.

## License
This project is licensed under the MIT License.


