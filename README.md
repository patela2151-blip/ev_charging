# EV Travel and Charge Scheduling using Reinforcement Learning

## Overview

This project explores reinforcement learning approaches for electric vehicle (EV) travel and charging schedule optimisation. The aim is to maximise task completion while managing travel time, battery level, charger availability, and charging visits.

The project compares classical and deep reinforcement learning methods against a heuristic baseline in a custom EV scheduling environment built with `gymnasium`.

## Algorithms Compared

The notebook evaluates the following methods:

- Heuristic baseline
- Q-Learning
- SARSA
- Deep Q-Network (DQN)
- Double Deep Q-Network (Double DQN)

## Project Structure

```text
.
├── notebooks/
│   └── EV_Travel_and_Charge_Scheduling_RL_file.ipynb
├── results/
│   ├── DoubleDQN.csv
│   ├── DQN.csv
│   ├── Final_Ranked_Results.csv
│   ├── Heuristic.csv
│   ├── Q-Learning.csv
│   ├── SARSA.csv
│   └── Statistical_Summary.csv
└── README.md
```

## Environment Description

The custom EV environment simulates an EV that must complete travel tasks while considering:

- Battery level
- Current time
- Travel time between nodes
- Charging station availability
- Waiting time when chargers are full
- Number of completed and remaining tasks
- Charging visits
- Final battery percentage

The agent chooses between travelling to task nodes, visiting charging stations, or waiting when necessary.

## Experimental Setup

Main configuration used in the notebook:

| Parameter | Value |
|---|---:|
| Training episodes | 200,000 |
| Test episodes | 1,000 |
| Number of tasks | 8 |
| Number of chargers | 2 |
| Maximum time | 480 minutes |
| Initial battery | 100% |
| Discount factor | 0.99 |
| Initial epsilon | 1.0 |
| Minimum epsilon | 0.01 |

## Results Summary

The models were evaluated using average total time, average number of charging visits, final battery level, and task completion rate.

| Model | Avg Time | Avg Charges | Avg Battery | Avg Task Completion Rate |
|---|---:|---:|---:|---:|
| SARSA | 474.73 | 1.28 | 37.84 | 0.859 |
| Heuristic | 475.56 | 1.00 | 35.38 | 0.929 |
| Q-Learning | 475.59 | 1.00 | 34.49 | 0.926 |
| DoubleDQN | 476.38 | 1.00 | 34.73 | 0.933 |
| DQN | 476.55 | 1.00 | 32.19 | 0.931 |

## Key Findings

- **SARSA achieved the lowest average travel time**, but it had the lowest task completion rate among the compared models.
- **Double DQN achieved the highest average task completion rate**, making it the strongest model for completing more tasks reliably.
- **DQN and Double DQN produced stable charging behaviour**, averaging one charging visit per test episode.
- The heuristic baseline performed competitively, showing that simple rule-based decisions can be effective in structured EV scheduling problems.

## Installation

Clone the repository:

```bash
git clone https://github.com/patela2151-blip/ev_charging
cd ev_charging
```

Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

For Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install numpy pandas matplotlib seaborn torch gymnasium
```

Or, if a `requirements.txt` file is available:

```bash
pip install -r requirements.txt
```

## How to Run

Open the notebook:

```bash
jupyter notebook notebooks/EV_Travel_and_Charge_Scheduling_RL_file.ipynb
```

Run all cells to train and evaluate the models.

The notebook generates result CSV files for each model and summary comparison files.

## Output Files

| File | Description |
|---|---|
| `Heuristic.csv` | Test results for the heuristic baseline |
| `Q-Learning.csv` | Test results for Q-Learning |
| `SARSA.csv` | Test results for SARSA |
| `DQN.csv` | Test results for Deep Q-Network |
| `DoubleDQN.csv` | Test results for Double DQN |
| `Statistical_Summary.csv` | Full statistical comparison of all models |
| `Final_Ranked_Results.csv` | Final ranked model comparison |

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- PyTorch
- Gymnasium
- Reinforcement Learning

## Notes

Training uses a high number of episodes and may take a long time depending on hardware. GPU acceleration is supported through PyTorch when CUDA is available.

For faster testing, reduce the `EPISODES` value in the notebook.

## Author

Ayush Patel

MSc Data Science Project
