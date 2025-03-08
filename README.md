# Multi-Robot Cooperation to Accomplish a Sequence of Tasks Using Deep Reinforcement Learning

Many real-world problems mandate teamwork, where multi-robot systems accomplish complex tasks through cooperation and decomposition. We study whether robots can learn cooperation to accomplish a sequence of complex tasks in a simulated environment inspired by a factory warehouse. A deep reinforcement learning approach, particularly Q-Learning and a multi-layered neural network, is used for the multi-agent system. The specific task the robots learn is to find bulky artifacts and move them to their destination, which requires cooperation in pairs. Our prior experiments reveal robots can learn to cooperate to perform complex tasks, but the scalability of this approach is limited in terms of the number of robots and tasks, and training time efficiency. The previous approach allocated artifacts to robots prior to training. In our novel approach, however, robots must learn to allocate subtasks themselves to move artifacts not specifically assigned to them. Methods include introducing explicit and implicit forms of communication, which is important for ad-hoc teamwork. We use robot simulations to empirically analyze how well the robots complete the sequence of tasks and evaluate the performance of various approaches through success rates, computing time, scalability, and generalizability.

To access the project, go to: https://github.umn.edu/khan0096/Warehouse/edit/master/readme.md

Associated Paper (outdated 2021, new paper in-progress): https://www-users.cse.umn.edu/~gini/publications/papers/Khan2021arms.pdf


## Installation

1. Install all dependant packages:
   ```bash
   pip install -r requirements.txt

2. Clone the repository:
   ```bash
   git clone https://github.umn.edu/khan0096/Warehouse.git

3. Run in the terminal:
   ```bash
   python3 main.py

The above command trains the default number of agents to complete a series of tasks (i.e., the search phase to find objects & the haul phase to move object to destination) based on the DQN algorithm in the specified environment.

4. To test the agents' performance (their ability to complete a series of tasks) using the model you trained above, run the following command: (Use `--save_results` flag in the command-line to save results to a `csv` file).
   ```bash
   python3 main.py --test --save_results

## Command-line Arguments (Optional):
All command-line arguments are optional, but some are good to specify depending on the experiment that is being run.

- `--device` (String): "cpu" or "cuda" - gpu (cuda) may result in faster training time. Defaults to cuda.
       
- `--pos_mode` (int): position mode
  - 0: all initial positions fixed.
  - 1: agent initial position is random.
  - 2: agent and obstacle initial position is random.
  - 3: agent, obstacle, and target position is random.
  - Defaults to 1.
- `--env_mode` (int): environment mode
  - 0: fully observable (no communication). 
  - 1: partially observable (no communication).
  - 2: partially observable environment with communication. 
  - Defaults to 0.
- `--num_agents` (int): number of agents in the environment, each must learn to complete series of tasks. note - must have minimum of 2 agents since this is a multi-agent system. Defaults to 2.
- `--num_obj` (int): number of objects (boxes) in the environment that agents must find and cooperatively lift and move to the target location to successfully complete series of (sub) tasks. Defaults to 1.             
- `--phase` (String): "search" "haul" or "both" - specify which phase to run training/testing for. Defaults to both.
- `--num_sims` (int): number of test simulation runs. Defaults to 1000.
- `--training_time` (int): total training time. Defaults to 10 million.
- `--grid_width` (int): environment width (horizontal). Defaults to 4.
- `--grid_height` (int): environment height (vertical). Defaults to 3.
- `--test` (flag): test agents' performance once training stage is complete. must specify correct values of training time, num agents, num objects, etc. to match training. Defaults to True.
- `--sim_speed` (float): simulation speed when rendering agent-grid-evironment for testing. Defaults to 0.05.
- `--render` (flag): render text in terminal and display figures; increases runtime of experiment but provides relevant information. Defaults to False.
- `--save_figs` (flag): save initial and final states of the environment as figures. Defaults to False.
- `--save_results` (flag): save all experiment results in a csv file. Defaults to False.
- `--random_alloc` (flag): randomly pre-allocate objects to agents instead of doing so sequentially, which is the default.
- `--commment` (String): comments when saving results of current experiment. Defaults to empty.
- `--success_threshold` (float): 'partial' successes to record when saving experiment results. Defaults to 0.75.
- `--min_helpers` (int): Controls minimum of agents needed to move the object. Must be at least 2. Defaults to 2.
- `--exploration_time` (int): time agent randomly explores the environment. Defaults to factor of 10 less than `training_time`.
- `--capacity` (int): replay memory size. Defaults to 1 million.
- `--train_interval` (int): time steps between each training cycle. Defaults to 50.
- `--batch_size` (int): sample size from replay memory for training. Defaults to 100. 
- `--record_div` (int): time steps between each print statement
- `--initial_epsilon` (float): initial epsilon for epsilon-greedy algorithm. Defaults to 1.0.
- `--final_epsilon` (float): final epsilon for epsilon-greedy algorithm. Defaults to 0.05.
- `--gamma` (float): discount factor (in bellman equation); controls the importance of future rewards. Defaults to 0.99.

## Credits

This project was created by [Nabil Khan](https://github.umn.edu/khan0096) and [Sreeyutha Ratala](https://github.com/SreeyuR).

