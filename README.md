# covid-detection
A deep learning model based on CNN fro detecting and mapping covid affected chest x-rays images
So, this model is primarily focussed upon detecting Covid-19 using chest x-ray images. The dataset comprised of around 280 images containing equal no. of normal x-rays and covid affected chest x-rays. The no. of images are low because of the reason that x-ray images of covid affected patients are very low in number on the internet. So to overcome this, data augmentation has been done to increase and generalise what the model sees on the available no. of images.

# Model Architecture:

![model (1)](https://user-images.githubusercontent.com/17724496/80915132-bc666400-8d6d-11ea-9aa5-b7f4c4f7714f.png)


So the first layer is a CNN layer and respective layers can be seen in the depicted figure.
Upon completion of training process, the graph for training accuracy looked something like:


![acc](https://user-images.githubusercontent.com/17724496/80915201-63e39680-8d6e-11ea-9617-ea0146f67cd5.png)


The testing accuracy was something like:

![test](https://user-images.githubusercontent.com/17724496/80915234-a1482400-8d6e-11ea-943a-cc396f100978.png)

We were able to achieve 97% accuracy on training data and 96% on validation data.

The confusion map for the same was:

![cm](https://user-images.githubusercontent.com/17724496/80915275-d785a380-8d6e-11ea-8886-4bce7380d9f7.png)

Our model was able to classify almost all x-ray images correctly. Only two images were wrongly classified.


# Grad-CAM :
In order to further visualise what our model is actually trying to capture in such x-ray images, we used class activation maps. In our project we have used gradient based Grad-CAM for depicting what the model actually sees.
uses the gradient information flowing into the last convolutional layer of the CNN to understand each neuron for a decision of interest. This results in a coarse heatmap of the same size as that of the convolutional feature maps.

Original X-RAY of a Covid affected person:

![x1](https://user-images.githubusercontent.com/17724496/80915810-38fb4180-8d72-11ea-9dcb-1bc5deb61567.png)

Grad-CAM Visualised X-RAY:

![x1g](https://user-images.githubusercontent.com/17724496/80915831-592b0080-8d72-11ea-8162-6bddbe943846.png)

Original X-RAY of a covid affected-person:

![x2](https://user-images.githubusercontent.com/17724496/80915882-a909c780-8d72-11ea-9213-b365bc4afc2d.png)

Grad-CAM Visualised X-RAY:

![x2g](https://user-images.githubusercontent.com/17724496/80915884-ab6c2180-8d72-11ea-9f61-0dc9f710156a.png)

Original X-RAY of a covid affected-person:

![x3](https://user-images.githubusercontent.com/17724496/80915926-f7b76180-8d72-11ea-817f-584fd70df146.png)

Grad-CAM Visualised X-RAY:

![x3g](https://user-images.githubusercontent.com/17724496/80915928-fab25200-8d72-11ea-8072-db43e52c9ca0.png)


As from the class activation maps, we can see that the model is trying to figure out something(infections) in the respiratory tract, which is indeed a probable criterion for covid detection. And if a normal x-ray image is passed to the model, the visualisations look something like:

Original X-RAY of a normal person:

![n1](https://user-images.githubusercontent.com/17724496/80916119-6c3ed000-8d74-11ea-957e-68cc48c46e61.png)

Grad-CAM Visualised X-RAY:

![n1g](https://user-images.githubusercontent.com/17724496/80916121-706aed80-8d74-11ea-8a96-316e6d440bc1.png)

Original X-RAY of a normal person:

![n2](https://user-images.githubusercontent.com/17724496/80916161-a3ad7c80-8d74-11ea-82fb-eaec06b2b559.png)

Grad-CAM Visualised X-RAY:

![n2g](https://user-images.githubusercontent.com/17724496/80916165-a7410380-8d74-11ea-820b-ab8d90fb7162.png)

As it can be seen from normal x-ray images, the model is not able to find any vulnerabilities(or infections) around the area of the lungs, and hence no heat map is drawn there. This means our model has learned quite a bit to detect anomalies in x-ray images between a normal one and a covid affectd one.

However this is not a complete replacement of a medical professional. Instead this model can be used by a medical professional and upon seeing the results of the model, appropriate decisions can be made. Since the model highlights the affected parts in a covid affected person's xray, the medical profeesional could use this result in their decisions.

However since this model has been trained on quite a less amount of data, due to unavailability of x-ray images of covid affected person, the model might sometime not fetch the expected results. Hence this model can in actual perfrom well equipped with the help of a medical professional.
