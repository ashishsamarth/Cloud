--------------------------------------------------------------------------------------------------------------------------
Q-001: Which of the following workload types does the following belong to?
"Identify fraudulent cases when it comes to credit card usage"
--------------------------------------------------------------------------------------------------------------------------
a. Computer Vision
b. Natural Language Processing
c. Anomaly Detection

Answer : c. Anomaly Detection
	
--------------------------------------------------------------------------------------------------------------------------
Q-002: Which of the following workload types does the following belong to?
"Find out if the image contains a person"
--------------------------------------------------------------------------------------------------------------------------
a. Computer Vision
b. Natural Language Processing
c. Anomaly Detection

Answer : a. Computer Vision
	
--------------------------------------------------------------------------------------------------------------------------
Q-003: Which of the following is not a principle when it comes to responsible AI?
--------------------------------------------------------------------------------------------------------------------------
a. Reliability
b. Fairness
c. Detection

Answer : c. Detection
	
--------------------------------------------------------------------------------------------------------------------------
Q-004: You are developing a machine learning model. You need to follow the principles of responsible AI. You have to 
ensure that dataset fed into the model does not discriminate on the basis of gender. Which of the following principle needs 
to be adhered here?
--------------------------------------------------------------------------------------------------------------------------
a. Privacy & Security
b. Reliability & Safety
c. Fairness
d. Inclusiveness

Answer : c. Fairness

--------------------------------------------------------------------------------------------------------------------------
Q-005: You are developing a machine learning model. You need to follow the principles of responsible AI. You discover the 
dataset that is being used to train the model has some missing values. Which of the following principle being broken when 
using this data set?
--------------------------------------------------------------------------------------------------------------------------
a. Privacy & Security
b. Reliability & Safety
c. Fairness
d. Inclusiveness

Answer : b. Reliability & Safety
	
--------------------------------------------------------------------------------------------------------------------------    
Q-006: What is confusion matrix?
--------------------------------------------------------------------------------------------------------------------------
Confusion matrix indicates the difference between what the Machine Learning Model actually predicted vs what it was 
supposed to predict. For a binary classification is looks like the following
    
    -----------------------------------------
    True Positives      |   False Positive
    -----------------------------------------
    False Negatives     |   True Negatives
    -----------------------------------------

--------------------------------------------------------------------------------------------------------------------------    
Q-007: What is Accuracy in results?
--------------------------------------------------------------------------------------------------------------------------
Accuracy teslls us how often the classifier is right in predicting the results.
In terms of mathematical formulat it looks like the following

(True Positives + True Negatives) / (True Positives + True Negatives + False Positives + False Negatives)

--------------------------------------------------------------------------------------------------------------------------
Q-008: What is Precision in results?
--------------------------------------------------------------------------------------------------------------------------
Precision tells us to what extent does the model accurately predict the results
In terms of mathematical formulat it looks like the following

(True Positives) / (True Positives + False Positives)

--------------------------------------------------------------------------------------------------------------------------
Q-009: What are Metrics for Regression Models?
--------------------------------------------------------------------------------------------------------------------------
Predictive modeling is the problem of developing a model using historical data to make a prediction on new data where we 
do not have the answer.
Predictive modeling can be described as the mathematical problem of approximating a mapping function (f) from input 
variables (X) to output variables (y). This is called the problem of function approximation.
The job of the modeling algorithm is to find the best mapping function we can given the time and resources available.

Mean Absolute Error (MAE) : It is the average of the absolute differences between the actual value and the model’s 
predicted value.

--------------------------------------------------------------------------------------------------------------------------
Q-010: What is Feature Engineering?
--------------------------------------------------------------------------------------------------------------------------
This process attempts to create additional relevant features from the existing raw features in the data, and to increase 
predictive power to the learning algorithm.

Example : Split the data horizontally to create additional columns / features to add more calrity for the machine 
learning algorithm. Follwed by selecting (also called as feature selection) only the necesary columns and reduce the 
noise for the ML model

--------------------------------------------------------------------------------------------------------------------------
Q-011: Your team needs to use Machine Learning to forecast the house prices for the coming year based on historical data. Would 
you use a classification algorithm for this requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer : b. No

--------------------------------------------------------------------------------------------------------------------------    
Q-012: Microsoft has infused the capability in some of its products to detect suspicious sign-in attempts. Here is 
Microsoft probably making use of Anomaly detection algorithms to implement this feature?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer : a. Yes
	
-------------------------------------------------------------------------------------------------------------------------- 
Q-013: Your team needs to use Machine Learning to train a model based on a classification algorithm. They have a finalized 
dataset that contains 3000 rows of information. They are planning on using the entire dataset to train the model. Can they 
use the same dataset to evaluate the model?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer : b. No

-------------------------------------------------------------------------------------------------------------------------- 
Q-014: A team has completed the training and evaluation of a model
The team is happy with the accuracy result of 0.872 and is using this as the final measure to decide that this model is the 
right one to choose. Is this the correct approach when evaluating the results?

Accuracy    : 0.872
Precision   : 0.763
Recall      : 0.666
F1 Score    : 0.711
AUC         : 0.927
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer : b. No [All results factors should be considered before selection of the model]

-------------------------------------------------------------------------------------------------------------------------- 
Q-015: Your team is planning on building a model in Azure Machine Learning by using a regression algorithm. They currently 
have a dataset that is not labelled. Can they use this to train the model?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer : b. No [To train the model, you need to have a labelled dataset]

-------------------------------------------------------------------------------------------------------------------------- 
Q-016: Which of the following in Azure Machine Learning allows you to easily drag and drop components and data assets to 
build and train models?
--------------------------------------------------------------------------------------------------------------------------
a. Notebooks
b. Automated ML
c. Designer
d. Environments

Answer : c. Designer

--------------------------------------------------------------------------------------------------------------------------
Q-017: Which of the following type of algorithm falls into the unsupervised mode of Machine Learning?
--------------------------------------------------------------------------------------------------------------------------
a. Regression
b. Classification
c. Clustering

Answer: c. Clustering [Clustering algorithms falls into the category of unsupervised Machine Learning.]

--------------------------------------------------------------------------------------------------------------------------    
Q-018: Which of the following feature in the Azure Face service can be used to answer the question

“Do these two faces belong to the same person”.
--------------------------------------------------------------------------------------------------------------------------
a. Identification
b. Verification
c. Comparision

Answer: b. Verification

--------------------------------------------------------------------------------------------------------------------------
Q-019: You are planning on creating a Custom Vision project based on the Classification project type. Can you choose 
Multilabel as the classification type?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

--------------------------------------------------------------------------------------------------------------------------    
Q-020: You are planning on creating a Custom Vision project based on the Object Detection project type. Can you choose 
Multilabel as the classification type?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: b. No

--------------------------------------------------------------------------------------------------------------------------    
Q-021: Can you use the Form Recognizer service to extract the details from an existing invoice?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

--------------------------------------------------------------------------------------------------------------------------
Q-022: Which of the following service can be used to detect objects in an image?
--------------------------------------------------------------------------------------------------------------------------
a. Form Recognizer
b. Azure AI Vision - Face API
c. Azure AI Vision - Image Analysis

