---
layout: default
use_math: true
comments: true
---
 
#### Reinforcement Learning

As opposed to standard supervised / unsupervised learning, reinforcement learning aims to maximize a total reward in an environment by taking an action at particular timestamp given state at that timestamp.

Note: Total reward being maximized is over all future timestamps. 

##### Notations

We assume that we have a RL agent that takes action $a_t$ at timestamp $t$ given a state $s_t$ and get a reward $r_t$

The total reward is $ R_t = \sum_{i=t}^{n} r_i$. 

In reality we add a discounting factor $\gamma$ to rewards that are too far off, which results in $\sum_{i=t}^{n} \gamma^i r_i$

#### Q function

The function relates the total reward we can recieve by taking an aciton $a_t$ in the state $s_t$

$ Q(s_t, a_t) = \mathbb{E}[R_t \| s_t, a_t] $

#### Policy

Another function $\pi (s)$ that takes a state and determines best action to take in that state.

One greedy policy to just pick the action that leads to maximum expected total reward.

$\pi_\* (s) = argmax_a Q(s, a) $


This leads to two different forms of RL algorithms:

- Value Learning
	- Find Q function and use greedy policy.
- Policy Learning
	- Learn the direct policy
	- Sample actions $a \~ \pi (s) $


#### Value Learning

Deep Neural Network can output $Q_ k$ for each possible action $a_k$.


We can design a loss function based on the reward recieved for action $a_t$ , i.e $r$ plus the discounted reward for action after that, $\gamma * max Q(s', a')$

Q Loss = $ \|\| r_t +  \gamma * max Q(s', a') - Q(s, a) \|\|\_{2} $


#### Deep Q Learning

- Downsides:
	- Discrete action space.
	- No stochasticity.

Steps in Deep Q Learning:
- Provide the state of the environment to the agent. 
- The agent uses Target Network and Q-Network to get the Q-Values of all possible actions in the defined state.
	- Q Network is used to pick the current action which hopes to achieve a Q value $Q$.
	- Based on the current action, we get to new state. The reward we saw in the current state + the Q value obtained in the next state ( this time using target network ) ( $Q'$ ) gives the expected total reward.
	- The difference between expected reward: $ R_t + Q'\_t+1 $ and proposed reward from Q network $Q$ needs to be minimized.
- Pick the action a, based on the epsilon value. Meaning, either select a random action (exploration) or select the action with the maximum Q-Value (exploitation).
- Perform action a
- Observe reward r and the next state s’
- Store these information in the experience replay memory <s, s’, a, r>
- Sample random batches from experience replay memory and perform training of the Q-Network.
- Each Nth iteration, copy the weights values from the Q-Network to the Target Network.
- Repeat steps 2-7 for each episode

To Summarize main steps are:

- Get current action and calcuated current and expected rewards
	- Use exploration vs exploitation while choosing current action.
- Save Experences $(s, s\', a, r)$ and perform experience replay
- Update target network


#### Policy gradient

Probability that a action is good given a state.

We learn a distribution $ P (a \| s) $, for example if we assume $P$ is a normal distribution, we learn the parameters $\mu$ and $\sigma$ for defining this distribution over continous actions. Then we can sample an action from this distribution.