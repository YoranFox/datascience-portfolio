# MY PORTFOLIO

Name: Yoran de Vos
Student-number: 17049784
Group: NANO


## Introduction

*How can a Machine Learning model, that predicts the optimal thresholding algorithm, assist VSParticle to analyze nanoparticle images?*. This is the Research question for our project we came up with after analyzing the project. The project is based around a application developed by VSPARTICLE, that uses image processing to alter a image of nano particles so that they can analyze the nano particles better. In this application there is one step called the Thresholding step where they use a threhsolding method to create a bitmap of the image. VSPARTICLE wants to know which threshold method works best for a given image. They provided us with samples of different runs they did in the applications. These runs contain the scores calculated and values used during the run, but also the user score that was given to indicate how well the picture turned out. With help of these samples we have to come up with a machine learning model that predicts the best thresholding method.

<details>
  <summary>VSPARTICLE</summary>
  <br/>
  Product owner: Thomas Storck - Scientific Software Engineer  
  <br/>
  VSPARTICLE is a company based in Delft specialized in Nano particles, they are creating and using cutting edge technology to research nanoparticles and nanomaterials. The applications and tools that are created are being used by the industry and researchers. 
  
  [VSPARTICLE website](https://vsparticle.com/)
</details>




## Content

1. DataCamp Courses
2. Jargon
3. Domain Knowledge
4. Research
5. Predictive Analytics
6. Presentations
7. Final paper
8. Reflection


## Datacamp Courses

TODO

Progress of the total completion

List of completed courses with a link to screenshots of completed courses


## Jargon

The words used in this paper that are domain specific are defined below.

* Threshold algorithm: A algorithm that is used during image processing to define what pixels are white and black.
* User score: The score a user gives at the end of the image processing to determine how good the image looks.



## Research

### Research Plan

[Link to research plan](https://github.com/YoranFox/datascience-portfolio/blob/main/NANO%20%E2%80%93%20Research%20plan%20(1).pdf)

My contribution to the research plan is done in multiple ways. At the start of writing the plan I layed out the general aproach for researching the project and also splitting the research question in different sub-questions. The plan for the sub-question *How does the given data need to be restructured in order to be useful for the model?* was written by me.

### Method

When looking at the different ways to predict the best threshold method we spotted a problem in the data. For most of the pictures that are used there is only one predicted userscore. This is a problem since we dont know the score the same picture would have been given on the other threshold algorithms. At this point I came up with a different approach, we make a model that predicts the userscore instead of the best userscore. This can be done since the scores of a image are being calculated for every thershold algorithm. The picture below shows how the best threshold algorithm will be chosen.

<img src="https://github.com/YoranFox/datascience-portfolio/blob/main/Visualisation_predicting_threshold_method.png" style="float: left;" alt="alt text" width="200">

This new approach can be seen as a classification problem since the value that we are going to predict is labeled from 1 to 10. During our research into different kind of multiclass classification models we found 4 we wanted to try out. There are more methods that were available but since 2 of our project members stopped with the minor we wanted to limit ourselfs to these four. These models are: 
- Decision tree
- Random Forest Classifier
- Logistic Regression
- MLP Classifier


## Predictive Analystics

During the project I have worked on multiple models that could be aplied to our data. I did this to get a better understanding on how well different models work for our problem. When working on those models I documented my thoughts and systematicly went through all the steps. I also created the script that was used to create the data used in our experiment.

<details>
<summary>Polynomial Regression model</summary>
<br>
At the first stages during the project regression was still a option we were considering, so polynomial regression is one of the models I worked on to try and get the best result. For the feature seleciton for this model I used a corrolation matrix (made by Oscar). From that I chose the two features with the highest corrolation since they were by far better then the other ones. First I analyzed the features, then I chose the degree of the polynomial regression by making a learning curve. After that I analized the model with the chosen hyper parameters. After that I finalized the model. These steps are all documented and analyzed in the notebook.  
<br>

[Notebook - Polynomial Regression](https://datascience.hhs.nl:8888/user/17049784/notebooks/nano/Code%20Yoran/ML%20models/Seperation-border%20Regression.ipynb)

</details>


<details>
<summary>The experiment</summary>
<br>
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

<img src="https://github.com/YoranFox/datascience-portfolio/blob/main/Function_Itt_Experiment.png" alt="alt text" width="200" height="30">

*f = features amount, p = parameters amount, m = model amount, b = balancing method amount, i = iterations*

The output of the function with the parameters used in the experiment shows us that the script will run 5120 times. 

#### Results

The results we got from the script are saved in a DataFrame and exported to a folder. As a group we started to visualize the results to get insights into the data that was generated. I focussed on the balancing methods, for this I created a visualisation to see the relation between different balancing methods with Accuracy vs Classes amount for every model type. The accuracy values are the means of the models with every feature combination.

<img src="https://github.com/YoranFox/datascience-portfolio/blob/main/Experiment_Balancing acc vs classes.png" alt="alt text" width="800" height="400">

With help of this visualisation we were able to confirm that the Balancing method we were going to use in the final model is indeed the best one for that model. Because when you look at the Logistic Regression model you can see that Under sampling has the highest score.

</details>

## Presenations

During the project I have done 3 presenations. Two internal presentations and 1 external presentation.

**Internal**

- [Week 9 Powerpoint](https://dehaagsehogeschool.sharepoint.com/:p:/r/sites/AppliedDataScience_groups-Nano/_layouts/15/doc2.aspx?sourcedoc=%7BB0D173CA-224B-4D7D-979C-085B02D84F41%7D&file=Internal%20presentations%20wk%209.pptx&action=edit&mobileredirect=true&wdPreviousSession=23810d55-45db-4fe5-9490-e1dfe999f7f3&wdOrigin=TEAMS-ELECTRON.teams.undefined)     *(if this link doesnt work you can download the powerpoint [here](https://github.com/YoranFox/datascience-portfolio/raw/main/Internal%20presentations%20wk%209.pptx))*


**External**

- [Week 13 Powerpoint](https://dehaagsehogeschool.sharepoint.com/:p:/r/sites/AppliedDataScience_groups-Nano/_layouts/15/Doc.aspx?sourcedoc=%7BC86D1590-FEAC-4AC5-9508-A99400933EC6%7D&file=Public%20presentations%20wk%2013.pptx&action=edit&mobileredirect=true&wdPreviousSession=2725bdf9-260b-4e76-bf60-0a348ad6decf&wdOrigin=TEAMS-ELECTRON.teams.undefined)    *(if this link doesnt work you can download the powerpoint [here](https://github.com/YoranFox/datascience-portfolio/raw/main/Public%20presentations%20wk%2013.pptx))*