Answer: c. Azure AI Vision - Image Analysis

--------------------------------------------------------------------------------------------------------------------------
Q-023: Which of the following service can be used to extract main topics from a given phrase?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Languauge - Question Answering
b. Azure AI Languauge - Key Phase Extraction
c. Azure AI Languauge - Sentimanet Analysis

Answer: b. Azure AI Languauge - Key Phase Extraction

--------------------------------------------------------------------------------------------------------------------------
Q-024: Which of the following service can be used to what a person thinks about a particular topic?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Languauge - Question Answering
b. Azure AI Languauge - Key Phase Extraction
c. Azure AI Languauge - Sentimanet Analysis

Answer: c. Azure AI Languauge - Sentimanet Analysis

--------------------------------------------------------------------------------------------------------------------------
Q-025: You are planning on using the Azure Speech service. Can you use the Azure Speech Service to enable real-time 
speech-to-speech translation?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

--------------------------------------------------------------------------------------------------------------------------
Q-026: You are planning on using the Azure Translator service. Can you use the service to translate documents?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

--------------------------------------------------------------------------------------------------------------------------
Q-027: You are planning on using the Question Answering solution available in Azure AI Language. Can you import existing 
questions from an Excel sheet?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

--------------------------------------------------------------------------------------------------------------------------
Q-028: Your team needs to develop several systems. One system needs to understand whether reviews are positive or 
negative. Which of the following type of workload does this come under?
--------------------------------------------------------------------------------------------------------------------------
a. Natural Language Processing
b. Computer Vision
c. Conversational AI

Answer: a. Natural Language Processing

Overall explanation :
This is an example of Natural Language processing

For more information on an example of Natural Language processing, one can visit the below URL

https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics

--------------------------------------------------------------------------------------------------------------------------
Q-029: Which of the following module is used in Azure Machine Learning Designer to split a dataset into a training and 
validation data set?
--------------------------------------------------------------------------------------------------------------------------
a. Normalize Data
b. Split Data
c. Join Data

Answer: b. Split Data

Overall Explanation: This can be done with the Split Data module
For more information on the Split Data module, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/split-data

--------------------------------------------------------------------------------------------------------------------------    
Q-030: Your team is planning on using the Azure Machine Learning Designer. Can you drag a dataset onto the designer?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

You can drag and drop datasets and modules onto the canvas.
For more information on the Machine Learning Designer, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer

--------------------------------------------------------------------------------------------------------------------------
Q-031: Your team is planning on using the Azure Machine Learning Designer. Can you drag a component onto the designer?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation :You can drag and drop datasets and components onto the canvas.
For more information on the Machine Learning Designer, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer   
 
--------------------------------------------------------------------------------------------------------------------------
Q-032: Your team is planning on using the Azure Machine Learning Designer. Can you drag a pipeline onto the designer?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: b. No

Overall explanation : You can drag and drop datasets and modules onto the canvas.
For more information on the Machine Learning Designer, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer

--------------------------------------------------------------------------------------------------------------------------
Q-033: Your team is planning on using the Azure AI Vision service. They would use it to analyze a set of images. Which of 
the following feature helps to identify an object and also get the bounding coordinates of the object?
--------------------------------------------------------------------------------------------------------------------------
a. Face detection
b. Object detection
c. Optical character recognizer

Answer: b. Object detection

Overall explanation : You can use the Object detection feature for this requirement
For more information on the Object Detection feature, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/overview-image-analysis?tabs=4-0

--------------------------------------------------------------------------------------------------------------------------
Q-034: Your team is planning on using the Azure AI Vision service. They would use it to analyze a set of images. Which of the 
following feature helps to extract printed and handwritten text from images?
--------------------------------------------------------------------------------------------------------------------------
a. Face detection
b. Object detection
c. Optical character recognizer

Answer: c. Optical character recognizer

Overall explanation : You can use the Optical character recognizer feature for this requirement
For more information on the Optical character recognition feature, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/overview-ocr    

--------------------------------------------------------------------------------------------------------------------------
Q-035: Which of the following are Microsoft principles of responsible AI? Choose 3 answers from the options given below
--------------------------------------------------------------------------------------------------------------------------
a. Privacy and Security
b. Opacity
c. Fairness
d. Transparency
e. Exclusiveness

Answer:  a. Privacy and Security, c. Fairness, d. Transparency

Overall explanation :
The six principles are

1. Fairness
2. Reliability & Safety
3. Privacy & Security
4. Inclusiveness
5. Transparency
6. Accountability

For more information on Responsible AI, one can visit the below URL

https://www.microsoft.com/en-us/ai/responsible-ai

--------------------------------------------------------------------------------------------------------------------------
Q-036: Your team needs to develop several systems. One system needs the capability to determine whether images contain a 
set of objects. Which of the following type of workload does this come under?
--------------------------------------------------------------------------------------------------------------------------
a. Natural Language Processing
b. Computer Vision
c. Conversational AI

Answer: b. Computer Vision

Overall explanation: Here we can use Computer Vision to get a set of objects from an image.
For more information on the Computer Vision service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/overview

--------------------------------------------------------------------------------------------------------------------------
Q-037: Your team needs to develop several systems. One system needs to have an automated chat facility which can answer 
user’s questions. Which of the following type of workload does this come under?
--------------------------------------------------------------------------------------------------------------------------
a. Natural Language Processing
b. Computer Vision
c. Conversational AI

Answer: c. Conversational AI

Overall explanation : This is an example of Conversational AI
For more information on an example of Conversational AI , one can visit the below URL

https://azure.microsoft.com/en-us/services/bot-services/

--------------------------------------------------------------------------------------------------------------------------
Q-038: Your team needs to train a model. Here the requirement is to find out which type of computer models always have 
failures. Which of the following type of Machine Learning algorithm needs to be used here?
--------------------------------------------------------------------------------------------------------------------------
a. Anomaly detection
b. Regression
c. Time Series
d. Classification
e. Clustering

Answer: e. Clustering

Overall explanation : This is an example of a Clustering algorithm
This example is taken from the below documentation link on the different types of machine learning algorithms

https://azure.microsoft.com/en-us/overview/machine-learning-algorithms    

--------------------------------------------------------------------------------------------------------------------------
Q-039: Which of the following is the process of creating new features from raw data?
--------------------------------------------------------------------------------------------------------------------------
a. Feature Engineering
b. Feature Selection

Answer: a. Feature Engineering

Overall explanation : This is called Feature engineering
For more information on Feature Engineering, one can visit the below URL

https://docs.microsoft.com/en-us/azure/architecture/data-science-process/create-features   

--------------------------------------------------------------------------------------------------------------------------
Q-040: Which of the following is the process of selecting a key subset of features?
--------------------------------------------------------------------------------------------------------------------------
a. Feature Engineering
b. Feature Selection

Answer: b. Feature Selection

Overall explanation : This is called Feature selection
For more information on Feature Engineering, one can visit the below URL

https://docs.microsoft.com/en-us/azure/architecture/data-science-process/create-features

