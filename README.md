# reinforcement_learning
Two reinforcement learning implementations based on Q learning and deep reinforcement learning using python

# dependency
- OpenAI Gym 
- PyTorch
# Q-Learning Agent Play Frozen Lake
Winter is here. You and your friends were tossing around a frisbee at the park when you made a wild throw that left the frisbee out in the middle of the lake. The water is mostly frozen, but there are a few holes where the ice has melted. If you step into one of those holes, you'll fall into the freezing water. At this time, there's an international frisbee shortage, so it's absolutely imperative that you navigate across the lake and retrieve the disc. However, the ice is slippery, so you won't always move in the direction you intend. The surface is described using a grid like the following:
This grid is our environment where S is the agent’s starting point, and it’s safe. F represents the frozen surface and is also safe. H represents a hole, and if our agent steps in a hole in the middle of a frozen lake, well, that’s not good. Finally, G represents the goal, which is the space on the grid where the prized frisbee is located.
![game1](https://github.com/HAOLI-TUKL/reinforcement_learning/blob/master/images/game1.png)
The agent can navigate left, right, up, and down, and the episode ends when the agent reaches the goal or falls in a hole. It receives a reward of one if it reaches the goal, and zero otherwise.
![game2](https://github.com/HAOLI-TUKL/reinforcement_learning/blob/master/images/game2.png)

## pseudo code for Q learning implementation

1. Initialize all Q-values in the Q-table to 0. 
2. For each time-step in each episode:
   1. Choose an action ( considering the exploration-exploitation trade-off). 
   2. Observe the reward and next state.
   3. Update the Q-value function ( using the formula we gave that will, overtime, make the Q-value function converge to the right hand side of the Bellman equation).
   
## Q table after learning
<img src="https://github.com/HAOLI-TUKL/reinforcement_learning/blob/master/images/game3.png" alt="none" width="500" height="313" align="bottom" />


# Deep reinforcement learning for the cart and pole problem
The cart and pole problem consists of a cart that can move left and right along a frictionless track. The cart has a pole attached to the top of it, which starts out in a vertical upright position, however, by design, the pole will fall either to the left or right when not balanced. The goal here is to prevent this pole from falling over. A reward of 
+
1
 will be given for each time step that the pole remains upright, and an episode will deemed over when the pole is more than 
15
 degrees from vertical or when the cart moves more than 
2.4
 units from the center of the screen.
<img src="https://github.com/HAOLI-TUKL/reinforcement_learning/blob/master/images/cartpole1.png" alt="none" width="500" height="313" align="bottom" />
## pseudo code for drl implementation

1. Initialize replay memory capacity. 
2. Initialize the policy network with random weights.
3. Clone the policy network, and call it the target network.
4. For each episode:  
   1. Initialize the starting state.  
   2. For each time step:  
      1. Select an action.  
         * Via exploration or exploitation. 
      2. Execute selected action in an emulator.  
      3. Observe reward and next state.
      4. Store experience in replay memory.  
      5. Sample random batch from replay memory.  
      6. Preprocess states from batch.  
      7. Pass batch of preprocessed states to policy network.  
      8. Calculate loss between output Q-values and target Q-values.
         * Requires a pass to the target network for the next state
      9. Gradient descent updates weights in the policy network to minimize loss.
         * After x time steps, weights in the target network are updated to the weights in the policy network.
 ## final plot after 1000 episodes
 ![cartport1](https://github.com/HAOLI-TUKL/reinforcement_learning/blob/master/images/cartpole2.png)

