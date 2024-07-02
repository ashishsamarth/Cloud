-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Machine Learning

-----------------------------------------------------------------------------------------------------------------------------------------------------------

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

    In the field to medicine, trying to determine if a patient is going to develop a heart disease in the future based on medical history

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Machine Learning Model

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
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


-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Machine Learning Classifications

-----------------------------------------------------------------------------------------------------------------------------------------------------------    

    a.  Two-Class / Binary-Classification   :   This classification results in Binary labels  [Yes / No]
                                    Mathematical Formula : y = f(x)
                                    Example : y is the salary, x is the age and 'f' is the model you are trying to create

    b.  Multi-Class / Multi-Classification    :   This classifiation results in a multi label
                                    Example: Based on the historical data for a passenger, which ticket class the customer would most probably buy.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Machine Learning Algorithms

-----------------------------------------------------------------------------------------------------------------------------------------------------------    
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
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Machine Learning Techniques

-----------------------------------------------------------------------------------------------------------------------------------------------------------   
    Types of ML Techniques

    a. Supervised Learning  :   In this technique, the algoithms make predictions based on a set of labeled examples that you provide. This technique is useful
                                when you know, what the outcome should look like

                                Example: You provide a dataset that includes city populations by the year for the past 100 years, and you want to know what the population
                                of a specific city will be, four years from now. The outcome uses labels that are already exist in the data set: Population, City & Year
                                
    b. Un-Supervised Learning