--------------------------------------------------------------------------------------------------------------------------
Q-041: Which of the following metrics can be used to evaluate a classification model? Choose 2 answers from the options 
given below
--------------------------------------------------------------------------------------------------------------------------
a. Recall
b. AUC
c. Mean absolute error
d. Root mean squared error

Answer: a. Recall, b. AUC

Overall explanation : You can use the metrics of Recall and AUC to evaluate a classification model
For more information on evaluating models, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/evaluate-model

--------------------------------------------------------------------------------------------------------------------------
Q-042: Which of the following metrics can be used to evaluate a regression model? Choose 2 answers from the options given 
below
--------------------------------------------------------------------------------------------------------------------------
a. Recall
b. AUC
c. Mean absolute error
d. Root mean squared error

Answer: c. Mean absolute error, d. Root mean squared error

Overall explanation : You can use the metrics of Mean absolute error and Root mean squared error to evaluate a 
classification modelFor more information on evaluating models, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/evaluate-model    

--------------------------------------------------------------------------------------------------------------------------
Q-043: Your team has deployed an endpoint within Azure Machine Learning.
![GitHub Image](/Azure/Assets/Q&As/Which-is-an-endpoint.png)
Which of the following would you use to call the endpoint? Choose 2 answers from the options given below
--------------------------------------------------------------------------------------------------------------------------
a. an API endpoint
b. A REST endpoint
c. An Authentication Token
d. An Authentication Key

Answer: b. A REST endpoint, d. An Authentication Key

Overall explanation : You will call the endpoint via the REST endpoint. And you will also make use of the authentication 
key.  

--------------------------------------------------------------------------------------------------------------------------
Q-044: Your team currently has a trained model in Azure Machine Learning. They now want to deploy the model via the use of 
a real-time inference pipeline. Which of the following service is used to deploy the endpoint so that it can consumed by 
users and applications?
--------------------------------------------------------------------------------------------------------------------------
a. Virtual machine scale set
b. Azure Batch
c. Azure Kubernetes
d. Azure Container Groups

Answer: c. Azure Kubernetes

Overall explanation : Azure Kubernetes is used to host the endpoint.

--------------------------------------------------------------------------------------------------------------------------
Q-045: Your team needs to build a machine learning pipeline to train, and a model based on Adult Census Income Binary 
classification data.
![GitHub Image](/Azure/Assets/Q&As/Pipeline-Components.png)
![GitHub Image](/Azure/Assets/Q&As/Pipeline-Components-Question.png)
You need to add the right components to the pipeline. Which of the following would go into Slot 1?
--------------------------------------------------------------------------------------------------------------------------
a. Train Model
b. Split Model
c. Score Model
d. Split Data

Answer: d. Split Data

Overall explanation : Here we first need to split the data.

--------------------------------------------------------------------------------------------------------------------------
Q-046: Your team needs to build a machine learning pipeline to train, and a model based on Adult Census Income Binary 
classification data.
![GitHub Image](/Azure/Assets/Q&As/Pipeline-Components.png)
![GitHub Image](/Azure/Assets/Q&As/Pipeline-Components-Question.png)
You need to add the right components to the pipeline. Which of the following would go into Slot 2?

--------------------------------------------------------------------------------------------------------------------------
a. Train Model
b. Split Model
c. Score Model
d. Split Data

Answer: a. Train Model

Overall explanation : Here we need to train the model.

--------------------------------------------------------------------------------------------------------------------------
Q-047: Your team needs to build a machine learning pipeline to train, and a model based on Adult Census Income Binary 
classification data.
![GitHub Image](/Azure/Assets/Q&As/Pipeline-Components.png)
![GitHub Image](/Azure/Assets/Q&As/Pipeline-Components-Question.png)
You need to add the right components to the pipeline. Which of the following would go into Slot 3?
--------------------------------------------------------------------------------------------------------------------------
a. Train Model
b. Split Model
c. Score Model
d. Split Data

Answer: c. Score Model

Overall explanation : Here we need to score the model.

--------------------------------------------------------------------------------------------------------------------------
Q-048: Your team needs to build an application. The application will be used to read text to users who have reduced 
vision. Which of the following service can be used for this requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Language - Key phrase extraction
b. Azure Bot service
c. Azure AI Speech Service
d. Azure AI Vision - Object detection

Answer: c. Azure AI Speech Service

Overall explanation : You can use the Text-to-Speech service to convert text to human-like synthesized speech.
For more information on the Speech service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/speech-service/overview

--------------------------------------------------------------------------------------------------------------------------
Q-049: Your development is planning on setting up a bot instance with the use of the Azure Bot service. Can the team 
communicate with the bot via Slack?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : There are many ways to communicate with the bot. One of them is via Slack
For more information on connecting via Slack, one can visit the URL

https://docs.microsoft.com/en-us/azure/bot-service/bot-service-channel-connect-slack?view=azure-bot-service-4.0

--------------------------------------------------------------------------------------------------------------------------
Q-050: Which of the following service allows you to host your own knowledge base?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Translator
b. Azure AI Vision Service
c. Azure AI Language Service
d. Azure AI Custom Vision

Answer: c. Azure AI Language Service

Overall explanation : You can use the question and answer feature with the Azure AI Language service
For more information on this service, one can visit the URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/question-answering/overview

--------------------------------------------------------------------------------------------------------------------------    
Q-051: Which of the following are types of content can you import in the question and answer service in Azure AI Language 
service? Choose 2 answers from the options given below
--------------------------------------------------------------------------------------------------------------------------
a. Excel Documents
b. Data Stored in Azure SQL Database
c. TSV Files
d. Files in XML Format

Overall explanation : The QnA Maker service does not support getting data from an Azure SQL database.
For more information on the QnA Maker service data sources, one can visit the URL

https://docs.microsoft.com/en-us/azure/cognitive-services/qnamaker/concepts/data-sources-and-content

--------------------------------------------------------------------------------------------------------------------------
Q-052: Your company is planning on building an ecommerce application. As part of the application, a module will be 
developed which would provide an interactive interface for automatically answering questions asked by the user. 
Which of the following type of module is being developed here as part of the application?
--------------------------------------------------------------------------------------------------------------------------
a. A Forecasting module
b. A Text Analytics Module
c. A conversational AI module

Answer: c. A conversational AI module

Overall explanation : Here the module depicts a conversational AI module which will converse with the user and try to 
answer their questions. 

--------------------------------------------------------------------------------------------------------------------------
Q-053: Your team has just conducted a Machine Learning experiment. The below chart is the result of the experiment
![GitHub Image](/Azure/Assets/Q&As/Machine-Learning-Experiment.jpg)
Which of the following type of model is the chart being used to evaluate?
--------------------------------------------------------------------------------------------------------------------------
a. Classification
b. Regression
c. Clustering

Answer: Regression

Overall explanation : When using charts which show cases the predicted vs true chart, this normally means that you are 
working with Regression-based algorithms.

