# Deep-Reinforcement-Learning-2.0

This repository is a record of what I studied in a course on building intensified deep learning models in Python provided by Udemy.

Link: https://www.udemy.com/course/deep-reinforcement-learning/

# Steps of building model
* Step 1.

  initialize the Experience Replay memory
![step1](https://user-images.githubusercontent.com/28240052/208210637-4896e675-3637-41dd-aca4-424c10a2cd82.png)

* Step 2.

  build one neural network for the Actor model and one neural network for the Actor target
  ![step2](https://user-images.githubusercontent.com/28240052/208119965-007094e9-418f-4b53-b188-eb4c73f58400.png)  

* Step 3.

  build two neural networks for the two Critic models and two neural networks for the two Critic targets
![step3](https://user-images.githubusercontent.com/28240052/208121558-0e99fe1f-d2a0-4bf4-876d-847de5faad05.png)
  
  
* Step 4.

  Sample a batch of trasitions (s, s', a, r) from the memory. Then for each element of the batch
  ![Step4-1](https://user-images.githubusercontent.com/28240052/208210801-552c222f-9b5a-4d9a-a052-2a436b014af3.png)
![Step4-2](https://user-images.githubusercontent.com/28240052/208210806-3e5b70fc-0729-4d79-9a39-9a1b8106e970.png)
  
  
* Step 5.

  From the next state s’, the Actor target plays the next action a’
  ![Step5](https://user-images.githubusercontent.com/28240052/208210893-ca8545c7-1ee1-4cea-a7d7-95eb208ae425.png)

  
* Step 6.

  add Gaussian noise to this next action a’ and we clamp it in a range of values supported by the environment
  ![Step6](https://user-images.githubusercontent.com/28240052/208211088-3b644a87-e458-45e2-8869-5eebfbd1faf2.png)

  
* Step 7.

  The two Critic targets take each the couple (s’, a’) as input and return two Q-values Qt1(s’,a’) and Qt2(s’,a’) as outputs 
![Step7](https://user-images.githubusercontent.com/28240052/208211133-7a5ea6cd-10a5-4943-ad22-17dbd02833af.png)


  
* Step 8.

  Keep the minimum of these two Q-values: min(Qt1, Qt2)
  ![Step8](https://user-images.githubusercontent.com/28240052/208211263-82b85d22-fd81-4ed8-9e25-c0874c5ad069.png)


* Step 9.

  Get the final target of the two Critic models, which is: Qt = r + γ * min(Qt1, Qt2), where γ is the discount factor
  ![Step9](https://user-images.githubusercontent.com/28240052/208212239-0e0e29cf-e237-4d2b-ad4a-30ce4dfbb8e9.png)


* Step 10.

  The two Critic models take each the couple (s, a) as input and return two Q-values Q1(s,a) and Q2(s,a) as outputs
  ![Step 10](https://user-images.githubusercontent.com/28240052/208212247-aa56c3d1-f7fd-49a4-984d-7ce9e04d6720.png)


* Step 11.

  Compute the loss coming from the two Critic models: Critic Loss = MSE_Loss(Q1(s,a), Qt) + MSE_Loss(Q2(s,a), Qt)
  ![Step 11](https://user-images.githubusercontent.com/28240052/208212252-7ac52521-472c-4c7e-81ee-4dce6b36eab2.png)

* Step 12.

  Backpropagate this Critic loss and update the parameters of the two Critic models with a SGD optimizer
  ![Step 12](https://user-images.githubusercontent.com/28240052/208212266-b39e2d32-aaf2-4fbf-b6cf-a55b3cbe29c4.png)

* Step 13.

  Once every two iterations, update our Actor model by performing gradient ascent on the output of the first Critic model
  ![Step 13](https://user-images.githubusercontent.com/28240052/208212272-83e25ef8-8cb2-4253-90e6-ca888e3a07db.png)


* Step 14.

  Still once every two iterations, we update the weights of the Actor target by polyak averaging
  ![Step 14](https://user-images.githubusercontent.com/28240052/208212279-0d04c553-7108-45ac-9eec-5cfc2c7196df.png)


* Step 15.

  Still once every two iterations, we update the weights of the Critic target by polyak averaging
  ![Step 14](https://user-images.githubusercontent.com/28240052/208212289-0bed8c1b-4c66-4f8d-85c1-328980e71305.png)
# What is Q Learning?

![Q learning](https://user-images.githubusercontent.com/28240052/208212431-bda107e8-b1c6-40be-b35a-671978330f01.png)

# What is Policy Gradient?

![policy gradient](https://user-images.githubusercontent.com/28240052/208212442-8f09816a-78b1-4f90-aef6-9236a187f0b0.png)



