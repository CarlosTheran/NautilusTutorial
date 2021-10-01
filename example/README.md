
# Facial Image Analysis using Containers on Nautilus

This file contains an example how you can run your deep learning program on your container. In particular, we are going to be using 
the image for DataScience that can be found [here](https://gitlab.nrp-nautilus.io/prp/jupyter-stack/container_registry/).

### Creating your pod 

Download the pod [datascience-pod](https://github.com/CarlosTheran/NautilusTutorial/blob/main/example/datascience-pod.yaml) 
and save it into your pod folder, then execute you pod. For more detail see [here](https://github.com/CarlosTheran/NautilusTutorial/blob/main/creating%20executing%20a%20pod/kubectl_pods.md).



### Abstract
This project uses artificial intelligence to explore the possibility of using facial image analysis to detect Autism in children. Early detection and diagnosis of Autism, along with treatment, is needed to minimize some of the difficulties that people with Autism encounter. A specialist usually diagnoses Autism through various Autism screening methods. This can be an expensive and complex process. Many children that display signs of Autism go undiagnosed because their families lack the expenses needed to pay for Autism screening and diagnosing. The development of a potentially inexpensive but accurate way to detect Autism in children is necessary for low-income families. In this project, a Convolutional Neural Network (CNN) is utilized, along with a dataset obtained from Kaggle. This dataset consists of collected images of male and female autistic and non-autistic children between the ages of two to fourteen years old. These images are used to train and test the CNN model. When one of the images is received by the model and importance is assigned to various features in the image, an output variable (autistic or non-autistic) is received.

*For original source visit* [project](https://cybertraining-dsc.github.io/report/su21-reu-378/project/)