--------------------------------------------------------------------------------------------------------------------------
Q-054: Your team has just finished using the Computer Vison service. Below are the results
![GitHub Image](/Azure/Assets/Q&As/computer-vision-object-detection.jpg)
Which of the following Computer Vision type was used here?
--------------------------------------------------------------------------------------------------------------------------
a. Object Detection
b. Semantic Segmentation
c. Optical Character Recognition
d. Image classification

Answer: a. Object Detection

Overall explanation : Here Computer Vision is being used to detect the different objects along with their confidence level.

--------------------------------------------------------------------------------------------------------------------------
Q-055: Which of the following is an example of conversational AI?
--------------------------------------------------------------------------------------------------------------------------
a. IoT devices sending telemetry data to Azure.
b. An automated automotive line used in car manufacturing
c. An ecommerce web site that helps to answer a user’s questions via the use of a knowledgebase

Answer:  c. An ecommerce web site that helps to answer a user’s questions via the use of a knowledgebase

Overall explanation : The ability to answer the user’s question based on an automated system via the use of a knowledge 
base is an example of conversational AI.    

--------------------------------------------------------------------------------------------------------------------------
Q-056: Your team is planning on making use of the Azure AI Language service. Can you use the service to extract phrases 
from text?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : You can do this with the Key phrase extraction feature of the Azure AI Language service.
For more information on the service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/key-phrase-extraction/overview

--------------------------------------------------------------------------------------------------------------------------
Q-057: Your team is planning on making use of the Azure AI Language service. Can you use the service to detect text 
language?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : You can do this with the Language detection feature of the Azure AI Language service.
For more information on the service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/language-detection/overview    

--------------------------------------------------------------------------------------------------------------------------
Q-058: Your development is planning on setting up a bot instance with the use of the Azure Bot service. Can the team 
communicate with the bot via Microsoft teams?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : There are many ways to communicate with the bot. One of them is via Microsoft Teams
For more information on connecting via Microsoft Teams, one can visit the URL

https://docs.microsoft.com/en-us/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0

--------------------------------------------------------------------------------------------------------------------------
Q-059: Your team is developing an application. Users would upload videos via the application. You have to ensure that closed 
caption is generated for the videos. Which of the following service can be used for this requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Language - Key phrase extraction
b. Azure Bot service
c. Azure AI Speech Service
d. Azure AI Vision - Object detection

Answer: c. Azure AI Speech Service

Overall explanation : You can use the Speech-to-Text service to transcribe the audio from the video files into text.
For more information on the Speech service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/speech-service/overview

--------------------------------------------------------------------------------------------------------------------------
Q-060: Your team is developing an application. It’s an ecommerce application. Part of the application allows users to 
raise support issues via the application. You need to add built-in intelligence to the support system that includes the 
following
1) Being able to look at key phrases in the text that the user has added when raising the support issue.
2) Understand how urgent the issue is based on the text that the user has added when raising the support issue.
Which of the following feature of the Azure AI Language service can you use for the requirement?
“Being able to look at key phrases in the text that the user has added when raising the support issue.”
--------------------------------------------------------------------------------------------------------------------------
a. Sentiment Analysis
b. Key phrase extraction
c. Language detection
d. Named Entity recognition

Answer: b. Key phrase extraction

Overall explanation : For extracting key phrases, you can use the Key phrase extraction feature in the Azure AI Language 
service For more information on the service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/key-phrase-extraction/overview

--------------------------------------------------------------------------------------------------------------------------
Q-061: Your team is developing an application. It’s an ecommerce application. Part of the application allows users to raise 
support issues via the application. You need to add built-in intelligence to the support system that includes the following
1) Being able to look at key phrases in the text that the user has added when raising the support issue.
2) Understand how urgent the issue is based on the text that the user has added when raising the support issue.
Which of the following feature of the Azure AI Language service can you use for the requirement?
“Understand how urgent the issue is based on the text that the user has added when raising the support issue.”
--------------------------------------------------------------------------------------------------------------------------
a. Sentiment Analysis
b. Key phrase extraction
c. Language detection
d. Named Entity recognition

Answer: a. Sentiment Analysis

Overall explanation : You can use Sentiment Analysis to understand the user’s sentiment based on the text added when the 
support issue was raised.For more information on the service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/sentiment-opinion-mining/overview?tabs=prebuilt   
--------------------------------------------------------------------------------------------------------------------------
Q-062: Your team is planning on using the Face service. Which of the following feature of the face service can be used for 
the below requirement?
“Match a face to set of faces”
--------------------------------------------------------------------------------------------------------------------------
a. Verification
b. Find Similar
c. Identification
d. Group

Answer: c. Identification

Overall explanation : You can use the Identification feature for this requirement
For more information on the Face service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/face/overview    

--------------------------------------------------------------------------------------------------------------------------
Q-063: Your team is planning on using the Face service. Which of the following feature of the face service can be used for 
the below requirement?
“Do these two faces belong to the same person”
--------------------------------------------------------------------------------------------------------------------------
a. Verification
b. Find Similar
c. Identification
d. Group

Answer: a. Verification

Overall explanation : You can use the Verification feature for this requirement
For more information on the Face service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/face/overview    
--------------------------------------------------------------------------------------------------------------------------
Q-064: Your team is planning on using the Face service. Which of the following feature of the face service can be used for 
the below requirement?
“Do a matching between a target face and a set of candidate faces”
--------------------------------------------------------------------------------------------------------------------------
a. Verification
b. Find Similar
c. Identification
d. Group

Answer: b. Find Similar

Overall explanation : You can use the Find Similar feature for this requirement
For more information on the Face service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/face/overview

--------------------------------------------------------------------------------------------------------------------------
Q-065: Your team is planning on using the AutoML solution in Azure Machine Learning. Can you use the Python language in 
Automated Machine Learning?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : The Python SDK is available with Automated Machine Learning
For more information on Automated Machine Learning, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml

--------------------------------------------------------------------------------------------------------------------------
Q-066: Your team is planning on using the AutoML solution in Azure Machine Learning. Do you need to have prior coding 
experience to work with AutoML?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: b. No

Overall explanation :
There is also an experience of AutoML for users who don’t have any prior coding experience.
For more information on Automated Machine Learning, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml

--------------------------------------------------------------------------------------------------------------------------
Q-067: Your team needs to train a model. Here the requirement is to find out what would be the cost of a three-bedroom 
house in the coming year. Which of the following type of Machine Learning algorithm needs to be used here?
--------------------------------------------------------------------------------------------------------------------------
a. Anomaly Detection
b. Regression
c. Time Series
d. Classification
e. Clustering

Answer: Regression

Overall explanation : This is an example of a Regression algorithm
This example is taken from the below documentation link on the different types of machine learning algorithms

https://azure.microsoft.com/en-us/overview/machine-learning-algorithms    

--------------------------------------------------------------------------------------------------------------------------
Q-068: Your team is planning on making use of the Azure AI Language - Question and answer service. They want to populate 
the knowledge base. Can they use the service to extract question-and-answer pairs from an Excel-based file?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, you can populate the knowledge-base via this method
For more information on the import and export process one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/question-answering/how-to/export-import-refresh

