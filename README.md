# Q-LEARNING: Explorer Robot in a 2D World

This project implements a classic Q-Learning algorithm to train an autonomous robot to navigate a 2D grid world. The robot's goal is to explore the environment, collect valuable resources, avoid dangers, and return to its base, all while learning an optimal policy through trial and error.

## Project Overview

The `ExplorerEnv` class defines a custom reinforcement learning environment where a robot agent must learn to maximize its cumulative reward. The environment features:
* A 15x15 grid world.
* A starting position `(0, 0)` and a base at `(14, 14)`.
* Five valuable resources to collect.
* Several dangerous zones to avoid.
* Obstacles that block movement.
* A reward system that penalizes movement, rewards resource collection and returning to base, and heavily penalizes encountering danger.

The core of the project is the `train_q_learning` function, which uses the standard Q-Learning update rule to iteratively improve the agent's policy over thousands of episodes. The code also includes functions to visualize the learned path and plot the convergence of the total reward over time.

## Key Features

* **Custom Environment (`ExplorerEnv`)**: Defines the state space, action space (up, down, left, right), transition dynamics, and reward function.
* **Q-Learning Algorithm**: Implements the fundamental model-free RL algorithm for learning an optimal action-value function.
* **Parameter Experimentation**: Compares three different sets of hyperparameters (learning rate `alpha`, discount factor `gamma`, exploration rate `epsilon`) to analyze their impact on learning speed and final performance.
* **Visualization**:
    * `display_grid`: Prints a text-based representation of the grid, showing the robot's path with step numbers.
    * `plot_convergence`: Generates a plot showing the total reward per episode, including a moving average for smoother visualization.
* **Performance Metrics**: Reports the average and maximum reward achieved for each parameter set.

## How to Run

This project is contained within a single Jupyter Notebook file: `Q_LEARNINGRobotExplorateurdansunMonde2D.ipynb`.

1.  **Prerequisites**: Ensure you have Python installed with the following libraries:
    *   `numpy`
    *   `matplotlib`
    *   `random`

2.  **Execution**:
    *   Open the notebook in Jupyter Lab or Jupyter Notebook.
    *   Run all cells sequentially.
    *   The notebook will automatically train the agent for 5000 episodes using three different parameter sets, display the final learned path for the first set, and generate a plot titled "Convergence des récompenses" (Reward Convergence).

## Output Interpretation

Upon running the notebook, you will see:

1.  **Statistics**: For each of the three parameter sets, it prints the average and maximum total reward achieved across all episodes.
2.  **Final Path Grid**: A text grid showing the robot's path from start (`S`) to base (`B`), with collected resources (`R`), dangers (`D`), obstacles (`X`), and the step number at each position along the path.
3.  **Convergence Plot**: A graph plotting the total reward per episode. The plot includes lines for each parameter set and their corresponding 100-episode moving averages, allowing you to visually assess how quickly and effectively each configuration learns.

## Hyperparameter Sets

The notebook compares three configurations:

*   **Set 1 (base)**: `alpha=0.1`, `gamma=0.99`, `epsilon=0.1`
*   **Set 2 (plus d'exploration)**: `alpha=0.05`, `gamma=0.95`, `epsilon=0.2` (Higher exploration)
*   **Set 3 (apprentissage rapide)**: `alpha=0.2`, `gamma=0.9`, `epsilon=0.05` (Faster learning rate, less exploration)

## Notes

*   The state is represented as an integer encoding the robot's position and a bitmask indicating which resources have been collected.
*   The code is written in French for some comments and output labels (e.g., "Récupense moyenne", "Grille avec chemin final"), reflecting the author's language preference.
*   This is a foundational example of tabular Q-Learning. For larger, more complex environments, function approximation (e.g., Deep Q-Networks) would be necessary.

---

*Created by: mariem1mansour*
*Last Updated: December 6, 2025*
