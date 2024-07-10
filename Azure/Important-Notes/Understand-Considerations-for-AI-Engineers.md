--------------------------------------------------------------------------------------------------------------------------
Understand considerations for AI Engineers
--------------------------------------------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------------------------------------------
What is Model training and inferencing
--------------------------------------------------------------------------------------------------------------------------
Many AI systems rely on predictive models that must be trained using sample data. The training process analyzes the data 
and determines relationships between the features in the data (the data values that will generally be present in new 
observations) and the label (the value that the model is being trained to predict).

After the model has been trained, you can submit new data that includes known feature values and have the model predict 
the most likely label. Using the model to make predictions is referred to as inferencing.

Many of the services and frameworks that software engineers can use to build AI-enabled solutions require a development 
process that involves training a model from existing data before it can be used to inference new values in an application.

--------------------------------------------------------------------------------------------------------------------------
What is Probability and confidence scores
--------------------------------------------------------------------------------------------------------------------------
A well-trained machine learning model can be accurate, but no predictive model is infallible. The predictions made by 
machine learning models are based on probability, and while software engineers don't require a deep mathematical 
understanding of probability theory, it's important to understand that predictions reflect statistical likelihood, not 
absolute truth. In most cases, predictions have an associated confidence score that reflects the probability on which the 
prediction is being made. Software developers should make use of confidence score values to evaluate predictions and apply 
appropriate thresholds to optimize application reliability and mitigate the risk of predictions that may be made based on 
marginal probabilities.

--------------------------------------------------------------------------------------------------------------------------