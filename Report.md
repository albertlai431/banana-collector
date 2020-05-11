## Agent

### DQN Algorithm

The **DQN (Deep Q-learning)** algorithm is based off of **TD Control**, more specifically the **Sarsamax** algorithm. TD Control allows for continuous and quicker learning than Monte Carlo methods, through updating the estimate q* after every time step. Sarsamax in particular, uses the greedy next action value to update the Q-table.

The DQN algorithm incorportates a **neural network** (denoted Q) to represent a continuous state space, such as the one used in this environment. It takes a vectorized state as input and outputs predicted reward values for each corresponding action, playing a similar role to a regular lookup table. It uses gradient descent after every time step to find the optimal parameters to better model the environment, and optimize the agent's actions. In particular, it determines the gradient from taking the loss 


  - Compute difference between reward + gamma*max_next_reward and current predicted state_action value
- DQN algorithm addresses instabilities with using a neural network with predicting state-action values (oscillations or divergences), allowing for convergence
  - Replay pool: removes correlation between consecutive sequences of experience tuples
    - Create a replay buffer from experience and sample small batches of them - learn from individual tuples many times, prioritize rare occurences
    - Switches between collecting experiences and learning from them
  - Fixed Q-targets:
    - Use 2 networks, one to represent local network and the other target network to keep a fixed network to compute the loss
    - "Dangling carrot in front of donkey" 
    - Update target network after a certain number of iterations

### Implementation
- QNetwork - architecture shown below, input = state vector (37), output = state-action values (4)
- ReplayBuffer - stores tuples of experiences in a deque with a max size (shown below), returns random batches of experiences
- Agent - contains local and target Q networks
  - act: uses local network along with epsilon-greedy policy to output next action
  - step: store experience tuple in replay buffer, and learns UPDATE_EVERY
  - learn: updates local network with gradient descent through loss.backward and optimizer.step, soft updates target network
- Training:
  - Loop over episodes:
    - Reset environment, set epsilon

### Hyperparameters
```python
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 64         # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR = 5e-4               # learning rate 
UPDATE_EVERY = 4        # how often to update the network 
```      

### Deep Q-Network Architecture
1. **Fully Connected**: 37 → 64 (Input layer)
2. **RELU** (Activation)
3. **Fully Connected**: 64 → 64 (Hidden layer)
4. **RELU** (Activation)
5. **Fully Connected**: 64 → 4 (Output layer)


## Plot of Rewards
![Plot of Rewards](/assets/training.png "Plot of Rewards")

_Environment solved in 391 episodes!	Average Score: 13.02_


## Ideas for Future Work
The submission has concrete future ideas for improving the agent's performance.