# Banana-collector
Deep Q-Learning Agent mastering the Unity Banana Collector environment! Through deep reinforcement learning, an agent learns to collect bananas in a Unity environment to maximize the score 🍌

Languages: Python 3.6 and Pytorch\
Environment: [Unity ML-Agents Toolkit](https://github.com/Unity-Technologies/ml-agents)

## The Environment
![Unity Environment](/assets/environment.gif "Unity Environment")

### Actions
- **0** - move forward
- **1** - move backward
- **2** - turn left
- **3** - turn right

### States
The state of the environment has 37 dimensions, including velocity and perceptions of its environment in terms of vectors.

### Rewards
The agent is given a reward of **+1** if it collects a yellow banana, and a reward of **-1** if it collects a blue banana. The environment is _solved_ when the agent accumulates an reward of **+13** over 100 episodes.

## How to Use
1. `git clone https://github.com/albertlai431/banana-collector`
2. Open `Navigation.ipynb` and excecute the first block of code to install all the depencies
3. Run the rest of the code to train the model! 😃 (a fully trained model is saved as `checkpoint.pth`)

