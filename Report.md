## Agent

### DQN Algorithm

The **DQN (Deep Q-learning)** algorithm is based off of **TD Control**, more specifically the **Sarsamax** algorithm. TD Control allows for continuous and quicker learning than Monte Carlo methods, through updating the estimate q* after every time step. Sarsamax in particular, uses the greedy next action value to update the Q-table.

The DQN algorithm incorportates a **neural network** (denoted Q) to represent a continuous state space, such as the one used in this environment. It takes a vectorized state as input and outputs predicted reward values for each corresponding action, playing a similar role to a regular lookup table. It uses gradient descent after every time step to find the optimal parameters to better model the environment, and optimize the agent's actions. In particular, it determines the gradient from taking the loss `optimal_value_for_state_action_pair - esimtaed_Q_value_for_state_action_pair`. 

However, simply replacing the Q-table with a neural network often leads to oscillations and divergences due to the unstable parameters, leading to a failure to convergence. DQN addresses these stabilities with a **replay pool** and **fixed Q-targets**. The replay pool removes correlation between consecutive sequences of experience tuples through creating a replay buffer which stores experience tuples collected by the agent. Rather than learning after each experience, it stores them in the replay buffer and samples small bathces of them randomly from time to time. This technique also allows the network for learn from individual experiences over and over again rather than discarding them after just learning once. Fixed Q-targets, on the other hand, fixes the instability involved with modifying the weights for both the optimal and estimated values during the update step, which can be analogized as a dog chasing its own tail. To address the issue, the DQN algorithm uses two networks, one to represent the estimated Q network and the other as a fixed target network to compute the loss. The target network is continually updated after a certain number of learning iterations.  

### Implementation

**Agent**
- 2 Q-networks and one replay buffer
- Act method: uses local network along with epsilon-greedy policy to output next action
- Step method: store experience tuple in replay buffer, and learns UPDATE_EVERY
- Learn method: updates local network with gradient descent through loss.backward and optimizer.step, soft updates target network

**Training:**
- Loop over episodes:
  - Reset environment, epsilon value, and observe initial state
  - Loop over time steps
    - Select action (Agent act method)
    - Execute selected action
    - Observe reward, next state, and done
    - Pass (state,action,reward,next_state, done) tuple to Agent (Agent step method)
      - Agent stores tuple in replay buffer
    - After UPDATE_EVERY iterations, sample batch of experiences from replay buffer and update network (Agent learn method)
      - Update target network after a certain number of updates

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
To improve performance, multiple future steps could be taken. For one, further improvements like Double DQN, Prioritized Experience Replay and Duelling networks could be implemented. In addition, different architectures of the Deep-Q network would be explored to better model the environment. Finally, more experimentation could be done with the hyperparameters! 