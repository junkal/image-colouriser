# Image Colouriser
 
This image colouriser is an UNet model with ResNet18 backbone. It follows the blog written by [Moein Shariatnia](https://towardsdatascience.com/colorizing-black-white-images-with-u-net-and-conditional-gan-a-tutorial-81b2df111cd8). The training script in the Jupyter notebook follows the training script found in the [Github repository](https://github.com/moein-shariatnia/Deep-Learning/tree/main/Image%20Colorization%20Tutorial) with some edits. Kudos and credits to this author for the good explanation and documentation.

The image colouriser model is trained in 2 stages as recommended by the author, using 20,000 images sampled from COCO-2017 dataset. The first stage trains the ResNet18 backbone with 15 epochs. This first stage training trains the ResNet backbone. The trained backbone is then used as the generator for the GAN. The second stage trains the whole generator on the task of colourisation. The second stage training is done with 20 epochs. The whole training process should take about 5.5 hr on Kaggle environment with GPU accelerator. 

The details of the training is given by the notebook: _colourise-images-with-u-net-and-gan.ipynb_. The final trained model is saved as **final\_model\_resnet18.pt**. 

The notebook _image\_colouriser\_inference.ipynb_ loads the model, reads in an image (presumably black and white image), extracts the L channel of the image to pass to the model to infer the colour (\*a and \*b) channels. The final trained model weighs can be downloaded from Google drive - the download link is provided in this notebook. The model is able to infer pretty well for some images, but perform really badly for some others.

Sample outputs:

![image](https://user-images.githubusercontent.com/6497242/170062727-60a720a0-2ea3-44db-a313-439d7cfb59ca.png)

The colourisation here is somewhat decent, except for the red patch on the top right hand side of the image.

![image](https://user-images.githubusercontent.com/6497242/170063102-47d28da6-7866-43ff-89d8-99f795502445.png)

Looks generally acceptable except for the wrong sky colours on the top of the image.

![image](https://user-images.githubusercontent.com/6497242/170064117-dff575f0-66ef-4e7a-892a-74ad1e11432c.png)

This is not good.

Certainly, there are rooms for improvements that can be made to improve the model, such as training with more images and training the overall UNet model with more epochs, changing the backbone model. Because I use the free GPU credits on Kaggle, and the training is very GPU hours heavy, all these improvements can only be implemented slowly over time.
