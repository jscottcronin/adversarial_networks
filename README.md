# adversarial_networks
Tensorflow implementation of deep convolutional - generative adversarial networks deployed on AWS gpu instance


# Goals:
## Summary:
Utilize two deep convolution neural networks to generate images of womens tops which replicate the design of the images used to train the models. I'll be using a tensorflow implementation of a deep convolutional generative adversarial network on an AWS gpu instance to speed up the network training.

## Training Data
I currently work at Trunk Club (a Nordstrom Company) which is an e-commerce fashion company. The business model is to ship personalized clothing to our customers who keep what they like and send back what they don't. Given we were acquired by Nordstrom, I have access to an incredible wealth of fashion images Nordstrom uses for their online store.

My training data stems from collecting 1.1M images of women's tops. A quick sample of the images is below:


![](/imgs/GIF_womens_tops.gif)
