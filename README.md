# w251_hw11 by abhisha@berkeley.edu 

Here is an introduction to Q learning that was very helpful: https://www.novatec-gmbh.de/en/blog/introduction-to-q-learning/ 

#### 1. What parameters did you change?


#### 2. What values did you try?
#### 3. Did you try any other changes that made things better or worse?
#### 4. Did they improve or degrade the model? Did you have a test run with 100% of the scores above 200?
#### 5. Based on what you observed, what conclusions can you draw about the different parameters and their values?


#### 6. What is the purpose of the epsilon value?

The epsilon value captures the exploration vs exploitation factor. Taken from [here](https://towardsdatascience.com/simple-reinforcement-learning-q-learning-fcddc4b6fe56)

An agent interacts with the environment in 1 of 2 ways. The first is to use the q-table as a reference and view all possible actions for a given state. The agent then selects the action based on the max value of those actions. This is known as exploiting since we use the information we have available to us to make a decision.

The second way to take action is to act randomly. This is called exploring. Instead of selecting actions based on the max future reward we select an action at random. Acting randomly is important because it allows the agent to explore and discover new states that otherwise may not be selected during the exploitation process. You can balance exploration/exploitation using epsilon (ε) and setting the value of how often you want to explore vs exploit.


#### 7. Describe "Q-Learning".

Q learning is a form of a DRL algorithm that is used to learn the optimal decision policy in a markov process. The goal of Q learning is to find the optimal policy by learning the optimal Q values for each state action pair. It does this by storing the optimal Q values in a Q table, that consists of the Q values (expected reward) from following the policy for the corresponding state action pairs. So once we have the optimal Q values, we can ultimately maximize the expected average reward by playing a number of steps in an episode of the experiment / game. Q learning typically uses the Bellman equation for defining the Q function.

![bellman](https://github.com/abhisha1991/w251_hw11/blob/master/Bellman2.png)
