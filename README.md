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

## Installation (Windows 10 64-bit)
1. Install [Anaconda](https://docs.anaconda.com/anaconda/install/) if you don't have it already.
2. Open Anaconda Prompt/command line 
3. Create a new environment (named banana-env): `conda create --name banana-env python=3.6` 
4. Activate environment: `activate banana-env`
5. Navigate to desired directory to download project file
6. Clone the repository: `git clone https://github.com/albertlai431/banana-collector` 
7. Go to dependencies directory `cd python`
8. Install dependencies `pip install .`
9. Install pytorch 0.4.0 with conda `conda install pytorch=0.4.0 -c pytorch`
10. Create kernel with environment: `python -m ipykernel install --user --name banana-env --display-name "banana-env"`

## How to Use
1. Open `train.ipynb` and run the code if you would like to train the agent 💪
2. Open `test.ipynb` and run the code if you would like to observe a fully trained agent! 😃