--------------------------------------------------------------------------------------------------------------------------
Q-069: A company has an ecommerce website. Currently there have dedicated support staff who help in answering user 
queries. They want to reduce the number of calls being attended by the support staff. They want to use an automated system 
to help answer some of the user’s queries. Which of the following services can help achieve this?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Vision - Object Detection and Face API
b. Azure AI Language - Question and answer and Azure Bot service
c. Azure AI Translator

Answer: b. Azure AI Language - Question and answer and Azure Bot service

Overall explanation: You can use the combination of the Azure Bot and Azure AI Language - Question and answer service for 
this requirement. The Bot service can make use of in-built knowledge based in the Azure AI Language - Question and answer 
service to answer user’s queries.    

--------------------------------------------------------------------------------------------------------------------------
Q-070: Your team is planning on using the Custom Vision service. They are going to build an object detector. Do you need 
to specify a domain when building the object detector?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, this is required when building an object detector with the Custom Vision service
For more information on the Custom Vision Service – Object detector, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/get-started-build-detector

--------------------------------------------------------------------------------------------------------------------------
Q-071: Your team is planning on using the Custom Vision service. They are going to build a classifier. Do you need to 
choose the Classification Type as either Multilabel or Multiclass when building the classifier?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, this is required when building a classifier with the Custom Vision service
For more information on the Custom Vision Service - Classifier, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier

--------------------------------------------------------------------------------------------------------------------------
Q-072: Your team is planning on using the Azure AI Document Intelligence service. Which of the following can be done with 
this service? Choose 2 answers from the options given below
--------------------------------------------------------------------------------------------------------------------------
a. Recognize the InvoiceID
b. Recognize the Customer’s Photo
c. Recognize the CustomerId
d. Translate the VendorAddress to a different language

Overall explanation: You can use the Azure AI Document Intelligence service to recognize key elements from an invoice , 
receipt etc. You can’t use it to recognize images or to translate languages.

For more information on the service, one can visit the below URL
https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/overview?view=doc-intel-3.0.0

--------------------------------------------------------------------------------------------------------------------------
Q-073: Your team is planning on using the Face API. Can the Face API also detect a person even if they are wearing 
glasses?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: One of the attributes that can be returned based on the Face API is whether the person is wearing 
glasses or not.

--------------------------------------------------------------------------------------------------------------------------
Q-074: Your team is planning on using the Face API. Can you use the Face API to group faces together based on similarity?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: You can do this with the help of the Group faces feature in the Face API
For more information on the Face service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/face/overview

--------------------------------------------------------------------------------------------------------------------------
Q-075: Your company needs to process large amounts of documents. Can you make use of the Azure AI Language service to 
detect the text language within the document?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: You can use the Language detection feature for this requirement.

For more information on this service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/language-detection/overview

--------------------------------------------------------------------------------------------------------------------------
Q-076: Your company needs to process large amounts of documents. From the document text, key elements such as people 
names , locations and dates need to be extracted.
Which of the following feature of the Azure AI Language service can you use for the requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Sentiment Analysis
b. Key phrase extraction
c. Language detection
d. Named Entity recognition 

Answer: d. Named Entity recognition

Overall explanation: You can use the Named Entity recognition to get all of these elements.
For more information on this service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/named-entity-recognition/overview

--------------------------------------------------------------------------------------------------------------------------
Q-077: Q: Your company has just launched a new ecommerce website where users can buy various products. Users are allowed 
to leave a review for each purchase. Your team needs to have an automated system to understand whether the user has a left 
a positive or negative review.
You also need to monitor the reviews for any sort of profanity. Would this analysis of the reviews come under the context 
of natural language processing?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Since you need to monitor the language of the reviews , it does come under the purview of natural 
language processing.    

--------------------------------------------------------------------------------------------------------------------------
Q-078: Your team is planning on making use of the Azure AISpeech service. Can you use the Speech service to translate 
speech?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: You can do this with the Speech Translation service
For more information on the Speech Service , one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/speech-service/speech-translation 

--------------------------------------------------------------------------------------------------------------------------
Q-079: Your team is planning on making use of the Azure AI Speech service. Can you use the Speech service to convert text 
to a human-like synthesized speech?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: You can do this with the Text-to-Speech service
For more information on the Speech Service , one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/speech-service/text-to-speech    

--------------------------------------------------------------------------------------------------------------------------
Q-080: Your team is planning on making use of the Azure AI Speech service. Can you use the Speech service to transcribe 
audio streams into text?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: You can do this with the Speech-to-Text service
For more information on the Speech Service , one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/speech-service/speech-to-text    

--------------------------------------------------------------------------------------------------------------------------
Q-081: Your team is planning on making use of the Azure Bot service. The Bot service is going to be used along with an 
ecommerce web site. Which of the following can be used along with the Bot service to determine the user’s intent?
--------------------------------------------------------------------------------------------------------------------------
a. Azure AI Language - Key phrase extraction
b. Azure AI Language - Sentiment Analysis
c. Azure AI Language - Language detection

Answer: b. Azure AI Language - Sentiment Analysis

Overall explanation: You can use the Azure AI Language - Sentiment Analysis service to determine the user’s intent.
For more information on this service , one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/sentiment-opinion-mining/overview?tabs=prebuilt    
--------------------------------------------------------------------------------------------------------------------------
Q-082: Your team is planning on making use of the Azure Bot service. The Bot service is going to be used along with an 
ecommerce web site. Can you also use Azure Bot service along with the Azure Cognitive service?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, these services can be integrated together.  
  
--------------------------------------------------------------------------------------------------------------------------
Q-083: Your team is planning on making use of the Azure Bot service. The Bot service is going to be used along with an 
ecommerce web site. Can you use the Azure Bot service to converse with customers that visit to the site?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, you can use the Azure Bot service to converse with customers.

--------------------------------------------------------------------------------------------------------------------------
Q-084: Your team is planning on making use of the Azure AI Language - Question and Answer service. They want to populate 
the knowledge base. Can they use the chit-chat feature to add questions and answers to the knowledge-base?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, this can also be done via the Azure AI Language - Question and Answer
For more information on the option to add chit-chat one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/question-answering/how-to/chit-chat

--------------------------------------------------------------------------------------------------------------------------
Q-085: Your company has just launched a new ecommerce website where users can buy various products. Users are allowed to 
leave a review for each purchase. Your team needs to have an automated system to understand whether the user has a left a 
positive or negative review.
Which of the following feature of the Azure AI Language service can you use for the requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Sentiment Analysis
b. Key phrase extraction
c. Language detection
d. Named Entity recognition

Answer: a. Sentiment Analysis

Overall explanation: You can use Sentiment Analysis to determine if a review is positive or not
For more information on the service, one can visit the below URL

https://learn.microsoft.com/en-us/azure/ai-services/language-service/sentiment-opinion-mining/overview?tabs=prebuilt

--------------------------------------------------------------------------------------------------------------------------
Q-086: Your team is planning on using Automated Machine Learning in Azure Machine Learning. Does Automated Machine 
Learning create a number of pipelines in parallel during model training?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Multiple pipelines are created whilst training a model. Each pipeline is used to train a 
different algorithm.

