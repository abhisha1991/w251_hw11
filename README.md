# w251_hw11 by abhisha@berkeley.edu 

Here is an introduction to Q learning that was very helpful: https://www.novatec-gmbh.de/en/blog/introduction-to-q-learning/ 

#### 1. What parameters did you change?

I tried to change several parameters - including self.density_first_layer, self.density_second_layer, learning rate, self.epsilon_min, self.batch_size, self.gamma and self.epsilon_decay. I even tried adding a third layer in the neural network. 

#### 2. What values did you try?

Ultimately, in the final attempt, only changing the density of the layers of the neural network + changing the activation function in the network layer helped. All other params - learning rate, gamma, epsilon were left unchanged. Ultimately, the neural network was trained with 512 density in layer 1, 256 density in layer 2 and the activation for layer 2 was changed to "tanh" instead of "relu".

#### 3. Did you try any other changes that made things better or worse?

Contrary to the belief that adding more layers would help, more layers in the neural network possibly led to overfitting, as it gave us lower training rewards (around -80) and gave us worse test rewards (less than -200). By making the epsilon decay an order of magnitude smaller (0.90 vs 0.995 original) - which didnt seem like much of a change, we realized that this actually made the epsilon value decay much more quickly over the iterations compared to before. To counteract how much the "floor" of the epsilon could be, I tried setting it to 0.4 instead of the original 0.01, but that didnt seem to have any improvement in performance either. Finally, just changing the learning rate without changing the neural network architecture also didnt seem to give any performance improvement. No performance improvement was observed by just changing the gamma value either. 

#### 4. Did they improve or degrade the model? Did you have a test run with 100% of the scores above 200?

We got pretty close. If we look at the below (our final attempt), we see that most runs were >200. Also to note, during training, we reached the 200 reward mark after 450 iterations. We however, did NOT run all 100 test iterations because the inference was taking too long (the Tx2 was running out of memory and to run a single inference (1 step out of 100 test steps), it was taking between 10-20 seconds)

![img](https://github.com/abhisha1991/w251_hw11/blob/master/final/test_perf.PNG)

#### 5. Based on what you observed, what conclusions can you draw about the different parameters and their values?


#### 6. What is the purpose of the epsilon value?

The epsilon value captures the exploration vs exploitation factor. Taken from [here](https://towardsdatascience.com/simple-reinforcement-learning-q-learning-fcddc4b6fe56)

An agent interacts with the environment in 1 of 2 ways. The first is to use the q-table as a reference and view all possible actions for a given state. The agent then selects the action based on the max value of those actions. This is known as exploiting since we use the information we have available to us to make a decision.

The second way to take action is to act randomly. This is called exploring. Instead of selecting actions based on the max future reward we select an action at random. Acting randomly is important because it allows the agent to explore and discover new states that otherwise may not be selected during the exploitation process. You can balance exploration/exploitation using epsilon (ε) and setting the value of how often you want to explore vs exploit.


#### 7. Describe "Q-Learning".

Q learning is a form of a DRL algorithm that is used to learn the optimal decision policy in a markov decision process. The ‘Q’ in Q-learning stands for quality. Quality here represents how useful a given action is in gaining some future reward. The goal of Q learning is to find the optimal policy by learning the optimal Q values for each state action pair. It does this by storing the optimal Q values in a Q table, that consists of the Q values (expected reward) from following the policy for the corresponding state action pairs. So once we have the optimal Q values, we can ultimately maximize the expected average reward by playing a number of steps in an episode of the experiment / game. Q learning typically uses the Bellman equation for defining the Q function.

![bellman](https://github.com/abhisha1991/w251_hw11/blob/master/Bellman2.png)

Q learning is a values based learning algorithm, because it iteratively (over a number of episodes) learns the Q values (for each state action pair) using the Bellman equation, until the Q function converges to the optimal Q function (Q*). Here is an [example](https://www.youtube.com/watch?v=qhRNvCVVJaA) of the lizard game that uses the Q learning algorithm. So in essence, Q learning uses value iteration (the Q table) to perform learning as opposed to policy based iteration. Policy-based learning algorithms estimate the value function with a greedy policy obtained from the last policy improvement.

Q learning is also "model free" learning because there is no explicit model that the agent needs to learn. The learning for the agent happens as a result of the derivation of an optimal policy based on its interaction with its environment.
