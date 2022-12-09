# Project 1 Navigation

Thanks to Udacity for creating a very interesting project, the source code in their lessons helped me a lot.

The solution code uses:

- Vanilla Deep Q-Network;
- Double Deep Q-Network to avoid oscillations caused by overestimated Q-values;
- Experience Replay in order to keep training the Q-Network with past experiences;
- Epsilon Greedy with geometric decay of 0.995, in order to balance exploration at the begining (epsilon=1) versus explotation at the end (epsilon=0.01);
- Adam optimizer with learning rate of 5e-4;
- BATCH_SIZE=64 (the number of experience tuples per training iteration);
- GAMMA=0.99 (the Q-Network is aware of the intermediate future, but not the far future);
- A deep neural network to represent complex continuous states.

The deep neural network to represent complex continuous states has:

- A linear fully-connected layer of dimensions state_size=37 and fc1_units=64;
- A linear fully-connected layer of dimensions fc1_units=64 and fc2_units=64;
- A linear fully-connected layer of dimensions fc2_units=64 and action_size=4.

## Plot of Rewards

The Q-Nework was trained for 706 episodes. In each episode, the agent is trained from the begining to the end of the simulation. Some episodes are larger and some episodes are shorter, depending when the ending condition of each episode appears. Each episode has many iterations. In each iteration, the Q-Network is trained with `BATCH_SIZE=64` experience tuples (SARS).

```
Episode 100 Average Score: 1.26
Episode 200 Average Score: 4.76
Episode 300 Average Score: 7.79
Episode 400 Average Score: 10.93
Episode 500 Average Score: 13.22
Episode 600 Average Score: 14.47
Episode 616 Average Score: 15.00
Environment solved in 516 episodes! Average Score: 15.00
```

The rubric asks to obtain an average score of 13 for 100 episodes but I increased that value to 15. As a result, the Q-Network achieved an average score greater than 15 in 516 episodes of training. In the graph, the blue lines connect the scores in each episode. Whereas the red lines connect the average scores in each episode.

![Plot of rewards (training)](/plot_training.png)

After training, the saved model was loaded and tested for 20 episodes. Here are the results of such testing. You can see that on average, the scores are greater than 13.

![Plot of rewards (testing)](/plot_testing.png)

Ideas about Future Works:

1. Increase epoch to increase the performance of agent

2. applying different extensions of DQN:

```
Double DQN (DDQN)
Prioritized experience replay
Dueling DQN
Noisy DQN
etc...
```
