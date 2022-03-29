# Exam AI-900: Microsoft Azure AI Fundamentals

## Describe Artificial Intelligence workloads and considerations (15-20%)

### Identify features of common AI workloads
- [ ] identify prediction/forecasting workloads
    - **Prediction:**
        - Prediction and demand forecasting (relationship between visitors and sales)
        - Text prediction in Google search
        - Video streaming predicting what you would like to see next
        - Product recommendations on e-commerce site       

    | Forecasting | Prediction |
    |-------------|------------|
    | Subset of prediction problems | A broad category of machine learning |
    | Explicit introduction of time | Not necessarily time based | 
    | Forecast weather | Prediction problems used with economics |
    | Scientific, free from bias | Judgemental, biased, subjective |
    
- [ ] identify features of anomaly detection workloads
    - **Anomaly Detection :**
        - More complicated form of prediction
        - Events that fall outside of boundaries
    - Batch or real-time API
    - Detect anomalies in data with time series
        
- [ ] identify computer vision workloads
    - **Computer Vision :**
        - Face detection (with approximate ages and assumed genders)
        - Scene \ object detection. Ex: Returning a bounding box that indicates location of a vehicle in an image.
      
- [ ] identify natural language processing or knowledge mining workloads
    - **NLP (Natural Language Processing) :**
        - Understanding sentence structure
        - Inferring what question is asking
        - Knowledge Mining - Cognitive Search :
            - Related to the above.
            - Searching through multiple media types and find organization and indexing in the clutter.
           
- [ ] identify conversational AI workloads
    - **Conversational AI - Chat Bots**


