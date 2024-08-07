--------------------------------------------------------------------------------------------------------------------------
Azure AI Services
--------------------------------------------------------------------------------------------------------------------------
Azure AI services are cloud-based services that encapsulate AI capabilities. Rather than a single product, you should 
think of AI services as a set of individual services that you can use as building blocks to compose sophisticated, 
intelligent applications.

![Github Image](/Azure/Assets/AI-Related-Terms/Azure-AI-Services.PNG)

1. **Vision Studio** : Allows to process images and return information
    - Image Analysis (Object detection / Person detection) : Used to extract features from images like objects / Coordiantes
    - Optical Character Recognition : Extract text from images
    - Spatial Analysis : Used to analyze the presence and movement of individual in a video feed.
    - Face Detection : To detect the human face in the image and return location coordinates
    - Custom Vision : Allows you to train your own image models [Select appropriate class and domain]
    - Document Intelligence : Process the data in forms and documents

    **Special Note** : If you wish to use the Postman to call the Vision API services, you will need to use the 
     - oci-apim-subscription-key 
     - content-type : application/octect-stream
     - reqest type  : binary


2. **Natural Languauge Processing** : Allows
    - Key Phrase Extraction   : Look for specific key words
    - Entity Recognition      : Has the ability to read text ad then categorize them {Name, Phone # etc}
    - Sentiment Analysis      : Has the ability to read text and understand the content and relay if its positive / negative 
    - Translation             : Has the ability to translate text / speech from one language to another
    - Speed Recognition       : Has the ability to listen to speech and generate content
    - Speech Synthesis        : Has the ability to generate speech
    - Question Answer Service : Has the ability to connect to a chat bot and respond like a customer care agent.

--------------------------------------------------------------------------------------------------------------------------
**Describe The Azure Bot Service**
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
**Cognitive Services**
--------------------------------------------------------------------------------------------------------------------------
Cognitive Services are a family of AI services and APIs that you can use to build intelligent solutions. Cognitive Services
 enable applications to see, hear , speak, search, understand, and begin with decision-making.

 This family of AI services is categorized into five groups: 
 - Decision 
 - Language 
 - Speech 
 - Vision 
 - Web search

 **Decision Group**: 
- Anomaly Detector  : Quickly identify potential problems by detecting unusual data points or trends in time-series data. 
- Metrics Advisor   : Built on Anomaly Detector , this service identifies the key areas for root cause analysis. Metrics 
Advisor helps focus on fixing issues rather than monitoring.
- Content Moderator : Detect potentially of fensive or undesirable text, image, and video content. Content Moderator provides 
a review tool, where a human can validate flagged content and improve the sensitivity of moderation.
- Personalizer      : Creates a personalized experience for a user based on his/her behavior . This could be content shown 
on a website or providing a dif ferent layout. Personalizer is an example of reinforcement learning.

**Languauge Group**:
- Immersive Reader : Helps readers of all ages and abilities to comprehend text using audio and visual cues. 
Immersive Reader can be used to improve literacy .
- Language Understanding : Builds natural language understanding into apps, bots, and IoT devices. Language Understanding 
interprets the intent and extracts key information from supplied text.
- QnA Maker : Creates a conversational question and answer layer on your existing F AQ and company information.
- Text Analytics : Discovers insights from textual data. T ext Analytics is one of the most used Cognitive Services. 
You can detect the sentiment of sentences or whole paragraphs. You can extract key phrases from a piece of text, and extract 
entities such as people, places, and things from a piece of text. Text Analytics supports a wide range of languages.
- Translator : Detects and translates text in real-time or in batch across more than 90 languages.

**Speech Group**:
- Speech to Text : Transcribes audio into readable, searchable text in real-time or from audio files. 
- Text to Speech : Synthesizes text into lifelike speech. 
- Speech Translation : Converts audio into text and translates into another language in real-time. Speech Translation 
    utilizes the Translator services. 
- Speaker Recognition : Identifies people from the voices in an audio clip.

**Vision Group**:
- Computer Vision service : Analyzes content in images and video and extracts details from the images. 
- Custom Vision : Trains computer vision with your own set of images that meets your business requirements. 
- Face : Detects faces in images and describes their features and emotions. Face can also recognize and verify people 
 from images. 
- Form Recognizer : Extracts text, key-value pairs, and tables from documents. 
- Video Analyzer for Media : Analyzes the visual and audio channels of a video and indexes its content.

**Web Search**:
Allows you to utilize the Bing search engine to search millions of webpages for images, news, product, and company 
    information. These services have been moved from Cognitive Services to a separate service, Bing W eb Search.

--------------------------------------------------------------------------------------------------------------------------
Identify endpoints and keys
--------------------------------------------------------------------------------------------------------------------------

When you provision an Azure AI services service resource in your Azure subscription, you are defining an endpoint through 
which the service can be consumed by an application.

To consume the service through the endpoint, applications require the following information:

**The endpoint URI** -  This is the HTTP address at which the REST interface for the service can be accessed. Most
     AI services software development kits (SDKs) use the endpoint URI to initiate a connection to the endpoint.
    
**A subscription key** - Access to the endpoint is restricted based on a subscription key. Client applications must provide 
a valid key to consume the service. When you provision an AI services resource, two keys are created - applications can use 
either key. You can also regenerate the keys as required to control access to your resource.

**The resource location** - When you provision a resource in Azure, you generally assign it to a location, which 
determines the Azure data center in which the resource is defined. While most SDKs use the endpoint URI to connect to the 
service, some require the location.

--------------------------------------------------------------------------------------------------------------------------
Use a REST API
--------------------------------------------------------------------------------------------------------------------------
Azure AI services provide REST application programming interfaces (APIs) that client applications can use to consume 
services. In most cases, service functions can be called by submitting data in JSON format over an HTTP request, which may 
be a POST, PUT, or GET request depending on the specific function being called. The results of the function are returned 
to the client as an HTTP response, often with JSON contents that encapsulate the output data from the function.

![Github Image](/Azure/Assets/AI-Related-Terms/Azure-REST-API.PNG)

The use of REST interfaces with an HTTP endpoint means that any programming language or tool capable of submitting and 
receiving JSON over HTTP can be used to consume AI services. You can use common programming languages such as Microsoft C#
, Python, and JavaScript; as well as utilities such as Postman and cURL, which can be useful for testing.

--------------------------------------------------------------------------------------------------------------------------
Use a SDK
--------------------------------------------------------------------------------------------------------------------------
You can develop an application that uses Azure AI services using REST interfaces, but it's easier to build more complex 
solutions by using native libraries for the programming language in which you're developing the application.

![Github Image](/Azure/Assets/AI-Related-Terms/Azure-SDK.PNG)

Software development kits (SDKs) for common programming languages abstract the REST interfaces for most AI services. SDK 
availability varies by individual AI services, but for most services there's an SDK for languages such as:

- Microsoft C# (.NET Core)
- Python
- JavaScript (Node.js)
- Go
- Java

Each SDK includes packages that you can install in order to use service-specific libraries in your code, and online 
documentation to help you determine the appropriate classes, methods, and parameters used to work with the service.

--------------------------------------------------------------------------------------------------------------------------
Azure Authentication
--------------------------------------------------------------------------------------------------------------------------
By default, access to Azure AI services resources is restricted by using subscription keys. Management of access to these 
keys is a primary consideration for security

**Regenerate Keys**
You should regenerate keys regularly to protect against the risk of keys being shared with or accessed by unauthorized users. 
You can regenerate keys using the Azure portal, or 
using the az cognitiveservices account keys regenerate Azure command-line interface (CLI) command

Each AI service is provided with two keys, enabling you to regenerate keys without service interruption. To accomplish this:

    a. If you're using both keys in production, change your code so that only one key is in use. 
    For example, configure all production applications to use key 1.
    b. Regenerate key 2.
    c. Switch all production applications to use the newly regenerated key 2.
    d. Regenerate key 1
    e. Finally, update your production code to use the new key 1.

For example, to regenerate keys in the Azure portal, you can do the following:

    a. In the Azure portal, go to your resource's Keys and Endpoint pane.
    b. Then select Regenerate Key1 or select Regenerate Key2, depending on which one you want to regenerate at the time.


**Protect keys with Azure Key Vault**
Azure Key Vault is an Azure service in which you can securely store secrets (such as passwords and keys). Access to 
the key vault is granted to security principals, which you can think of user identities that are authenticated using 
Microsoft Entra ID. Administrators can assign a security principal to an application (in which case it is known as a 
service principal) to define a managed identity for the application. 
The application can then use this identity to access the key vault and retrieve a secret to which it has access. Controlling 
access to the secret in this way minimizes the risk of it being compromised by being hard-coded in an application or saved 
in a configuration file.

You can store the subscription keys for an AI services resource in Azure Key Vault, and assign a managed identity to 
client applications that need to use the service. The applications can then retrieve the key as needed from the key 
vault, without risk of exposing it to unauthorized users.

![Github Image](/Azure/Assets/AI-Related-Terms/Azure-Authentication-Protect-Keys-In-Azure-Key-Vault.PNG)

**Token Based Authentication**
When using the REST interface, some AI services support (or even require) token-based authentication. In these cases, 
the subscription key is presented in an initial request to obtain an authentication token, which has a valid period of 
10 minutes. Subsequent requests must present the token to validate that the caller has been authenticated.

Note: When using an SDK, the calls to obtain and present a token are handled for you by the SDK.


**Microsoft Entra ID authentication**
Azure AI services supports Microsoft Entra ID authentication, enabling you to grant access to specific service principals
 or managed identities for apps and services running in Azure.There are different ways you can authenticate against 
 Azure AI services using Microsoft Entra ID, including:

 -Authenticate using service principals
    -Create a custom subdomain
    You can create a custom subdomain in different ways including through the Azure portal, Azure CLI, or PowerShell.
    For example: You can create a subdomain using PowerShell in the Azure Cloud Shell. To do this, you select your 
    subscription using the following command:

    Powershell: Set-AzContext -SubscriptionName <Your-Subscription-Name>
    Powershell: $account = New-AzCognitiveServicesAccount -ResourceGroupName <your-resource-group-name> 
                -name <your-account-name> -Type <your-account-type> -SkuName <your-sku-type> -Location <your-region> 
                -CustomSubdomainName <your-unique-subdomain-name>
    
    -Assign a role to a service principal
    You've created an Azure AI resource that is linked with a custom subdomain. Next, you assign a role to a service 
    principal.To start, you'll need to register an application. To do this, you run the following command:

    Powershell: $SecureStringPassword = ConvertTo-SecureString -String <your-password> -AsPlainText -Force
    Powershell: $app = New-AzureADApplication -DisplayName <your-app-display-name> -IdentifierUris <your-app-uris> 
                -PasswordCredentials $SecureStringPassword

    This creates the application resource.

    Then you use the New-AzADServicePrincipal command to create a service principal and provide your application's ID:

    Powershell: New-AzADServicePrincipal -ApplicationId <app-id>

    Finally, you assign the Cognitive Services Users role to your service principal by running:

    Powershell: New-AzRoleAssignment -ObjectId <your-service-principal-object-id> -Scope <account-id> 
                -RoleDefinitionName "Cognitive Services User"


 -Authenticate using managed identities
    Managed identities come in two types:
    - **System-assigned managed identity** : A managed identity is created and linked to a specific resource, such as a 
    virtual machine that needs to access Azure AI services. When the resource is deleted, the identity is deleted as well.

    - **User-assigned managed identity** : The managed identity is created to be useable by multiple resources instead 
    of being tied to one. It exists independently of any single resource.

--------------------------------------------------------------------------------------------------------------------------
Implement network security
--------------------------------------------------------------------------------------------------------------------------
**Apply network access restrictions**
By default, Azure AI services are accessible from all networks. Some individual AI services resources (such as Azure AI 
Face service, Azure AI Vision, and others) can be configured to restrict access to specific network addresses - either 
public Internet addresses or addresses on virtual networks.

![Github Image](/Azure/Assets/AI-Related-Terms/Azure-Network-Restrictions.PNG)

With network restrictions enabled, a client trying to connect from an IP address that isn't allowed will receive an Access 
Denied error.

--------------------------------------------------------------------------------------------------------------------------
Deploy Azure AI services in containers
--------------------------------------------------------------------------------------------------------------------------
Containers enable you to host Azure AI services either on-premises or in Azure. 

For example: if your application uses sensitive data in an on-premises SQL Server to call an Azure AI services service, 
you can deploy Azure AI services in containers on the same network. Now your data can stay on your local network and not 
be passed to the cloud. Deploying Azure AI services in a container on-premises will also decrease the latency between the 
service and your local data, which can improve performance.

**Understand containers**: 
When you deploy a software service, it must be hosted in an environment that provides the hardware, operating system, and 
supporting runtime components on which the service depends.

Azure AI services is provided as a cloud service, in which the service software is hosted in an Azure data center that 
provides the underlying runtime services, operating system, and hardware. However, you can also deploy some Azure AI 
services in a container, which encapsulates the necessary runtime components, and which is in turn deployed in a container 
host that provides the underlying operating system and hardware.

**What is a container?**:
A container comprises an application or service and the runtime components needed to run it, while abstracting the 
underlying operating system and hardware. In practice, this abstraction results in two significant benefits:
- Containers are portable across hosts, which may be running different operating systems or use different hardware - 
making it easier to move an application and all its dependencies.
- A single container host can support multiple isolated containers, each with its own specific runtime configuration - 
making it easier to consolidate multiple applications that have different configuration requirement.

A container is encapsulated in a container image that defines the software and configuration it must support. 
Images can be stored in a central registry, such as Docker Hub, or you can maintain a set of images in your own registry.

**Container deployment**:
To use a container, you typically pull the container image from a registry and deploy it to a container host, specifying 
any required configuration settings. The container host can be in the cloud, in a private network, or on your local 
computer. 
For example:
- A Docker* server.
- An Azure Container Instance (ACI).
- An Azure Kubernetes Service (AKS) cluster.

Docker is an open source solution for container development and management that includes a server engine that you can use 
to host containers. There are versions of the Docker server for common operating systems, including Microsoft Windows and 
Linux.

--------------------------------------------------------------------------------------------------------------------------
Use Azure AI services containers
--------------------------------------------------------------------------------------------------------------------------
There are container images for Azure AI services in the Microsoft Container Registry that you can use to deploy a 
containerized service that encapsulates an individual Azure AI services service API.
To deploy and use an Azure AI services container, the following three activities must occur:
- 1.The container image for the specific Azure AI services API you want to use is downloaded and deployed to a container 
host, such as a local Docker server, an Azure Container Instance (ACI), or Azure Kubernetes Service (AKS).
- 2.Client applications submit data to the endpoint provided by the containerized service, and retrieve results just as 
they would from an Azure AI services cloud resource in Azure.
- 3.Periodically, usage metrics for the containerized service are sent to an Azure AI services resource in Azure in order 
to calculate billing for the service.

![Github Image](/Azure/Assets/AI-Related-Terms/Azure-AI-Services-Containers.PNG)

**Azure AI services container images**:
Each container provides a subset of Azure AI services functionality. For example, not all features of the Azure AI 
Language service are in a single container. Language detection, translation, and sentiment analysis are each separate 
container images. However, the setup steps are similar for each container.

- Language-Containers
![Github Image](/Azure/Assets/AI-Related-Terms/Azure-AI-Services-Container-Images.PNG)

- Speech Containers
![Github Image](/Azure/Assets/AI-Related-Terms/Azure-AI-Services-Container-Images-Speech-Service.PNG)

- Vision Containers
![Github Image](/Azure/Assets/AI-Related-Terms/Azure-AI-Services-Container-Images-Vision-Service.PNG)

**Azure AI services container configuration**
![Github Image](/Azure/Assets/AI-Related-Terms/Azure-AI-Services-Container-Configuration.PNG)

**Consuming Azure AI services from a Container**:
After your Azure AI services container is deployed, applications consume the containerized Azure AI services endpoint
 rather than the default Azure endpoint. The client application must be configured with the appropriate endpoint for 
 your container, but does not need to provide a subscription key to be authenticated. You can implement your own 
 authentication solution and apply network security restrictions as appropriate for your specific application scenario.

--------------------------------------------------------------------------------------------------------------------------
Detect, analyze, and recognize faces 
--------------------------------------------------------------------------------------------------------------------------
There are two Azure AI services that you can use to build solutions that detect faces or people in images.

**Azure AI Vision service**: This service enables you to detect people in an image, as well as returning a bounding box 
for its location

**Face service**: This service offers more comprehensive facial analysis capabilities than the Azure AI Vision service, 
including:
- Face detection (with bounding box).
- Comprehensive facial feature analysis (including head pose, presence of spectacles, blur, facial landmarks, occlusion 
and others).
- Face comparison and verification.
- Facial recognition.

--------------------------------------------------------------------------------------------------------------------------
Azure AI Vision
--------------------------------------------------------------------------------------------------------------------------
Azure AI provides two different features that read text from documents and images, one in the Azure AI Vision Service, the 
other in Azure AI Document Intelligence. There is overlap in what each service provides, however each is optimized for 
results depending on what the input is.

**Image Analysis Optical character recognition (OCR)**: 
- Use this feature for general, unstructured documents with smaller amount of text, or images that contain text.
- Results are returned immediately (synchronous) from a single API call.
- Has functionality for analyzing images past extracting text, including object detection, describing or categorizing an 
image, generating smart-cropped thumbnails and more.
- Examples include: street signs, handwritten notes, and store signs.

**Document Intelligence**:
- Use this service to read small to large volumes of text from images and PDF documents.
- This service uses context and structure of the document to improve accuracy.
- The initial function call returns an asynchronous operation ID, which must be used in a subsequent call to retrieve the 
results.
- Examples include: receipts, articles, and invoices.

You can access both technologies via the REST API or a client library. In this module, we'll focus on the OCR feature in 
Image Analysis

--------------------------------------------------------------------------------------------------------------------------
Read API
--------------------------------------------------------------------------------------------------------------------------
To use the Read OCR feature, call the ImageAnalysis function (REST API or equivalent SDK method), passing the image URL or 
binary data, and optionally specifying a gender neutral caption or the language the text is written in (with a default 
value of en for English).

To make an OCR request to ImageAnalysis, specify the visual feature as READ.

**Python**:
```
    result = client.analyze(
        image_url=<image_to_analyze>,
        visual_features=[VisualFeatures.READ]
    )

```
If using the REST API, specify the feature as read.
```
    https://<endpoint>/computervision/imageanalysis:analyze?features=read&...
```    

The results of the Read OCR function are returned synchronously, either as JSON or the language specific object of a 
similar structure. These results are broken down in blocks (with the current service only using one block), then lines,
 and then words. Additionally, the text values are included at both the line and word levels, making it easier to read 
 entire lines of text if you don't need to extract text at the individual word level.    

--------------------------------------------------------------------------------------------------------------------------