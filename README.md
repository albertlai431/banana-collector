# Banana-collector
Deep Q-Learning Agent mastering the Unity Banana Collector environment! Through deep reinforcement learning, an agent learns to collect bananas in a Unity environment to maximize the score 🍌

Languages: Python 3.6 and Pytorch\
Environment: [Unity ML-Agents Toolkit](https://github.com/Unity-Technologies/ml-agents)

## The Environment
**Before Training:** *Reward: -1.0*
![Before Training ](/assets/before-training.gif "Before-training")

**After Training:** *Reward: +17.0*
![After Training ](/assets/after-training.gif "After-training")

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
2. Open Anaconda Prompt/command line/terminal 
3. Create a new environment (named banana-env): `conda create --name banana-env python=3.6` 
4. Activate environment: `activate banana-env`
5. Navigate to desired directory to download project file: `cd path/to/desired/directory`
6. Clone the repository: `git clone https://github.com/albertlai431/banana-collector` 
7. Go to dependencies directory: `cd banana-collector/python`
8. Install dependencies (may take a while): `pip install .`
9. Install pytorch 0.4.0 with conda: `conda install pytorch=0.4.0 -c pytorch`
10. Create kernel with environment: `python -m ipykernel install --user --name banana-env --display-name "banana-env"`

## How to Use
1. Launch jupyter-notebook and navigate to cloned repository directory
2. Open `train.ipynb` and run the code if you would like to train the agent 💪
3. Open `test.ipynb` and run the code if you would like to observe a fully trained agent! 😃
4. **Important:** Before running any code in either of the ipynb files, click **Kernel** on the top bar, **Change kernel > banana-env**
5. Remember to deactivate the environment in the Anaconda Prompt/command line/terminal after you are done: `conda deactivate` 

## Potential Issues
- The folder `Banana_Windows_x86_64` may not always work; if you are getting a `UnityTimeOutException`, please go to [this link](https://github.com/udacity/deep-reinforcement-learning/tree/master/p1_navigation#Getting-Started) and replace `Banana_Windows_x86_64` with the correct folder for your system. You may also need to modify the `env` declaration. 