For more information on Automated Azure Machine Learning , one can visit the below URL
https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml
    
--------------------------------------------------------------------------------------------------------------------------
Q-087: Your team is planning on using Automated Machine Learning in Azure Machine Learning. Does Automated Machine 
Learning automatically infer the training data?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: b. No

Overall explanation: No, you still need to specify the training data.
For more information on Automated Azure Machine Learning , one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml
    
--------------------------------------------------------------------------------------------------------------------------
Q-088: Your team is planning on using Automated Machine Learning in Azure Machine Learning. Does Automated Machine 
Learning automatically infer what label needs to be predicted?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: b. No

Overall explanation: No, you still need to specify what label needs to be predicted.
For more information on Automated Azure Machine Learning , one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml    

--------------------------------------------------------------------------------------------------------------------------
Q-089: You have to train a model that predicts the fare for a train journey. You have a dataset that has the information 
for various train journeys. Which of the following can be used in the prediction?
--------------------------------------------------------------------------------------------------------------------------
a. The model of the train
b. The distance of each journey
c. The driver's id

Answer: b. The distance of each journey

Overall explanation: You can use the training journey distance as a feature to predict the fare.  
  
--------------------------------------------------------------------------------------------------------------------------
Q-090: Your team needs to train a model. Here the requirement is to find out which credit card purchases might be 
fraudulent. Which of the following type of Machine Learning algorithm needs to be used here?
--------------------------------------------------------------------------------------------------------------------------
a. Anomaly detection
b. Regression
c. Time Series
d. Classification
e. Clsutering

Answer: a. Anomaly detection

Overall Explanation: This is an example of an Anomaly detection algorithm
This example is taken from the below documentation link on the different types of machine learning algorithms

https://azure.microsoft.com/en-us/overview/machine-learning-algorithms    

--------------------------------------------------------------------------------------------------------------------------
Q-091: Your team needs to train a model. Here the requirement is to find out whether an email is a spam. Which of the 
following type of Machine Learning algorithm needs to be used here?
--------------------------------------------------------------------------------------------------------------------------
a. Anomaly detection
b. Regression
c. Time Series
d. Classification
e. Clsutering

Answer: d. Classification

Overall explanation: This is an example of an Classification algorithm
This example is taken from the below documentation link on the different types of machine learning algorithms

https://azure.microsoft.com/en-us/overview/machine-learning-algorithms 
   
--------------------------------------------------------------------------------------------------------------------------
Q-092: Your team is designing an AI system. Here they want to ensure that they provide customers with the required 
information and controls on what data is collected and how the data is stored. Which of the following Microsoft principle 
of AI does this come under?
--------------------------------------------------------------------------------------------------------------------------
a. Fairness
b. Reliability & Safety
c. Privacy & Security
d. Inclusiveness
e. Transparency
f. Accountability

Answer: c. Privacy & Security

Overall explanation: This comes under the principle of Privacy & Security
For more information on Responsible AI, one can visit the below URL

https://www.microsoft.com/en-us/ai/responsible-ai
    
--------------------------------------------------------------------------------------------------------------------------
Q-093: Your team is planning on using the Computer Vision service. Can you use the service to detect faces from images?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes , this is possible with the Computer Vision service
For more information on the Computer Vision service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/overview    

--------------------------------------------------------------------------------------------------------------------------
Q-094: Your team is designing an AI system. Here they want to ensure that the AI system is tested thoroughly before it can 
be used. Which of the following Microsoft principle of AI does this come under?
--------------------------------------------------------------------------------------------------------------------------
a. Fairness
b. Reliability & Safety
c. Privacy & Security
d. Inclusiveness
e. Transparency
f. Accountability

Answer: b. Reliability & Safety

Overall explanation: This comes under the principle of Reliability & Safety
For more information on Responsible AI, one can visit the below URL

https://www.microsoft.com/en-us/ai/responsible-ai    

--------------------------------------------------------------------------------------------------------------------------
Q-095: Your team is planning on working with the Azure Machine Learning service. They need to set up the required compute 
target environments. Which of the following is the Azure Machine Learning compute clusters used for?
--------------------------------------------------------------------------------------------------------------------------
a. Real-time inference
b. Batch-Interference

Answer: b. Batch-Interference

Overall explanation : This is used for Batch inference workloads.
For more information on Azure Machine Learning compute targets, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-compute-target
    
--------------------------------------------------------------------------------------------------------------------------
Q-096: Your team is planning on working with the Azure Machine Learning service. They need to set up the required compute 
target environments. Which of the following is the Azure Kubernetes Service target environment used for?
--------------------------------------------------------------------------------------------------------------------------
a. Real-time inference
b. Batch-Interference

Answer: a. Real-time inference

Overall explanation: This is used for Real-time inference workloads.
For more information on Azure Machine Learning compute targets, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-compute-target

--------------------------------------------------------------------------------------------------------------------------
Q-097: Your team is planning on using the Machine Learning Designer. The team is working on a pipeline. Does the designer 
save your progress in the pipeline as you are editing it?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: Yes, all of the pipeline work is saved as draft work.
For more information on the Machine Learning Designer, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer
    
--------------------------------------------------------------------------------------------------------------------------
Q-098: Your team is planning on using the Machine Learning Designer. Is the Machine Learning Designer a drag-and-drop 
interface that can be used to train and deploy models in Azure Machine Learning?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation: This is one of the main features of the Machine Learning Designer.
For more information on the Machine Learning Designer, one can visit the below URL

https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer
    
--------------------------------------------------------------------------------------------------------------------------
Q-099: Your team currently has the following data set
![GitHub Images](/Azure/Assets/Q&As/Dataset.jpg)
You have to train a model that will predict the Course Category Sales.
Which of the following would “Course Category Sales
--------------------------------------------------------------------------------------------------------------------------
a. A Feature
b. A Label

Answer: b. A Label

Overall explanation: This is what you want to predict. Hence this will be a label.
    
--------------------------------------------------------------------------------------------------------------------------
Q-100: Your team currently has the following data set
![GitHub Images](/Azure/Assets/Q&As/Dataset.jpg)
You have to train a model that will predict the Course Category Sales.
Which of the following would “Number of courses” be in this case?
--------------------------------------------------------------------------------------------------------------------------
a. A Feature
b. A Label

Answer: a. A Feature

Overall explanation : Here you can use the attribute of “Number of courses” to predict the Course Category Sales. Hence 
this can be a feature.    

--------------------------------------------------------------------------------------------------------------------------
Q-101: Your team needs to build an object detection model. Here they want to use their own images to train the model. 
Which of the following service can be used for this requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Face API
b. Custom Vision
c. Computer Vision

Answer: b. Custom Vision

Overall explanation: You can use the Custom Vision API for this requirement
For more information on the Custom Vision service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/overview

--------------------------------------------------------------------------------------------------------------------------
Q-102: Which of the following can be accomplished with the use of the Computer Vision service? Choose 2 answers from the 
options given below
--------------------------------------------------------------------------------------------------------------------------
a. Extract text from images
b. Convert text from one language to another
c. Extract key phrases from text
d. Extract visual features from images

