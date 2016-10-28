## - [Generative Adversarial Text to Image Synthesis] (https://arxiv.org/abs/1605.05396)

TLDR; Using a DCGAN to generate appropriate images for a given text. G uses a random noise z with text encoder outputs to generate a synthetic image x to feed into D. A training sample x is also fed into D. Both are processed and combined with text encoder outputs and determined if from training sample or not. D will also be fed a synthetic image composed on incorrect text encoder outputs and it will have to classify as NOT from training data. So the generator really has to learn how to make images to fool D that also make sense with the given text. 
![general](images/text2image/general.png)

### Detailed Notes:
- Objective: 
Recall that D will always try to predict the probability that a given sample is from the training data. The first term is for the discriminator and we want to maximize it since we want D to predict that x is from training (since it is) with high probability. The second term is for the generator and we want to minimize it since it is 1 - D(G(z)) bc we want the D(G(z)) to be high since we expect G to trick D, so we want to minimize 1-D(G(z)). 
![objective](images/text2image/objective.png)

- Loss
Our loss is based on 0/1 loss which gives 0 if our prediction is correct and 1 if not correct. We compute the loss for both the images and the text descriptions. 
![loss](images/text2image/loss.png)

- DCGAN
Both G and D are conditioned on text features.
![dcgan](images/text2image/dcgan.png)

- Generator
G is used to take the noise input z and the text encoder outputs in order to create the synthetic image x. So ALL G does is create a synthetic image with a text. It will go through D where is it concatenated with the same text but the synthetic image first goes through several convolution operations.
![generator](images/text2image/generator.png)

- Discriminator
D is used take in an image, perform some convolution and then depth concat with the text encoder outputs, perform further convolution and determine if sample is from training or not. 
![discriminator](images/text2image/discriminator.png)

- Tasks
Recall that our generator creates a synthetic image and feeds into D. Also recall that our training data simply takes an image and feeds into D. The CORRECT text description for this image is used inside D as well as when constructing synthetic image in G. However, the discriminator is just processing the images it gets, it doesn't know if the text we supply is appropriate or not. Note that we pretrain D on the training data, so in the beginning it can easily separate the training data from synthetic images. But later on it will become more and more difficult. If it only uses the images, it will be difficult to distinguish synthetic from training, so it also needs to factor in for the sentence. So, the discriminator will have three tasks:

	1. Identify REAL images w/ APPROPRIATE text as TRUE
	2. Identify FAKE images w/ APPROPRIATE text as FALSE
	3. Identify FAKE images w/ INCORRECT text as FALSE
	
This gives another signal to G, telling it that it has to not only learn to create synthetic images but learn to create synthetic images that are appropriate for the given text.
![general2](images/text2image/general2.png)








