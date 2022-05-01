# Neural_Network_Charity_Analysis

## Overview

Beks is a data scientist and programmer at AlpabetSoup, which is a philanthropic foundation dedicated toward helping organizations that protect the environment, improve people's well-being, and unify the world.  Over the past two decades, they have raised and donated over $20 billion!  With these massive amount of money being used to hopefully improve the world, they want to ensure that the money is actually working towards accomplishing that goal (as opposed to being wasted or used inefficiently, going towards corruption instead of actual philanthropy, or simply falling through the cracks).

As Beks is in charge of data collection and analysis of the entire organization, her job is to analyze the impact of each donation and vet potential recipients in an attempt to ensure that the foundation's money is being used effectively.  As a result, the organization's president has asked her to help determine which organizations are worth giving to and which are simply too risky.  He wants her to create a mathematical, data-driven solution which can accomplish that task accurately.  Since the problem is so complex, she decides to go with a deep learning neural network which will accept all types of input data and produce a clear result.  Due to both the scale and the importance of this project, she has asked us for our assistance in getting the model up and running.

Luckily, Beks has come preparred.  She comes armed with a massive CSV file containing information on 34,300 projects and how they turned out.  It includes each company's name and identification number, application type, industry sector affiliation, government organization classification, funding use case, organization type, active status, income amount classification, special considerations, funding amount requested, and ultimately whether or not the money was considered to be used effectively.

## Results

### Data Preprocessing

* What variable(s) are considered the target(s) for your model?

* What variable(s) are considered to be the features for your model?

* What variable(s) are neither targets nor features, and should be removed from the input data?

### Compiling, Training, and Evaluating the Model

![Original Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/orig_results.png)

#### Optimization Attempt #1

![Optimization Attempt #1: Feature Importance](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt1_feature_importance.png)

![Optimization Attempt #1 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt1_results.png)

#### Optimization Attempt #2

![Optimization Attempt #2: Activation Functions](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt2_activation.png)

![Optimization Attempt #2 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt2_results.png)

#### Optimization Attempt #3

![Optimization Attempt #3: Number of Nodes](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt3_nodes.png)

![Optimization Attempt #3 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt3_results.png)

#### Optimization Attempt #4

![Optimization Attempt #4: Feature Importance](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt4_layer.png)

![Optimization Attempt #4 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt4_results.png)

* How many neurons, layers, and activation functions did you select for your neural network model, and why?

* Were you able to achieve the target model performance?

* What steps did you take to try and increase model performance?

## Summary

Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.