Answer: a. Extract text from images, d. Extract visual features from images

Overall explanation: You can extract text and visual features from images.
For more information on the Computer Vision service, one can visit the below URL

https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/overview 
   
--------------------------------------------------------------------------------------------------------------------------
Q-103: Your team need to create a machine learning model that will be used to predict numeric values based on input data. 
Which of the following algorithm type should they use for this requirement?
--------------------------------------------------------------------------------------------------------------------------
a. Regression 
b. Anomaly
c. Classification
d. Clustering

Answer: a. Regression 

Overall explanation : Here you will use the Regression-based algorithm.

--------------------------------------------------------------------------------------------------------------------------
Q-104: You are planning on using the Custom Vision service. Do you need to provide your own images to train the model in 
Custom Vision?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : Yes, when you create a project in the Custom Vision service, you have to upload your own images to 
train the model.

--------------------------------------------------------------------------------------------------------------------------
Q-105: Can you use the Face API to return face attributes such as headPose and occlusion?
--------------------------------------------------------------------------------------------------------------------------
a. Yes
b. No

Answer: a. Yes

Overall explanation : Yes, this is possible.

API link:
 https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236
    
--------------------------------------------------------------------------------------------------------------------------
Q-106: Which AI workload should you use for the customer support department?
--------------------------------------------------------------------------------------------------------------------------
Answer: Conversational AI will allow simple inquiries to be handled by an automated bot. You can create a chatbot for your 
website, create an assistant for customer service agents, and even enable a bot in a mobile app

--------------------------------------------------------------------------------------------------------------------------
Q-107: Which principle of Responsible AI should you employ to gain the trust of users in your bot?
--------------------------------------------------------------------------------------------------------------------------
Answer: Transparency is the principle that AI-based solutions should be understandable. Users should be aware of the 
purpose of the AI-based system, how it operates, and its scope and limitations. A chatbot should clearly tell the user 
that it is a bot and what it can and cannot do.

--------------------------------------------------------------------------------------------------------------------------
Q-108: Which AI workload should you use to analyze the images for skin conditions?
--------------------------------------------------------------------------------------------------------------------------
Answer: Computer vision allows you to analyze images. You can train computer vision with existing images to classify 
images to determine the type of skin complaint

--------------------------------------------------------------------------------------------------------------------------
Q-108: How can you address the storage requirements for the images?
--------------------------------------------------------------------------------------------------------------------------
Answer: You can run AI in the app on the mobile device. The image will not need to be stored and will not leave the device.
 You will instead store the results of the classification along with other symptom data and discard the image.
 
--------------------------------------------------------------------------------------------------------------------------
Q-109:  Which AI workload could identify adverse reactions to a drug treatment?
--------------------------------------------------------------------------------------------------------------------------
Answer: Anomaly detection can detect adverse reactions. It can detect where there is a change in trends and can detect 
unusual readings.
--------------------------------------------------------------------------------------------------------------------------
Q-110: Which principle of Responsible AI requires rigorous testing of your AI-based app?
--------------------------------------------------------------------------------------------------------------------------
Answer: Reliability & Safety requires the rigorous testing of an AI-based system’s functionality and deployment to ensure 
that it works as expected and to eliminate potential risk to human life.

--------------------------------------------------------------------------------------------------------------------------
Q-111: Which machine learning type should you use to determine if a social media post has positive or negative sentiment?
--------------------------------------------------------------------------------------------------------------------------
Answer: The classification machine learning model is used to predict mutually exclusive categories. Classification 
involves learning using labels to classify data. Two-class classification algorithms can provide an either/or answer 
such as a social media post having a positive or negative sentiment.

--------------------------------------------------------------------------------------------------------------------------
Q-112: Which type of machine learning groups unlabeled data using similarities in the data?
--------------------------------------------------------------------------------------------------------------------------
Answer: The clustering machine learning model analyzes unlabeled data to find similarities in data points and groups them 
together into clusters. The clustering algorithm segments data into multiple groups based on similarities in the data

--------------------------------------------------------------------------------------------------------------------------
Q-113: Which two datasets do you split your data into when building a machine learning model?
--------------------------------------------------------------------------------------------------------------------------
Answer: The dataset is split into a training dataset and a testing dataset. The testing dataset is often referred to as the 
validation dataset.
--------------------------------------------------------------------------------------------------------------------------
Q-114: Which metrics can you use to evaluate a regression machine learning model?
--------------------------------------------------------------------------------------------------------------------------
Answer: Root mean squared error (RMSE) is used to evaluate regression models. RMSE is a measure of the dif ference between 
predictions and actual values. The closer RMSE is to 0, the better the model is performing. You can also use Coefficient 
of Determination.

--------------------------------------------------------------------------------------------------------------------------
Q-115: Which metrics can you use to evaluate a classification machine learning model?
--------------------------------------------------------------------------------------------------------------------------
Answer: Precision is a measure of the correct positive results. Precision is the number of true positives divided by the 
sum of the number of true positives and false positives. Precision is scored between 0 and 1, with closer to 1 being 
better.You can also use Accuracy and F-Score.

--------------------------------------------------------------------------------------------------------------------------
Q-116: Which compute tar get should you use for development of machine learning models?
--------------------------------------------------------------------------------------------------------------------------
Answer: A compute instance is a configured development environment for machine learning.

--------------------------------------------------------------------------------------------------------------------------
Q-117:  What is used to increase the predictive power of a machine learning model?
--------------------------------------------------------------------------------------------------------------------------
Answer: Feature engineering is the process of creating new features from raw data to increase the predictive power of the 
machine learning model.

--------------------------------------------------------------------------------------------------------------------------
Q-118: What should you do to prevent your model from being biased by one feature?
--------------------------------------------------------------------------------------------------------------------------
Answer: Normalization is the method that adjusts the values in numeric columns so that all numeric values are on a common 
scale, normally between 0 and 1. A dataset that has values using different scales can bias the model toward that feature.

--------------------------------------------------------------------------------------------------------------------------
Q-119: What should you do to enable a trained machine learning model to be measured for accuracy?
--------------------------------------------------------------------------------------------------------------------------
Answer: Y ou should score the model. After a model has been trained, the model should be evaluated using a different set 
of data. Scoring applies the validation dataset to the trained model to generate predictions that can be evaluated using 
metrics that measure the accuracy of the predictions.

--------------------------------------------------------------------------------------------------------------------------
Q-120: What should you do after training your model prior to deploying your model as a web service?
--------------------------------------------------------------------------------------------------------------------------
Answer: After training your model, you need to create an inference pipeline that performs the same steps for new data 
input, not the sample data used in training.

--------------------------------------------------------------------------------------------------------------------------
Q-121: You use Automated ML to find the best model for your data. Which option should you use to interpret and provide 
transparency for the model selected?
--------------------------------------------------------------------------------------------------------------------------
Answer: Explain best model generates an explanation for the model that was identified as the best model.

--------------------------------------------------------------------------------------------------------------------------
Q-122: which two types of datasets can you register and use to train Automatic Machine Learning (AutoML) models?
--------------------------------------------------------------------------------------------------------------------------
Answer: File and tabular datasets can be used in Azure Machine Learning training workflows.