### Identify guiding principles for responsible AI
- Videos from Microsoft about their AI guiding principles -> [Video Link](https://www.microsoft.com/en-us/ai/responsible-ai?activetab=pivot1%3aprimaryr6)

    ![Responsible AI](./images/responsible-ai.svg)

- [ ] describe considerations for **fairness** in an AI solution
    - Fundamentally a "sociotechnical" challenge
    - Require greater diversity in people creating and deploying AI solutions
    - Ultimately *reduce bias* in how AI treats people of all backgrounds
- [ ] describe considerations for **reliability and safety** in an AI solution
    - Resistant to harmful manipulations
    - Bbe safe for users
    - Consistent operation
    - Consider how to handle unusual or missing values.
- [ ] describe considerations for **privacy and security** in an AI solution
    - Provide users information and controls over the collection, storage and use of their data.
- [ ] describe considerations for **inclusiveness** in an AI solution
    - AI system that empowers everyone, including people who have hearing, visual, and other impairments.
- [ ] describe considerations for **transparency** in an AI solution
    - Transparency helps understand the data and algorithms used to train a model, data transformation logic, etc.
    - Make the model explainable.
    - Auto ML has *model explain ability*, we enable you to understand feature importance as part of automated ML runs.
- [ ] describe considerations for **accountability** in an AI solution
    - How can you use a human-led approach to drive value for your business?
    - How will your organization’s foundational values affect your approach to AI?
    - How will you monitor AI systems to ensure they are evolving responsibly?

## Describe fundamental principles of machine learning on Azure (30-35%)

### Identify common machine learning types
- [ ] identify regression machine learning scenarios
    - Predicted vs. True shows the relationship between a predicted value and its correlating true value for a regression problem.
- [ ] identify classification machine learning scenarios
- [ ] identify clustering machine learning scenarios

### Describe core machine learning concepts
- [ ] identify features and labels in a dataset for machine learning

    - **Features**: Data values that influence prediction of a model.
        - Example: if predicting fares of taxi trips, could use things like distance travelled or length of time in taxi as features.
    - The *Split Data module* is particularly useful when you need to separate data into training and testing sets. Use the Split Rows option if you want to divide the data into two parts. You can specify the percentage of data to put in each split, but by default, the data is divided 50-50.
    - [*Feature engineering*](https://docs.microsoft.com/en-us/azure/machine-learning/team-data-science-process/create-features) is used to generate additional features.

- [ ] describe how training and validation datasets are used in machine learning

    - **Unvupervised Learning** : Ability to find patterns in data without human help.
    - **Supervised Learning** : Humans label the data and give general guidance.

- [ ] describe how machine learning algorithms are used for model training
- [ ] select and interpret model evaluation metrics for classification and regression

### Identify core tasks in creating a machine learning solution
- [ ] describe common features of data ingestion and preparation
- [ ] describe feature engineering and selection
- [ ] describe common features of model training and evaluation
- [ ] describe common features of model deployment and management

### Describe capabilities of no-code machine learning with Azure Machine Learning studio
- [ ] automated ML UI

    - [**Confusion matrices**](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-understand-automated-ml#confusion-matrix) provide a visual for how a machine learning model is making systematic errors in its predictions for classification models. The word "confusion" in the name comes from a model "confusing" or mislabeling samples.
        - Identifies how many times evaluated results differ from expected labels
        - Confusion matrix for a good model would show most results along the diagonal (ie most evaluations == expected labels).
        - In a *binary classification* algorithm, the concept of false negatives, true positives, true negatives and false positives exists.
            - Where the algo predicts a positive (1) and the actual is also positive (1) then it is a true positive.
            - if predicts negative (0) and actual is positive (1) then it is a false negative (falsely predicting negative).
            - if predicts positive and actual negative, then false positive.
            - if predicts negative and actual negative, then true negative.
            - [See this article](https://docs.microsoft.com/en-us/previous-versions/azure/machine-learning/classic/evaluate-model-performance#inspecting-the-evaluation-results-1).

- [ ] azure Machine Learning designer


## Describe features of computer vision workloads on Azure (15-20%)

### Identify common types of computer vision solution:
- [ ] identify features of image classification solutions
- [ ] identify features of object detection solutions
- [ ] identify features of optical character recognition solutions
- [ ] identify features of facial detection, facial recognition, and facial analysis solutions

    - [**Face Service**](https://docs.microsoft.com/en-us/azure/cognitive-services/face/overview) : provides AI algorithms that detect, recognize, and analyze human faces in images.
        - Examples:
            - Identity verification
            - Touchless access control
            - Face redaction
        - Returns rectangle coordinates of faces locations. Also returns unique ID that represents stored face data.
            - Optionally can extract set of face-related attributes : head pose, age, emption, facial hair and glasses.
        - Use for face identification or face matching (verification)

### Identify Azure tools and services for computer vision tasks
- [ ] identify capabilities of the Computer Vision service

    - A specific resource for the Computer Vision service.
    - Returns bounding box, image class name and probability score
    - The **OCR API** is designed for quick extraction of small amounts of text in images.
    - [The **Read API**](https://westus.dev.cognitive.microsoft.com/docs/services/computer-vision-v3-2/operations/5d986960601faab4bf452005):
        - For text-heavy images and multi-page, mixed language, and mixed type documents.
        - Asynchronous
        - Supports numerous image types
        - The file size must be less than 50 MB
        - Supports 164 languages for print text and 9 languages for handwritten
    
- [ ] identify capabilities of the Custom Vision service

    - Azure Custom Vision is an image recognition service that lets you build, deploy, and improve your own image identifier models.
    - Unlike the Computer Vision service, Custom Vision allows you to specify your own labels and train custom models to detect them.
    - 2 categories
        1. Object detection
        2. Image classification
    - To use, requires prediction key, endpoint, model name and project id

- [ ] identify capabilities of the Face service
- [ ] identify capabilities of the Form Recognizer service


## Describe features of Natural Language Processing (NLP) workloads on Azure (15-20%)

### Identify features of common NLP Workload Scenarios
- [ ] identify features and uses for key phrase extraction
- [ ] identify features and uses for entity recognition
- [ ] identify features and uses for sentiment analysis
- [ ] identify features and uses for language modeling
- [ ] identify features and uses for speech recognition and synthesis
- [ ] identify features and uses for translation

### Identify Azure tools and services for NLP workloads
- [ ] identify capabilities of the Text Analytics ([Language](https://docs.microsoft.com/en-us/azure/cognitive-services/language-service/)?) service

    - Classify text, sentiment analysis, language detection, key phrases
    - Sentiment analysis : scores between 0.0 (negative) and 1.0 (positive sentiment). 
- [ ] identify capabilities of the Language Understanding service (LUIS)
    - Superseded by Cognitive Services Language?
    - 4 types of entities can be created:
        - Machine Learned
        - Regex
        - Pattern.any
        - List
    - Also capable of sentiment analysis
- [ ] identify capabilities of the Speech service
- [ ] identify capabilities of the Translator Text service


## Describe features of conversational AI workloads on Azure (15-20%)

### Identify common use cases for conversational AI
- [ ] identify features and uses for webchat bots

    - Examples :
        - Webchat for customer support. Reduces customer support call volume to support persons.

- [ ] identify common characteristics of conversational AI solutions

### Identify Azure services for conversational AI
- [ ] identify capabilities of the QnA Maker service
- [ ] identify capabilities of the Azure Bot service
    - Bot service [**skills**](https://microsoft.github.io/botframework-solutions/overview/skills/) can be used to extend capabilities of the bot
