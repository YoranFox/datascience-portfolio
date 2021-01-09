# MY PORTFOLIO

TODO (Personal information)



## Introduction

TODO


## Content

1. DataCamp Courses
2. Jargon
3. Research
4. Predictive Analytics
5. Data Preprocessing
6. Domain Knowledge
7. Presentations
8. Final paper


## Datacamp Courses

TODO

Progress of the total completion

List of completed courses with a link to screenshots of completed courses


## Jargon

The words used in this paper that are domain specific are defined below.

* Threshold algorithm: A algorithm that is used during image processing to define what pixels are white and black


## Research

### Research Plan

[Link to research plan](https://github.com/YoranFox/datascience-portfolio/blob/main/NANO%20%E2%80%93%20Research%20plan%20(1).pdf)

My contribution to the research plan is done in multiple ways. At the start of writing the plan I layed out the general aproach for researching the project and also splitting the research question in different sub-questions. The plan for the sub-question *How does the given data need to be restructured in order to be useful for the model?* was written by me.

## Predictive Analystics

During the project I have worked on multiple models that could be aplied to our data. I did this to get a better understanding on how well different models work for our problem. When working on those models I documented my thoughts and systematicly went through all the steps. I also created the script that was used to create the data used in our experiment.

### Polynomial Regression model

At the first stages during the project regression was still a option we were considering, so polynomial regression is one of the models I worked on to try and get the best result. For the feature seleciton for this model I used a corrolation matrix (made by Oscar). From that I chose the two features with the highest corrolation since they were by far better then the other ones. First I analyzed the features, then I chose the degree of the polynomial regression by making a learning curve. After that I analized the model with the chosen hyper parameters. After that I finalized the model. These steps are all documented and analyzed in the notebook.

[Notebook - Polynomial Regression](https://datascience.hhs.nl:8888/user/17049784/notebooks/nano/Code%20Yoran/ML%20models/Seperation-border%20Regression.ipynb)

### The experiment

For our project we wanted to know what model and feature combination would work best to predict the user score. To find this out we chose to go for a brute force method, by trying out all posible combinations and generating a model for that. After which we calculated scores that we could use to compare and get the best possible combination. The script that generated this data is programmed by me. 

#### Method
The script is created in a way so that it is expendable and easely altered to generated different kind of data. To do this I came up with a modular system where you can add models and balancing methods by adding a function. Then it was possible to pick which functions are used to generate the data. Also a lot of variables like the features and label names are changable. In this script for all models the data is also balanced and splitted in x amount of classes defined by the current itteration. The scaling and genrating of the scores is done the same way in all itterations.

#### Generated Data
The models and balancing methods used during the experiment are chosen by looking at and researching different options. Also other projects are looked at when deciding the options. We ended up with these options:

Models:
- Decision tree
- Random Forest Classifier
- Logistic Regression
- MLP Classifier

Balancing methods:
- No Balancing
- Random Oversampling
- SMOTE
- Cluster based Oversampling SMOTE

Classes: 2 - 5

Scaler: Power Transformer (Box-Cox)

Scores generated: Accuracy, recall, precision and Mean absolute error

The data that is generated is done by training and validating the model with k-fold cross validation. The amount of models  that are created and validated can be calculated by using the following funciton: 
![alt text](http://url/to/img.png)

#### Results