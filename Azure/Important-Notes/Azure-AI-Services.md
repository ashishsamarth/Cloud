--------------------------------------------------------------------------------------------------------------------------
Azure AI Services
--------------------------------------------------------------------------------------------------------------------------

1. Vision Studio : Allows to process images and return information
    - Image Analysis (Object detection / Person detection) : Used to extract features from images like objects / Coordiantes
    - Optical Character Recognition : Extract text from images
    - Spatial Analysis : Used to analyze the presence and movement of individual in a video feed.
    - Face Detection : To detect the human face in the image and return location coordinates
    - Custom Vision : Allows you to train your own image models [Select appropriate class and domain]
    - Document Intelligence : Process the data in forms and documents

    Special Note : If you wish to use the Postman to call the Vision API services, you will need to use the 
     - oci-apim-subscription-key 
     - content-type : application/octect-stream
     - reqest type  : binary


2. Natural Languauge Processing : Allows
    - Key Phrase Extraction   : Look for specific key words
    - Entity Recognition      : Has the ability to read text ad then categorize them {Name, Phone # etc}
    - Sentiment Analysis      : Has the ability to read text and understand the content and relay if its positive / negative 
    - Translation             : Has the ability to translate text / speech from one language to another
    - Speed Recognition       : Has the ability to listen to speech and generate content
    - Speech Synthesis        : Has the ability to generate speech
    - Question Answer Service : Has the ability to connect to a chat bot and respond like a customer care agent.

--------------------------------------------------------------------------------------------------------------------------
Describe The Azure Bot Service

--------------------------------------------------------------------------------------------------------------------------
The Azure Bot Service is a cloud-based platform for developing, deploying, and managing bots. Azure Bot Services provide 
the capabilities known as conversational AI.
Conversational AI is where the computer simulates a conversation with a user or customer. Conversational AI has extended 
beyond simple chatbots to intelligence agents and virtual assistants like Cortana

There are two conversational AI services included in the Azure AI Fundamentals exam

1. QnA Maker A tool to build a bot using existing support and other documentation.
2. Azure Bot Service Tools to build, test, deploy, and manage bots.

Both QnA Maker and the Azure Bot Service leverage the Language Understanding (LUIS) service in Cognitive Services.

--------------------------------------------------------------------------------------------------------------------------
Cognitive Services

--------------------------------------------------------------------------------------------------------------------------
Cognitive Services are a family of AI services and APIs that you can use to build intelligent solutions. Cognitive Services
 enable applications to see, hear , speak, search, understand, and begin with decision-making.

 This family of AI services is categorized into five groups: 
 - Decision 
 - Language 
 - Speech 
 - Vision 
 - Web search

 Decision Group: 
    - Anomaly Detector : Quickly identify potential problems by detecting unusual data points or trends in time-series data. 
    - Metrics Advisor : Built on Anomaly Detector , this service identifies the key areas for root cause analysis. Metrics 
        Advisor helps focus on fixing issues rather than monitoring.
    - Content Moderator : Detect potentially of fensive or undesirable text, image, and video content. Content Moderator 
        provides a review tool, where a human can validate flagged content and improve the sensitivity of moderation.
     - Personalizer : Creates a personalized experience for a user based on his/her behavior . This could be content shown 
        on a website or providing a dif ferent layout. Personalizer is an example of reinforcement learning.

Languauge Group:
    - Immersive Reader : Helps readers of all ages and abilities to comprehend text using audio and visual cues. Immersive 
        Reader can be used to improve literacy .
    - Language Understanding : Builds natural language understanding into apps, bots, and IoT devices. Language Understanding 
        interprets the intent and extracts key information from supplied text.
    - QnA Maker : Creates a conversational question and answer layer on your existing F AQ and company information.
    - Text Analytics : Discovers insights from textual data. T ext Analytics is one of the most used Cognitive Services. 
        You can detect the sentiment of sentences or whole paragraphs. Y ou can extract key phrases from a piece of text, 
        and extract entities such as people, places, and things from a piece of text. T ext Analytics supports a wide range 
        of languages.
     - Translator : Detects and translates text in real-time or in batch across more than 90 languages.

Speech Group:
    - Speech to Text : Transcribes audio into readable, searchable text in real-time or from audio files. 
    - Text to Speech : Synthesizes text into lifelike speech. 
    - Speech Translation : Converts audio into text and translates into another language in real-time. Speech Translation 
    utilizes the Translator services. 
    - Speaker Recognition : Identifies people from the voices in an audio clip.

Vision Group:
    - Computer Vision service : Analyzes content in images and video and extracts details from the images. 
    - Custom Vision : Trains computer vision with your own set of images that meets your business requirements. 
    - Face : Detects faces in images and describes their features and emotions. Face can also recognize and verify people 
        from images. 
    - Form Recognizer : Extracts text, key-value pairs, and tables from documents. 
    - Video Analyzer for Media : Analyzes the visual and audio channels of a video and indexes its content.

Web Search:
    Allows you to utilize the Bing search engine to search millions of webpages for images, news, product, and company 
    information. These services have been moved from Cognitive Services to a separate service, Bing W eb Search.

--------------------------------------------------------------------------------------------------------------------------    