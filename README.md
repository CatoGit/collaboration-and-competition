[//]: # (Image References)
[Tennis]: https://github.com/CatoGit/collaboration-and-competition/blob/master/Tennis.gif "Tennis"

# Collaboration and Competition using DDPG

In this project two agents control rackets and play tennis against each other. 
An agent receives +0.1 reward by hitting the ball over the net. Otherwise it receives a reward of -0.01.
Since both agents want to maximize their reward, both want to keep the ball in play as long as possible.

The task is episodic. After each episode, the sum of the rewards that each agent achieved is calculated (without discounting).
This results in two rewards (one for each agent). The maximum of these two is taken as the episode score.  
The environment counts as solved once the average score is at least +0.5 over 100 consecutive episodes.


![TennisPlay][Tennis]

## State and action space (Continuous)

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. 
Each agent has its own observations. 
Each agent has two continuous actions corresponding to movement toward or away from the net and jumping.

## Instructions
1. Follow the instructions [here](https://github.com/udacity/deep-reinforcement-learning#dependencies) to install all dependencies. 

2. The environment can be downloaded from one of the links below for all operating systems:
    * Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    * Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    * Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    * Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
    
3. Place the file in the `colandcomp/` folder and unzip it.

3. Train your DDPG agent using `ColandCompProject.ipynb`. 

4. Watch your trained agent. Enjoy!
