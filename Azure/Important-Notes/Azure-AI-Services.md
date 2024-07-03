--------------------------------------------------------------------------------------------------------------------------
    Azure AI Services

--------------------------------------------------------------------------------------------------------------------------
1. Vision Studio : Allows to process images and return information
    Image Analysis (Object detection / Person detection) : Used to extract features from images like objects / Coordiantes
    Optical Character Recognition : Extract text from images
    Spatial Analysis : Used to analyze the presence and movement of individual in a video feed.
    Face Detection : To detect the human face in the image and return location coordinates
    Custom Vision : Allows you to train your own image models [Select appropriate class and domain]
    Document Intelligence : Process the data in forms and documents

    Special Note : If you wish to use the Postman to call the Vision API services, you will need to use the 
     - oci-apim-subscription-key 
     - content-type : application/octect-stream
     - reqest type  : binary

2. Natural Languauge Processing : Allows
    Key Phrase Extraction   : Look for specific key words
    Entity Recognition      : Has the ability to read text ad then categorize them {Name, Phone # etc}
    Sentiment Analysis      : Has the ability to read text and understand the content and relay if its positive / negative 
    Translation             : Has the ability to translate text / speech from one language to another
    Speed Recognition       : Has the ability to listen to speech and generate content
    Speech Synthesis        : Has the ability to generate speech