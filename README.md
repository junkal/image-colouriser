# Image Colouriser
 
This image colouriser is an UNet model with ResNet18 backbone. It follows the blog written by [Moein Shariatnia](https://towardsdatascience.com/colorizing-black-white-images-with-u-net-and-conditional-gan-a-tutorial-81b2df111cd8). The training script in the Jupyter notebook follows the training script found in the [Github repository](https://github.com/moein-shariatnia/Deep-Learning/tree/main/Image%20Colorization%20Tutorial) with some edits.

The image colouriser model is trained in 2 stages as recommended by the author, using 20,000 images sampled from COCO-2017 dataset. The first stage trains the ResNet18 backbone with 15 epochs. This first stage training trains the ResNet backbone. The trained backbone is then used as the generator for the GAN. The second stage trains the whole generator on the task of colourisation. The second stage training is done with 20 epochs. The whole training process should take about 5.5 hr on Kaggle environment with GPU accelerator. The model is saved as **final\_model\_resnet18.ptz**

The details of the training is given by the notebook: _colourise-images-with-u-net-and-gan.ipynb_

The notebook _image\_colouriser\_inference.ipynb_ loads the model, reads in an image (presumably black and white image), extracts the L channel of the image to pass to the model to infer the colour (\*a and \*b) channels. Using the current  model with 20,000 train images at 15 & 20 epochs is able to infer pretty well for some images, but perform really badly for some others.

Sample outputs: