--------------------------------------------------------------------------------------------------------------------------
    Machine Learning

--------------------------------------------------------------------------------------------------------------------------

    Example where Machine learning is used

    a. Fraud Detection

    Q#1 - Is the user making a valid transaction    : Boolean Response [Yes / No]
    Q#2 - What is the amount of the transaction
    Q#3 - Where is the transaction being carried out from?
    Q#4 - Does the user normally carry out transactions from this location?
    Q#5 - To what is the transaction being made out to ?
    Q#6 - Is this type of transaction normally carried out by the user ?

    b. Image Detection

    Providing the AI solution with an Image and evaluate the solution(s) ability to 'recognize objects'

    c. Anomaly Detection

    In the field to medicine, trying to determine if a patient is going to develop a heart disease in the future based on 
    medical history

--------------------------------------------------------------------------------------------------------------------------
    Machine Learning Model

--------------------------------------------------------------------------------------------------------------------------
    
    ![GitHub Image](/Azure/Assets/Machine-Learning/Machine-Learning-Flow.JPG)

    Step#1 - You feed existing / historical data [Which is labelled and has outcomes] into a Machine Learning Algorithm
    Step#2 - The Machine Learning Algorithm tries to find patterns in the data Set
    Step#3 - Machine learning model algorithm will create a model that can predict an outcome
    Step#4 - The outcome you wish to determine is called the 'Label'
    Step#5 - Test the ML model, to evaluate its accuracy, since end of the day its a prediction

    Key Considerations:
    a. Data should be relevant to the problem being solved.
    b. Their should be enough data points to help develop the model
    c. Data should be free of errors
    d. The data provide should have features to be evaluated, and only required cleaned & structured dataset to be used
    e. The data used to train & test the model should following the 70% to 30% ratio

--------------------------------------------------------------------------------------------------------------------------
    Machine Learning Model Types

--------------------------------------------------------------------------------------------------------------------------

    Anomaly Detection   :  Finds unusual occurrences.
    Classification      :   Classifies images or predicts between several categories.
    Clustering (including K-Means Clustering)   :   Discovers structures.
    Regression          :   Predicts values

--------------------------------------------------------------------------------------------------------------------------
    Machine Learning Classifications : Used to devide or classify the data

--------------------------------------------------------------------------------------------------------------------------    

    a.  Two-Class / Binary-Classification   
        :   This classification results in Binary labels  [Yes / No]
            Mathematical Formula : y = f(x)
            Example : y is the salary, x is the age and 'f' is the model you are trying to create

    b.  Multi-Class / Multi-Classification    
        :   This classifiation results in a multi label
            Example: Based on the historical data for a passenger, which ticket class the customer would most probably buy.

--------------------------------------------------------------------------------------------------------------------------
    Machine Learning Algorithms

--------------------------------------------------------------------------------------------------------------------------    
    Types of ML Algorithms
    
    a. Linear based Algorithms

    b. Regression based Algorithms
        - Predict the number of Web Orders for next few days [Forecasting], based on last 4 weeks of data

    c. Anomaly Detection Algorithms
        - Identify data points that fall outside the defined parameters for what is defined as normal
    
    d. Time Series Algorithms
        - Identify how values changes over time, then you can predict the value for the future [e.g Hotel booking prices]
    
    e. Clustering Algorithms
        - Here Similarity of data points are taken into account [What kind of food do customers like to order]
    
--------------------------------------------------------------------------------------------------------------------------
    Machine Learning Techniques

--------------------------------------------------------------------------------------------------------------------------   
    Types of ML Techniques

    a. Supervised Learning  :   
        In this technique, the algoithms make predictions based on a set of labeled examples that you provide. This 
        technique is useful when you know, what the outcome should look like.
        You use supervised learning where you already have existing data that contains both the features and the label.

        Note: Regression & Classification Models are examples of Supervised Learning

        Example: You provide a dataset that includes city populations by the year for the past 100 years, and you want to 
        know what the population of a specific city will be, four years from now. The outcome uses labels that are already 
        exist in the data set: 
            Population, City & Year

    b. Un-Supervised Learning : 
        In this technique, the data points aren't labeled, the algorithm labels them for you by organizing the data or 
        describing its structure. This technique is useful, when you don't know what the outcome should look like.
        You use unsupervised learning where you are trying to discover something about your data that you do not already 
        know.

        Note: Clustering is an example of Un-Supervised Learning

        Example: You provide customer data, and want yo create segments of customer who like similar products. The data you 
        provided isn't labeled and the labels in the outcomes are generated based on the similarities that were discovered 
        between data points


    c. Reinforcement Learning : 
        This technique uses algorithms that learn from outcomes and decides which action to take next. After each action, 
        the algorithm receives feedback that helps it to determine where the choice it made was correct, neutral or 
        incorrect. Its a good technique to use for automated systems that have to make a lot o small decisions without 
        human guidance. Reinforcement learning is used, for example, in building a model to play chess and is commonly 
        used in robotics.

        Example : You are designing an autonomous car, and you want to ensure that it's obeying the law and keeping people 
        safe. As the car gains experience and a history of reinforcement, it learns how to stay in its lane, go the speed 
        limit and brake for pedestrians
--------------------------------------------------------------------------------------------------------------------------
    Machine Learning Pipeline Flow

-------------------------------------------------------------------------------------------------------------------------- 
    Feed the data --> 
        Clean the data [Deal with missing values] --> 
            Split the data (70% [Train] /30% [Test]) --> 
                Train your model --> Score the model --> 
                    Evaluate the model
--------------------------------------------------------------------------------------------------------------------------
    Describe Classification Model

-------------------------------------------------------------------------------------------------------------------------- 
    Classification machine learning models are used to predict mutually exclusive categories, or classes. Classification 
    involves learning using labels to classify data and is an example of supervised machine learning.
    Classification is used to make predictions where we do not require continuous values but need distinct categories, 
    such as Pass or Fail

    ![GitHub Image](/Azure/Assets/Machine-Learning/Dataset-Classification.JPG)

    Using the above data, we could build and train a classification model to use the hours studied to predict whether a 
    student passes the exam or not. Using this data, a simple two-class model will likely predict that studying for less 
    than 18 hours will fail and 18 hours or more will pass.

    In a classification model, we are interested where the model gets it wrong. For student L, the model predicts a pass, 
    but the actual result was a fail—this is a false positive. 
    Student E actually passed, but the model predicted that the student will fail—this is a false negative

--------------------------------------------------------------------------------------------------------------------------
    Outputs of Classification Model

--------------------------------------------------------------------------------------------------------------------------   
    Accuracy    : This measures the goodness of a classfication model
    Precision   : This measues the proportion of the true results over the positive results
    Recall      : This is the fraction of the total amount of relevant cases that were actually retrieved
    F1 Score    : This is weighted average of the precision vs  the recall. The ideal F1 score is 1
    AUC         : This is the area under the curve that shows the true positives and the false positives

--------------------------------------------------------------------------------------------------------------------------
    Outputs of Regression Model

--------------------------------------------------------------------------------------------------------------------------
    Mean Absolute Error             : This s used to measure how close the predictions are to the outcomes, its ideal to 
                                      have a low score
    Root Mean Squared Error         : This helps to summarize the error in the model
    Relative absolute Error         : This is the absolute difference between the expected and the actual values
    Relative square Error           : This is used to normalize the total squated error of the actual values
    Coefficient of determination    : This is used to represent the predictive power of the model between 0 and 1

--------------------------------------------------------------------------------------------------------------------------
    Describe Clustering Model

-------------------------------------------------------------------------------------------------------------------------- 
    Clustering machine models learn by discovering similarities, patterns, and relationships in the data without the data 
    being labeled. Clustering is an example of unsupervised learning where the model attempts to discover structure from 
    the data or tell us something about the data that we didn’t know.

    Clustering analyzes unlabeled data to find similarities in data points and groups them together into clusters. A 
    clustering algorithm could be used, for example, to segment customers into multiple groups based on similarities in 
    the customer’s details and history.

    A clustering model predicts mutually exclusive categories, or classes. K-means clustering is a common clustering model 
    where K is the number of distinct clusters you want the model to group the data by. The way clustering works is to 
    calculate the distance between the data point and the center of the cluster and then to minimize the distance of 
    each data point to the center of its cluster.

    A common example of a clustering model is the recommender model.
    for a company that wants to provide recommendations to its users by generating personalized targeted recommendations. 
    A recommender model looks for similarities between customers. For example, a video streaming service knows which movies 
    customers watch and can group customers by the types of movies they watch. A customer can then be shown other movies 
    watched by other customers which are similar to them based on their viewing history.

--------------------------------------------------------------------------------------------------------------------------
    Identify Labels

-------------------------------------------------------------------------------------------------------------------------- 
    If you are using supervised training—for example, a regression or a classification model—then you need to select the 
    label(s) from your dataset.

    Labels are the columns in the dataset that the model predicts.

    For a regression model, the Score column is the label you would choose, as this is a numeric value. Regression models 
    are used to predict a range of values.
    For a classification model, the Pass column is the label you would choose as this column has distinct values. 
    Classification models are used to predict from a list of distinct categories.

--------------------------------------------------------------------------------------------------------------------------
    Feature selection

--------------------------------------------------------------------------------------------------------------------------
    A feature is a column in your dataset. You use features to train the model to predict the outcome. Features are used 
    to train the model to fit the label.
    After training the model, you can supply new data containing the same features, and the model will predict the value 
    for the column you have selected as the label.

    Feature selection is the process of selecting a subset of relevant features to use when building and training the model. 
    Feature selection restricts the data to the most valuable inputs, reducing noise and improving training performance.

    - Increase the model’ s ability to classify data accurately by eliminating features that are irrelevant, redundant, 
    or highly correlated.
    - Increase the ef ficiency of the model training process.

    If you can reduce the number of features without losing the variance and patterns in the data, the time taken to
    train the model is minimized. For instance, you can exclude features that are highly correlated with each other as 
    this just adds redundancy to the processing. 
    Azure Machine Learning has a module for Filter-Based Feature Selection to assist in identifying features that are 
    irrelevant. Azure Machine Learning applies statistical analysis to determine which columns are more predictive than the 
    others and ranks the results. You can exclude the columns that have a poor predictive effect.

--------------------------------------------------------------------------------------------------------------------------
    Feature engineering

--------------------------------------------------------------------------------------------------------------------------    
    Feature engineering is the process of creating new features from raw data to increase the predictive power of the 
    machine learning model. Engineered features capture additional information that is not available in the original 
    feature set.

    Examples of feature engineering are as follows:

    - Aggregating data
    - Calculating a moving average
    - Calculating the difference over time
    - Converting text into a numeric value
    - Grouping data

    Models train better with numeric data rather than text strings. In some circumstances, data that visually appears to be 
    numeric may be held as text strings, and you need to parse and convert the data type into a numeric value.

--------------------------------------------------------------------------------------------------------------------------
    Bias

--------------------------------------------------------------------------------------------------------------------------      
    Bias in machine learning is the impact of erroneous assumptions that our model makes about our data. Machine learning 
    models depend on the quality, objectivity, and quantity of data used to train it. 
    Faulty, incomplete, or prejudicial data can result in a poorly performing model.

    we introduced the Fairness principle and how an AI model should be concerned with how data influences the model’s 
    prediction to help eliminate bias. You should therefore be conscious of the provenance of the data you are using in 
    your model. You should evaluate the bias that might be introduced by the data you have selected.

    A common issue is that the algorithm is unable to learn the true signal from the data, and instead, noise in the data 
    can overly influence the model.

    An example from computer vision is where the army attempted to build a model that was able to find enemy tanks in 
    photographs of landscapes. The model was built with many different photographs with and without tanks in them. The model 
    performed well in testing and evaluation, but when deployed, the model was unable to find tanks. Eventually, it was 
    realized that all pictures of tanks were taken on cloudy days, and all pictures without tanks were taken on sunny days. 
    They had built a model that identifies whether a photograph was of a sunny or a cloudy day; the noise of the sunlight 
    biased the model. The problem of bias was resolved by adding additional photographs into the dataset with varying
     degrees of cloud cover.

--------------------------------------------------------------------------------------------------------------------------
    Normalization

--------------------------------------------------------------------------------------------------------------------------   
    A common cause of bias in a model is caused by data in numeric features having different ranges of values. Machine 
    learning algorithms tend to be influenced by the size of values, so if one feature ranges in values between 1 and 10 
    and another feature between 1 and 100, the latter column will bias the model toward that feature.

    You mitigate possible bias by normalizing the numeric features, so they are on the same numeric scale.

--------------------------------------------------------------------------------------------------------------------------
    Evaluation

--------------------------------------------------------------------------------------------------------------------------   

    Evaluation  is the process of measuring the accuracy of a trained model. A set of metrics is used to measure how 
    accurate the predictions of the model are. Evaluation is a key part of the building of your model.
    Azure Machine Learning generates metrics for each experiment. Y ou can view these metrics to evaluate your model’ s 
    performance 

--------------------------------------------------------------------------------------------------------------------------
    Describe Model Deployment & Management

--------------------------------------------------------------------------------------------------------------------------       
    Azure Machine Learning allows you to create and manage versions of your model and then choose which version of a model 
    to deploy so that applications can use the model to make predictions.
    In machine learning, infer encing  refers to the use of a trained model to make predictions for new unseen data. A 
    machine learning model can be used for:

    - Real-time: For individual or small numbers of data observations. 
    - Batch: For lar ge volumes of data.

    For real-time processing : the model is deployed as a web service that enables applications to request via http.
    If you have used a pipeline to build your model, you can create an inference pipeline that performs the same steps for 
    new data input, not the sample data used in training. You can publish the inference pipeline as a web service. 
    A real-time inference pipeline must have at least one W eb Service Input module and one Web Service Output module. 
    The Web Service Input module is normally the first step in the pipeline.

    In Azure Machine Learning, when you publish a real-time inferencing model, you deploy the model as a web service 
    running in a Docker container . There are three ways you can deploy the container: 
    - Azure Kubernetes Service (AKS) cluster : AKS is Microsoft’ s implementation of Kubernetes and is used to run highly 
    scalable realtime interference as a web service for production. 
    
    - Azure Container Instance (ACI) : ACI is used to run a single Docker container . You can use this to expose your 
    prediction model as a web service for testing and low-volume production scenarios. 
    
    - IoT Edge :  Azure IoT Edge supports the running of containers containing machine learning models on small devices, 
    reducing the need for network traffic and reducing latency . 
    
    You can also use ONNX (Open Neural Network Exchange) to export your model and deploy it on other platforms, such as on 
    a mobile device.

    For batch inference processing : you create a pipeline that includes steps to load the input data, load the model, 
    predict labels, and write the results to a datastore, normally to a file or to a database.

--------------------------------------------------------------------------------------------------------------------------    
    Describe Azure Automated Machine Learning

--------------------------------------------------------------------------------------------------------------------------  

    Azure Automated Machine Learning (AutoML) finds the best algorithm for the dataset. A number of iterations are run to 
    evaluate dif ferent algorithms and features. The results are analyzed and ranked, and an explanation is produced that 
    interprets the best model for the data, parameters, and task.

    Following figure shows the Automated ML process, where data is fed into Automated ML, which then outputs a best-fit 
    trained model.

    ![GitHub Image](/Azure/Assets/Machine-Learning/Automated-ML.JPG)

    Automated ML trades data science skills with compute power and time. A data scientist will evaluate and choose the 
    features, algorithm, and hyperparameters for the model. Automated ML simply tries all combinations of algorithm, 
    features, and parameters and then ranks the results by the chosen metric. Clicking on Automated ML in the left-hand 
    navigation pane in the Azure Machine Learning studio lists all previous ML runs and allows you to create a new run. 

    Note: Automated ML only supports supervised learning, as you must specify a label for the model to fit the data to

--------------------------------------------------------------------------------------------------------------------------    
Describe Azure Machine Learning Designer

--------------------------------------------------------------------------------------------------------------------------    

    Azure Machine Learning designer is a visual drag-and-drop tool for creating machine learning pipelines. Azure Machine 
    Learning designer simplifies the process of building, testing, and deploying models. Azure Machine Learning designer 
    contains modules for data preparation, training, data visualization, and model evaluation.
