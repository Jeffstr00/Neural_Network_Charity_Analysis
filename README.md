# Neural_Network_Charity_Analysis

## Overview

Beks is a data scientist and programmer at AlpabetSoup, which is a philanthropic foundation dedicated toward helping organizations that protect the environment, improve people's well-being, and unify the world.  Over the past two decades, they have raised and donated over $20 billion!  With these massive amount of money being used to hopefully improve the world, they want to ensure that the money is actually working towards accomplishing that goal (as opposed to being wasted or used inefficiently, going towards corruption instead of actual philanthropy, or simply falling through the cracks).

As Beks is in charge of data collection and analysis of the entire organization, her job is to analyze the impact of each donation and vet potential recipients in an attempt to ensure that the foundation's money is being used effectively.  As a result, the organization's president has asked her to help determine which organizations are worth giving to and which are simply too risky.  He wants her to create a mathematical, data-driven solution which can accomplish that task accurately.  Since the problem is so complex, she decides to go with a deep learning neural network which will accept all types of input data and produce a clear result.  Due to both the scale and the importance of this project, she has asked us for our assistance in getting the model up and running.

Luckily, Beks has come prepared.  She comes armed with a massive CSV file containing information on 34,300 projects and how they turned out.  It includes each company's name and identification number, application type, industry sector affiliation, government organization classification, funding use case, organization type, active status, income amount classification, special considerations, funding amount requested, and ultimately whether or not the money was considered to be used effectively.

## Results

### Data Preprocessing

* What variable(s) are considered the target(s) for your model?
Our target variable falls under the IS_SUCCESSFUL column.  It represents whether or not the project was deemed to be a success, and is what we want to be able to predict the result of.

* What variable(s) are neither targets nor features, and should be removed from the input data?
The first two columns, the EIN classification number and NAME, are neither targets nor features.  As a result, they should not be included in our machine learning model, and we drop them using `application_df = application_df.drop(columns=["EIN","NAME"])`.

* What variable(s) are considered to be the features for your model?

The remaining variables (application type, affiliation, classification, use case, organization, status, income amount, special considerations, and asking amount) are our feature variables.  We will see if we can use them to predict whether the project will ultimately be successful.

### Compiling, Training, and Evaluating the Model

![Original Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/orig_results.png)

Our first attempt at a deep learning model proved to be a solid effort.  We used two hidden layers: the first with 80 hidden nodes and Relu activation function and the second having 30 hidden nodes and another Relu activation.  For the output layer, we used Sigmoid.  We ended up with 73.49% accuracy.  While this is a decent result from a first effort in a situation where accuracy isn't of paramount importance (compared to, for instance, medical situations), it falls a bit short of our 75% goal, so we will look to further optimize our model.

(Note: Since I made several different optimization attempts, and within each of those attempts tried many different iterations, I commented out the code for saving the .H5 and checkpoint files for optimization attempts which didn't provide the best results).

#### Optimization Attempt #1

![Optimization Attempt #1: Feature Importance](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt1_feature_importance.png)

![Optimization Attempt #1 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt1_results.png)

In our first attempt at optimizing the model, we sought to remove variables which don't add much to the predictability.  In order to do this, we established and ran a balanced random forest model.  The provided us with information on how important each feature was:
* ASK_AMT = .4081
* AFFILIATION = .2598
* APPLICATION = .1242
* CLASSIFICATION = .0816
* ORGANIZATION = .0499
* INCOME_AMT = .0483
* USE_CASE .0269
* SPECIAL_CONSIDERATION = .0009
* STATUS = .0001
While Asking Amount provided 40% of the predictability, others provided much less.  Status was almost completely negligible, and Special Consideration wasn't much better.  As a result, we dropped these two columns from our dataset before performing our analysis, thinking that they might be confusing the model without providing any real benefits.  However, this produced virtually identical results to our original attempt, so we need to try something else.

#### Optimization Attempt #2

![Optimization Attempt #2: Activation Functions](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt2_activation.png)

![Optimization Attempt #2 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt2_results.png)

For our second attempt at improving the model, we looked at changing the activation functions.  We tried many different permutations using relu, leaky_relu, tanh, and even sigmoid in the hidden layers.  The best results occured when we used tanh in the first layer and leaky_relu in the second.  However, this only slightly improved our results, bringing it up to 73.61% (from 73.49%).  This was barely an improvement, and still falls under our 75% goal, so we still have work to do.

#### Optimization Attempt #3

![Optimization Attempt #3: Number of Nodes](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt3_nodes.png)

![Optimization Attempt #3 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt3_results.png)

For our third attempt, we tried changing the number of nodes used in each of our hidden layers.  After much trial and error, our best results came when we changed the number of nodes from 80 and 30 down to 40 and 15.  (Note: when we re-ran the model to save our results since it ended up being the winner, the accuracy was down a bit.  However, it did provide us with our highest observed results).  Even with accuracy at 73.60%, we were below our 75% goal, so we had one more trick up our sleeve.

#### Optimization Attempt #4

![Optimization Attempt #4: Feature Importance](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt4_layer.png)

![Optimization Attempt #4 Results](https://github.com/Jeffstr00/Neural_Network_Charity_Analysis/blob/main/Resources/opt4_results.png)

In our last attempt at improving the model, we decided to add a third hidden layer.  Even after trying using many difference choices for both node number and activation functions, we actually saw decreased performance in this attempt.  Accuracy actually fell a bit to 73.54%, so we went back to our previous version for our optimal version, even though it ultimately didn't reach our goal.

* How many neurons, layers, and activation functions did you select for your neural network model, and why?

After a ton of trial and error, for our best results, we went with two hidden layers and an output layer.  The hidden layers featured 40 and 15 nodes and used tanh and leaky_relu activation functions respectively (sigmoid was used for the output layer).

* Were you able to achieve the target model performance?

No.  Our goal was 75%, and the best results we achieved were 73.61%, which was barely an improvement over our first attempt which saw 73.49% accuracy.  To be honest, this was absolutely incredibly frustrating.

* What steps did you take to try and increase model performance?

To improve performance, we tried removing variables which proved to not be useful in helping with the predictions, changing up the activation functions, altering the number of nodes, and even adding hidden layers to the model.  In our experience, only changing up the activation functions and changing the number of nodes provided any benefit.  Even then, the gains were quite meager.

## Summary

In all, this model seemed to provide lukewarm results.  73.6% accuracy might be considered pretty good in some cases.  Since this is not a case where accuracy is absolutely critical (like diagnosing deadly diseases, for instance), that might even be the case here.  However, we ultimately fell short of our goal of 75% accuracy.  As a result, unless we could find a way to improve the model, we might need to look to other models.

While deep learning models can be great for working with huge amounts of data, they aren't always the best choice.  Since we didn't achieve our goal, we might need to look at other methods such as logistical regression, balanced random forest, or easy ensemble classifier.  Even though it isn't an extreme amount, since the amounts of successful and unsuccessful programs isn't balanced, using these bias reduction techniques could possibly provide more accurate results in this instance.