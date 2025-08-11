# BMS Simulation

This repository simulates a Battery Management System (BMS) for a single lithium-ion cell. The simulation includes models for battery behavior, state-of-charge (SOC) and state-of-health (SOH) estimation, thermal dynamics, and basic alert monitoring.

## Features

- **Battery Model:** Simulates terminal voltage based on open-circuit voltage and internal resistance.
- **SOC Estimator:** Updates battery state-of-charge based on current flow and capacity.
- **SOH Estimator:** Simulates battery capacity degradation over charge/discharge cycles.
- **Thermal Model:** Tracks temperature changes based on current, resistance, and basic cooling.
- **Monitor:** Issues alerts for overvoltage, undervoltage, over/undercooling, and low SOC conditions.
- **Simulation Runner:** Executes a 1-hour simulation with random current profile and visualizes results.

## How It Works

The simulation script (`simulation_runner.ipynb`) performs the following steps:

1. **Imports Models:** Loads all models and the monitor function.
2. **Initializes Models:** Battery, SOC/ SOH estimators, and thermal model are created.
3. **Generates Current Profile:** 1-hour simulation with 1A average random current.
4. **Simulation Loop:** For each second:
   - Updates voltage, SOC, SOH, and temperature.
   - Checks for alerts.
   - Logs all parameters.
5. **Visualization:** Plots SOC, SOH, temperature, and voltage over time.
6. **Results:** Saves plots to the `results` directory.

## Alerts

During simulation, the system triggers alerts for:
- **Overvoltage:** Voltage > 4.2V
- **Undervoltage:** Voltage < 3.0V
- **Overtemperature:** Temperature > 60°C
- **Undertemperature:** Temperature < 0°C
- **Low SOC:** SOC < 10%

## Output

After running the simulation, results are saved as `results/simulation_results.png` and displayed:

- State of Charge (SOC)
- State of Health (SOH)
- Battery Temperature (°C)
- Battery Voltage (V)

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/rohitgore2005/BMS-Simulation.git
   cd BMS-Simulation
   ```

2. Install dependencies (if needed):
   ```
   pip install matplotlib numpy
   ```

3. Run the simulation:
   - Open `simulation_runner.ipynb` in Jupyter Notebook and run all cells.
   - The result plot will be saved in the `results` folder.

## File Structure

- `simulation_runner.ipynb` — Main simulation script and runner.
- `battery_model.py` — Battery behavior model (imported, also redefined in notebook).
- `soc_estimation.py` — SOC estimation logic (imported, also redefined in notebook).
- `soh_estimation.py` — SOH estimation logic (imported, also redefined in notebook).
- `thermal_model.py` — Thermal model for cell temperature (imported, also redefined in notebook).
- `monitor.py` — Alert monitoring logic (imported, also redefined in notebook).
- `results/` — Output directory for simulation plots.

> **Note:** The notebook contains self-contained definitions for all models, but also imports them from separate modules for modularity.

## License

This project is provided for simulation and educational purposes.
