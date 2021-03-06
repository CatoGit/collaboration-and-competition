# Report

## Learning algorithm

The Deep Deterministic policy gradient (DDPG) algorithm is used for solving this environment.
The reason for using this algorithm is the continuous action space. In contrast to the single agent Continuous Control Project, there are two agents in this environment. Each agent receives its own observations.
Both agents use the same actor network to select actions and their experience is added to a shared replay buffer.
The DDPG uses two neural networks (actor & critic). The actor network approximates the optimal policy 
by mapping states to the best actions deterministically. 
The critic then uses these best actions to evaluate the action-value function.

The updates in the DDPG case are "soft target updates". These blend in a small amount of the regular network weights (e.g. 0.01%) to the target network weights. 
To explore better policies, noise is sampled into the actor policy.
To generate noise a normal distribution is used (Ornstein-Uhlenbeck process). 

### Neural network model architecture
The network architecture is similar to the one that is presented in the DDPG paper [[1]](https://arxiv.org/abs/1509.02971) and consists of an actor and a critic network. 

Actor:
* Layer 1: 8 input - 400 output
* Layer 2: 400 input - 300 output
* Layer 3: 300 input - 2 output

Critic:
* Layer 1: 8 input - 400 output
* Layer 2: 402 input - 300 output
* Layer 3: 300 input - 1 output 

### DDPG parameters

Both agents produce experience tuples (action, state, reward, next state) with every step in the environment. 
The DDPG stores these in the shared replay buffer. 
Every time step, the networks is updated 10 times. 
One update consists of sampling a batch size (1024) of experiences from the replay buffer
and then updating the actor network, the critic network and the target networks of both.
As suggested in the Udacity course, gradient clipping is used when updating the critic network. 

* Time steps per episode: 1000
* Discount factor: 0.99
* Replay buffer size: 1e6
* Batch size: 1024
* Timesteps between learning: 1
* Learning rate of the actor:  1e-4
* Learning rate of the critic:  1e-3
* Soft update parameter tau: 1e-3

### Results

First round of training:

```
Episode 100	Average Score: 0.0060
Episode 200	Average Score: 0.0510
Episode 300	Average Score: 0.0409
Episode 400	Average Score: 0.0610
Episode 500	Average Score: 0.0700
Episode 600	Average Score: 0.0920
Episode 700	Average Score: 0.1170
Episode 800	Average Score: 0.1479
Episode 900	Average Score: 0.1460
Episode 1000	Average Score: 0.2249
Episode 1100	Average Score: 0.2320
Episode 1200	Average Score: 0.2170
Episode 1300	Average Score: 0.2519
Episode 1400	Average Score: 0.2378
Episode 1500	Average Score: 0.2818
Episode 1600	Average Score: 0.3169
Episode 1700	Average Score: 0.3549
Episode 1800	Average Score: 0.3509
Episode 1900	Average Score: 0.3737
Episode 2000	Average Score: 0.4119
Episode 2100	Average Score: 0.4130
Episode 2200	Average Score: 0.4649
Episode 2225	Average Score: 0.4589
```

After a disconnect from the GPU, the training was continued with the checkpoints from the first round of training. 
After another 510 episodes, an average score of over +0.5 was achieved. This means, a total of 2735 episodes were needed to solve the environment.

![Results](Results2.png)

```
Episode 100	Average Score: 0.2178
Episode 200	Average Score: 0.2908
Episode 300	Average Score: 0.3389
Episode 400	Average Score: 0.3290
Episode 500	Average Score: 0.4469
Episode 510	Average Score: 0.5098
Environment solved in 510 episodes!	Average Score: 0.5098
```


### Possible future work

* make the agent learn from pixel input
* implement batch normalization
* implement the algorithm from the MADDPG Paper [[2]](https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf
)
