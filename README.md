# adversarial_networks
Tensorflow implementation of deep convolutional - generative adversarial networks deployed on AWS gpu instance


# Goals:
## Summary:
The goal here is to utilize two deep convolution neural networks to generate new styles of womens tops. These tops are trained on the more than 1 million styles of tops in Nordstrom's current inventory. I'll be using a tensorflow implementation of a deep convolutional generative adversarial network on an AWS gpu instance to speed up the neural network training.

## Training Data
I currently work at Trunk Club (a Nordstrom Company) which is an e-commerce fashion company. The business model is to ship personalized clothing to our customers who keep what they like and send back what they don't. Given we were acquired by Nordstrom, I have access to an incredible wealth of fashion images Nordstrom uses for their online store.

My training data stems from collecting 1.1M images of women's tops. A quick sample of the images is below:


![](/imgs/GIF_womens_tops.gif)