--------------------------------------------------------------------------------------------------------------------------
Q-123: Which of the following best describes the predictions made by a machine learning model?
--------------------------------------------------------------------------------------------------------------------------
a.  Absolutely correct values based on conditional logic.
b.  Randomly selected values with an equal chance of selection.
c.  Probabilistic values based on correlations found in training data.

Answer:  c.  Probabilistic values based on correlations found in training data.

Explanation: Machine learning models are trained using historic data, and rely on algorithms that find statistical 
relationships in the data. Predictions are generally based on probability; and while models are often extremely accurate, 
predictions are based on a confidence score that indicates a level of probability.

--------------------------------------------------------------------------------------------------------------------------
Q-124:	A data scientist has used Azure Machine Learning to train a machine learning model. How can you use the model in 
your application? 
--------------------------------------------------------------------------------------------------------------------------
a.  Use Azure Machine Learning to publish the model as a web service.
b.  Export the model as an Azure AI service.
c.  You must build your application using the Azure Machine Learning designer.

Answer:   a.  Use Azure Machine Learning to publish the model as a web service.

Explanation: You can use Azure Machine Learning to publish a trained model as a web service, and consume it from 
applications through its REST interface.

--------------------------------------------------------------------------------------------------------------------------  
Q-125: You want to index a collection of text documents, and search them from a mobile application. Which service should 
you use to create the index? 
--------------------------------------------------------------------------------------------------------------------------
a.  The Azure AI service
b.  Azure AI Search
c.  Azure OpenAI Service

Answer: b.  Azure AI Search    

--------------------------------------------------------------------------------------------------------------------------
Q-126: How are client applications typically granted access to an Azure AI Services endpoint? 
--------------------------------------------------------------------------------------------------------------------------
a. The application must specify a valid subscription key for the Azure Resource.
b. The user of the application must enter a username and password associated with the Azure Subscription
c. Access to Azure AI Services is granted to anonymous users by default

Answer: a. The application must specify a valid subscription key for the Azure Resource.

--------------------------------------------------------------------------------------------------------------------------
Q-127: In which format are message exchanged between a cliet app and an Azure AI Services resource when using a REST API?
--------------------------------------------------------------------------------------------------------------------------
a. XML
b. JSON
c. HTML

Answer: b. JSON

--------------------------------------------------------------------------------------------------------------------------
Q-128: You need to regenerate the primary subscription key for an Azure AI Services resource that an app uses. What 
should you do first to minimize service interruption for the app? 
--------------------------------------------------------------------------------------------------------------------------
a. Switch the app to use the secondary key
b. Change the resource endpoint
c. Enable a firewall

Answer: a. Switch the app to use the secondary key

--------------------------------------------------------------------------------------------------------------------------
Q-129: You want to store the subscription keys for an Azure AI Services resource securely, so that authorized apps can 
retrieve them when needed. What kind of Azure resource should you provision. 
--------------------------------------------------------------------------------------------------------------------------
a. Azure Storage
b. Azure Key Vault
c. Azure App Service

Answer: b. Azure Key Vault

--------------------------------------------------------------------------------------------------------------------------
Q-130: When running code on your computer that connects to Azure AI Services, you receive an error that access is denied 
due to Virtual Network/Firewall rules. What configuration do you need to set in the Azure AI Services instance? 
--------------------------------------------------------------------------------------------------------------------------
a. In the Networking properties, configure Selected Networks and Private Endpoints.
b. In Networking properties, add your client IP address to the Firewall allowed list.
c. In Access control, add your Microsoft Entra ID user account to a role.

Answer: b. In Networking properties, add your client IP address to the Firewall allowed list.

--------------------------------------------------------------------------------------------------------------------------
Q-131: How should you collect telemetry for your Azure AI Services resource for later analysis? 
--------------------------------------------------------------------------------------------------------------------------
a. Create an alert.
b. Configure diagnostic settings.
c. Create a dashboard.

Answer: b. Configure diagnostic settings.

--------------------------------------------------------------------------------------------------------------------------
Q-132: You are defining an alert that notifies you when a key regeneration event is recorded in the activity log for your 
Azure AI Services resource. What should you do? 

a. Specify a Scope of Activity Log.
b. Specify an Action that uses an Azure Logic App to read the activity log.
c. Specify a Condition with a Signal Type of Activity Log.

Answer: c. Specify a Condition with a Signal Type of Activity Log.

--------------------------------------------------------------------------------------------------------------------------
Q-134: You are viewing a metric for your Azure AI Services resource in a chart. You want to combine the chart with 
visualizations of other resources and data. What should you do? 
--------------------------------------------------------------------------------------------------------------------------
a. Add the chart to a dashboard
b. Share the chart
c. Clone the chart

Answer: a. Add the chart to a dashboard

--------------------------------------------------------------------------------------------------------------------------
Q-135: 	You plan to use an Azure AI services container in a local Docker host. Which of the following statements is true? 
--------------------------------------------------------------------------------------------------------------------------
a. Client applications must pass a subscription key to the Azure resource endpoint before using the container.
b. The container must be able to connect to the Azure resource endpoint to send usage data for billing.
c. All data passed from the client application to the container is forwarded to the Azure resource endpoint.

Answer: b. The container must be able to connect to the Azure resource endpoint to send usage data for billing.

--------------------------------------------------------------------------------------------------------------------------
Q-136: Which of the following parameters must you specify when deploying an Azure AI services container image? 
--------------------------------------------------------------------------------------------------------------------------
a. EULA
b. ResourceGroup
c. SubscriptionName

Answer: a. EULA

Explanation: You must specify a EULA parameter with the value "yes" to explicitly accept the license agreement.

--------------------------------------------------------------------------------------------------------------------------
Q-137: You plan to use the language detection functionality of Azure AI Language in a container. Which container image 
should you deploy? 
--------------------------------------------------------------------------------------------------------------------------
a. mcr.microsoft.com/azure-ai-services/textanalytics
b. mcr.microsoft.com/azure-ai-services
c. mcr.microsoft.com/azure-ai-services/textanalytics/language

Answer: c. mcr.microsoft.com/azure-ai-services/textanalytics/language

--------------------------------------------------------------------------------------------------------------------------
Q-138: You want to use the Azure AI Vision Analyze Image function to generate an appropriate caption for an image. Which 
visual feature should you specify? 
--------------------------------------------------------------------------------------------------------------------------
a. Tags
b. Description
c. Categories

Answer: Description
Explanation: To generate a caption, include the description visual feature in your analysis

--------------------------------------------------------------------------------------------------------------------------
Q-139: What is the purpose of the Azure AI Vision service? 
--------------------------------------------------------------------------------------------------------------------------
a. To provide functionality for audio transcription
b. To extract information from images
c. To detect the presence and location of specific sounds within an audio file

Answe: b. To extract information from images
Explanation: The Azure AI Vision service is designed to help you extract information from images through various 
functionalities

--------------------------------------------------------------------------------------------------------------------------

