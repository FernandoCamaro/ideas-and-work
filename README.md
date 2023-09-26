# Ideas and Work

Here I describe current ideas and work I am doing.\
If code available, it can be access by clicking in the associated section title.

## [hijepa](https://github.com/FernandoCamaro/HIJEPA)
Extension of [IJEPA](https://github.com/facebookresearch/ijepa) to the hierarchical setup with some additional features.\
Currently [working on it](https://github.com/FernandoCamaro/HIJEPA)

## [μ-zero](https://github.com/FernandoCamaro/muzero)
My attempt to implement Mu-zero in Pytorch, right after the paper was published.\
I trained an agent in the Tic-Tac-Toe environment, but the resulting policies are not strong.\
Need to revisint this project.

## [self-supervised-picking](https://github.com/FernandoCamaro/self-supervised-picking)
DQN agent trained to pick objects with success grasp self-supervision. 

## [imitation learning](https://github.com/FernandoCamaro/imitation_learning)
I explored some basic imitation learning algorithms in a VR environment.

## [adversarial diayn](https://github.com/FernandoCamaro/adiayn/tree/adiayn)
Trying some ideas based on adversarial learning to the Diversity-Is-All-You-Need (DIAYN) algorithm.

## Other ideas to explore

### [Analogy-discovery](Analogy-discovery.md)
I would like to explore that learns to create analogies from examples.

### Indepence of latent factors
Will it of any help to try to obtain embeddings whose components are independent?\
We can have a discriminator that tries to predict the value of one component given the others, while the encoder tries the opposite.\
Furthermore, can be useful to apply this idea not only for a VAE but also in all internal layers of network?

### Symmetric version of [OpenAI paper on Asymmetric Self-Play](https://arxiv.org/abs/2101.04882)
Due to the asymetry in the original paper the game could be harder and unfair for one of the two players.\
For example, if Bob sets the goals by reaching them, it could set them by creating some caotic situation difficult for Alice to replicate, like kicking a ball towards some objects. It is importat at least that Bob can robustly reach the goals he sets.\

### GANs with a third player
Again, GANs are not symmetric, however we can maybe improve the learning if there is a third agent that changes the labels\
in order to keep a more balanced game.\ For example, if the discriminator is correctly classifying all the fake samples, this agent could change the labels of 40% of the fake samples to real.

### RL with diminishing state
Normally we want an agent work with images as input, but that normally requires a lot of training as compared to using the high-level state of the environment, like the positions and orientation of all the objects. What if we start training the agent with both inputs, image observation and states and then we gradually remove the state input? Wouldn't it be easier for the agent to learn the policy in the image space?