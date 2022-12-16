# Deep-Reinforcement-Learning-2.0

This repository is a record of what I studied in a course on building intensified deep learning models in Python provided by Udemy.

Link: https://www.udemy.com/course/deep-reinforcement-learning/

# Steps of building model
* Step 1.

  initialize the Experience Replay memory

* Step 2.

  build one neural network for the Actor model and one neural network for the Actor target
  ![step2](https://user-images.githubusercontent.com/28240052/208119965-007094e9-418f-4b53-b188-eb4c73f58400.png)  

* Step 3.

  build two neural networks for the two Critic models and two neural networks for the two Critic targets
  
* Step 4.

  Sample a batch of trasitions (s, s', a, r) from the memory. Then for each element of the batch
  
* Step 5.

  From the next state s’, the Actor target plays the next action a’
  
* Step 6.

  add Gaussian noise to this next action a’ and we clamp it in a range of values supported by the environment
  
* Step 7.

  The two Critic targets take each the couple (s’, a’) as input and return two Q-values Qt1(s’,a’) and Qt2(s’,a’) as outputs
  
* Step 8.

  Keep the minimum of these two Q-values: min(Qt1, Qt2)

* Step 9.

  Get the final target of the two Critic models, which is: Qt = r + γ * min(Qt1, Qt2), where γ is the discount factor

* Step 10.

  The two Critic models take each the couple (s, a) as input and return two Q-values Q1(s,a) and Q2(s,a) as outputs

* Step 11.

  Compute the loss coming from the two Critic models: Critic Loss = MSE_Loss(Q1(s,a), Qt) + MSE_Loss(Q2(s,a), Qt)

* Step 12.

  Backpropagate this Critic loss and update the parameters of the two Critic models with a SGD optimizer

* Step 13.

  Once every two iterations, update our Actor model by performing gradient ascent on the output of the first Critic model

* Step 14.

  Still once every two iterations, we update the weights of the Actor target by polyak averaging

* Step 15.

  Still once every two iterations, we update the weights of the Critic target by polyak averaging

|  | Deep Q-Learning | Policy Gradient | Actor-Critic | World Models |
| --- | --- | --- | --- | --- |
| Model-Free vs Model-Based | Model-Free | Model-Free | Model-Free | Model-Based  |
| Value-Based vs Policy-Based | Value-Based | Policy-Based | Both | Policy-Based |
| Off-Policy vs On-Policy | Off-Policy | On-Policy | Off-Policy | On-Policy |


