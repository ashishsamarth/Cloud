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