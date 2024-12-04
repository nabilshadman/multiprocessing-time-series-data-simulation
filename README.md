# Time Series Data Simulation with Multiprocessing

A Python implementation leveraging multiprocessing capabilities to generate large-scale time series data (10,000 samples) from an initial dataset of 20 samples, demonstrating parallel computation techniques for efficient data simulation.

## Overview

This project demonstrates time series data generation using parallel processing in Python. It calculates rates of change from time-dependent data and uses those rates to simulate new parameter values while preserving statistical properties and correlations between parameters.

## Features

- **Rate of Change Calculation**: Computes temporal derivatives of time series data
- **Parallel Processing**: Utilizes Python's multiprocessing to enable efficient simulation
- **Statistical Preservation**: Maintains statistical relationships between parameters
- **Large-scale Generation**: Scales from 20 samples to 10,000 samples
- **Correlation-aware**: Considers cross-parameter correlations in simulations

## Technical Implementation

### Core Components

1. **Rate Calculation Module**
   - Computes rate of change for time series data
   - Handles datetime conversions and missing values
   - Provides robust error handling

2. **Simulation Engine**
   - Implements parallel simulation using Pool's starmap
   - Uses kernel density estimation for rate distribution
   - Preserves parameter correlations during simulation

3. **Data Processing Pipeline**
   - Reads initial time series data
   - Processes and validates input parameters
   - Generates synchronized timestamps

### Project Structure
```
.
├── original.csv                     # Initial dataset with parameters
├── paramX1wrtTime.csv               # Time series data for parameter X1
├── paramX2wrtTime.csv               # Time series data for parameter X2
└── simulate_time_series_data.ipynb  # Main implementation notebook
```

## Getting Started

### Prerequisites
- Python 3.x
- Required packages:
  ```python
  numpy>=1.19.0
  pandas>=1.2.0
  scipy>=1.6.0
  ```

### Installation
1. Clone the repository:
```bash
git clone https://github.com/yourusername/time-series-data-simulation.git
cd time-series-data-simulation
```

2. Install dependencies:
```bash 
pip install -r requirements.txt
```

### Usage
1. Place your input data files in project directory:
   - `original.csv`: Initial parameter dataset
   - `paramX1wrtTime.csv`: Time series for first parameter
   - `paramX2wrtTime.csv`: Time series for second parameter

2. Run the simulation:
```python
python simulate_time_series_data.py
```

## Implementation Details

### Key Functions

1. **Rate Calculation**
```python
def find_rate(data):
    """
    Computes rate of change for time series data
    Args:
        data (pandas.DataFrame): Time series data with datetime index
    Returns:
        pandas.DataFrame: Data with additional rate column
    """
```

2. **Parameter Simulation**
```python
def simulate_corr(temp):
    """
    Simulates correlated parameter values
    Args:
        temp (int): Chunk identifier for parallel processing
    Returns:
        pandas.DataFrame: Simulated parameter values
    """
```

### Workflow
1. Calculate rates of change for time-dependent parameters
2. Generate rate samples using kernel density estimation
3. Initialize parallel simulation parameters
4. Execute parallel simulation processes
5. Combine results and add timestamps
6. Export final simulated dataset

## Results

The simulation produces:
- 10,000 synchronized time series samples
- Preserved statistical properties
- Maintained parameter correlations
- Time-stamped data points

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request
