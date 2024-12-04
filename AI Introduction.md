# AI Introduction

## Overview

|Term|Notes|
|-|-|
|**Artificial Intelligence (AI)**|A broad field aimed at creating machines that can perform tasks requiring human intelligence, including problem-solving, decision-making, and task execution.|
|**Machine Learning (ML)**|A subfield of AI where models are trained using data and algorithms to make predictions or decisions without explicit programming for each specific task.|
|**Deep Learning/Neural Nets**|A subfield of ML utilizing multi-layered neural networks to perform complex tasks such as image classification and speech recognition with high accuracy.|

|Artificial Intelligence|Generative AI|Artificial General Intelligence (AGI) or General AI|
|-|-|-|
|**Definition**|Creates data resembling its training|Possesses human-like cognitive abilities|
|**Examples**|Generative Adversarial Networks, Large Language Models (e.g., GPT models)|Theoretical, depicted in science fiction|
|**Capabilities**|||
|Data Creation|Generates synthetic data|Broad understanding without specific training|
|Content|Produces art, music, writing|Adapts to new tasks easily|
|Language|Understands and generates human text|Learns autonomously|
|Simulations|Creates realistic digital environments||	
|**Challenges**||
|Quality Control|Ensuring consistent, high-quality output|Building a comprehensive cognitive model|
|Bias|Mitigating biases from training data|Ensuring safe behavior|
|Resources|Requires significant computational power|Managing ethical and societal impacts|
|**Current State**|Practical applications (ChatGPT, Bard)|Mostly theoretical, still a distant goal|
|**Impact**|Advances in problem-solving and creativity|Aspirational vision of human-like intelligence|

### Machine Learning

**Machine Learning Algorithms**: Programs that adjust their performance based on data exposure and feedback, improving their accuracy and efficiency in tasks like image recognition and natural language processing.

|Machine Learning Type|Notes|Examples|
|-|-|-|
|**Supervised Learning**|Uses labeled data where each input is associated with a correct output<br>Predicts outcomes for new data based on training<br>Ideal for classification and regression tasks|Classification: Linear classifiers, decision trees<br>Regression: Linear regression, logistic regression|
|**Unsupervised Learning**| Analyzes unlabeled data to find hidden patterns<br>No human intervention needed for labeling data|Clustering: K-means clustering, hierarchical clustering<br>Association: Apriori algorithm, market basket analysis|
|**Semi-Supervised Learning**|Combines techniques from supervised and unsupervised learning for scenarios with limited labeled data and abundant unlabeled data|Generative Adversarial Network (GAN)|
|**Reinforcement Learning**|Agent learns to interact with an environment through trial and error<br>Receives rewards or penalties based on actions<br>Learns optimal actions to maximize cumulative rewards|AlphaGo: Learned to play Go at a world-champion level|

### Deep Learning

* Deep Learning is an advanced subset of machine learning that relies on neural networks, which are computational models inspired by the human brain. Neural networks consist of layers of interconnected nodes (neurons) that process data. The "deep" in deep learning refers to the multiple layers within these networks. Deep learning is particularly effective for complex tasks such as image classification and speech recognition. In practice, deep learning models are trained on vast amounts of data to perform specific tasks, like recognizing objects in images or translating spoken language in real time. These neural networks are implemented on specialized hardware to handle the intensive computations required.
* Being a subset of machine learning, deep learning holds certain similarities to the broader concept such as the need for datasets and algorithms. However, it goes one step further in its analytical abilities by utilising various layers of neural networks. Deep learning algorithms typically utilise 3 or more layers in an artificial neural network. **Example: The largest GPT-3 model (175B) uses 96 attention layers.**

|Components of Neural Networks|How It Works|Industry Applications|Limitations|
|-|-|-|-|
|**Data inputs:** Data that you wish to process<br> **Weights:** Determine the importance of each input on the outcome<br>**Biases:** Represents the amount of assumptions on output<br>**Activation functions:** Determine whether the data will be transferred to the next layer<br>**Outputs:** Decisions made by the deep learning program|1. Data process through weighted channels and neuroses containing bias<br>2. The neuron may or may not be activated based on the activation function<br>3. If activated, data will process to the next layer<br>4. Procsess repeats until on output is produced<br> **Does not require human intervention to learn from mistakes.**|1. Google DeepMind’s AlphaGo program<br>2. Amazon Alexa<br>3. Self-driving Vehicles<br>4. Predicting earthquakes<br>5. Adding sounds to silent movies<br>|Requires significant time<br>Requires GPUs and vast computing power|

### Key Differences Between Machine Learning And Deep Learning

|Compare|Machine Learning|Deep Learning|
|-|-|-|
|Approach|Requires structured data|Rely on neural networks to process data|
|Human Intervention|Requires human intervention for mistakes|Neural networks are capable of learning from their mistakes|
|Hardware|Can function on CPUs|Requires GPUs and significant computing power|
|Time|Takes seconds to hours|typically requires weeks|
|Uses|Forecasting and predicting and other simple application|More complex application like autonomous vehicles|

### AI vs ML vs DL

|Artificial Intelligence|Machine Learning|Deep Learning|
|-|-|-|
|AI is a set of techniques and processes for machines to imitate human behavior. Both ML and DL are used to develop an AI application.|ML is a subspace of AI and is used to process large amounts of data and predict future events.|DL uses neural networks, where a bunch of nodes or artificial neurons try to solve a problem in ways similar to that of biological neurons.|
|AI systems replicate human behavior and solve problems like missionaries and cannibals, the Bayes theorem, the shortest path, etc.|ML inherits symbolic approaches from AI and uses models, statistics, and probability theories to make data-driven decisions.|DL provides a multi-level abstraction, which makes it easier to train models without depending on specific algorithms.|
|AI requires high-end computational devices to simulate the desired output.|ML can work with smaller datasets, thereby reducing the need for high-end graphics and computer systems.|DL requires high-end systems as the performance of the models highly depends on the amount of data fed in.|
|AI takes a long time to train a machine and make it capable enough to produce impeccable results.|ML takes much less time to train, ranging from a few hours to a day.|DL models a take longer time than ML models as they have so many parameters to take into consideration.|
|Interpretability depends on implementation methods used to solve a particular problem.|It is easy to interpret the final results as ML uses decision trees that have rules for what and how it chooses.|In DL, it is hard to interpret the final result.|

---

## Artificial Neural Network (ANN)

|Component/Process|Notes|
|-|-|
|**Input Layer**|The initial layer that receives input data, which could be features from a dataset. The input layer receives raw data or features from the input source.|
||The input layer does not process data; it simply passes the data to the next layer. There are no weights associated with the input layer itself; weights are applied in the connections between the input layer and the hidden layers.|
|**Hidden Layers**|These intermediate layers process data and learn intricate patterns. A neural network can consist of multiple hidden layers, making it “deep” (Deep Neural Network, or DNN).|
||In the hidden layers, each neuron processes the weighted sum of inputs and biases using an activation function. The activation function introduces non-linearity, allowing the network to capture complex patterns. The hidden layers play a crucial role in feature extraction and transformation.|
|**Weights and Biases Adjustment**|During the learning phase, the network adjusts weights and biases through a process called backpropagation. It compares the network’s output to the desired output, calculates the error, and adjusts weights to minimize this error.|
||Backpropagation involves calculating the gradient of the error with respect to each weight by the chain rule, iteratively updating the weights to minimize the error using optimization techniques such as gradient descent.|
|**Output Layer**|The final layer that produces the network’s prediction or output. The processed information propagates through the hidden layers to the output layer. The output layer provides the final prediction or classification result.|
||The nature of the output layer depends on the task: for classification, it might use a softmax activation function to output probabilities, while for regression tasks, it might use a linear activation function.|
|**Training**|The network iteratively updates weights and biases using training data to minimize the prediction error. This process fine-tunes the network’s ability to make accurate predictions.|
||Training involves feeding the network with a large amount of labeled data, calculating the error for each prediction, and updating the weights accordingly. This process is repeated over many epochs until the network performs satisfactorily on the training data.|
|**Prediction**|Once trained, the network can process new, unseen data and generate predictions or classifications based on the patterns it has learned.|During the prediction phase, the trained network uses the learned weights and biases to process new inputs and produce outputs. The network's performance on unseen data is often evaluated using separate validation and test datasets.|

|Types of Artificial Neural Network|Applications|
|-|-|
|**Feedforward Neural Networks (FNN)**|Information flows from the input to the output layer without cycles.Commonly used in tasks like image recognition, classification, and regression.|
|**Convolutional Neural Networks (CNN)**|Primarily used for image analysis, CNNs use specialized layers such as convolutional and pooling layers to automatically detect and learn spatial hierarchies of features in images.|
|**Generative Adversarial Networks (GAN)**|Consisting of a generator and a discriminator, GANs are used for tasks like image generation, style transfer, and data augmentation. The generator creates data, while the discriminator evaluates its authenticity.|
|**Recurrent Neural Networks (RNN)**|Connections form cycles, allowing feedback loops. Suitable for tasks involving sequences, such as language processing, time series prediction, and speech recognition.|
|**Long Short-Term Memory Networks (LSTM)**|A type of RNN, LSTMs are designed to handle long-term dependencies and sequence data, known for their ability to remember information for extended periods. Commonly used in tasks like language modeling and machine translation.|
|**Transformer**|The Transformer model is a deep learning model that adopts a self-attention mechanism, primarily used in Natural Language Processing (NLP) and increasingly in Computer Vision (CV). It allows for the handling of long-range dependencies more effectively than RNNs. **Introduced in the paper "[Attention Is All You Need](https://arxiv.org/abs/1706.03762)" by Google in 2017.**|

### Generative Pre-trained Transformers (GPT)

* GPTs are based on the transformer architecture, pre-trained on large datasets of unlabeled text, and capable of generating novel human-like content. As of 2023, most large language models share these characteristics and are often referred to broadly as GPTs.
* **In November 2022, OpenAI launched ChatGPT**, an online chat interface powered by an instruction-tuned language model. This model was trained similarly to InstructGPT, utilizing **Reinforcement Learning from Human Feedback (RLHF)**. Human AI trainers conducted conversations by playing both the user and the AI, combining this new dialogue dataset with the InstructGPT dataset to create a conversational format suitable for a chatbot.
* Microsoft's Bing Chat: Uses OpenAI's GPT-4 as part of a broader close collaboration between OpenAI and Microsoft.
* Google's Bard: Initially based on Google's LaMDA family of conversation-trained language models, with plans to transition to their PaLM models.

---

## Large Language Models

Large Language Models, focus on linguistic data and can be built upon architectures like RNNs or transformers (as in the case of GPT and BERT).

* **GPT-3.5, it was trained using a massive dataset containing 500 billion tokens, and it consists of 175 billion parameters.** This model can understand and generate text based on the patterns it learned during training.
* **Parameters**: Think of parameters as the pieces of information the model learns during its training phase. They're like the building blocks that help the model understand language and generate responses. These parameters are adjusted and fine-tuned through a process called training, where the model learns from a large dataset of text.
* **Tokens:** Tokens are the basic units of language that the model works with. In simple terms, you can think of them as words, punctuation marks, or even parts of words. For example, in the sentence "The cat is sleeping," each word ("The," "cat," "is," "sleeping") is a token. But tokens can also represent parts of words or special characters, like prefixes or suffixes.

### Mathematical formula metaphorically decribing parameters in a model

* Total Parameters = (Ingredients + Cooking Techniques) × Complexity Level Ingredients
* Just like in a recipe, different ingredients represent different aspects of language learning, such as vocabulary, grammar rules, context understanding, etc. Cooking Techniques: These represent the methods used to combine and process the ingredients, akin to the algorithms and training processes used in building the language model. Complexity Level: This factor represents how intricate and nuanced the final dish (or text generation) needs to be. More complex dishes require more ingredients and advanced cooking techniques. So, the total number of parameters in a language model can be seen as a result of combining various ingredients with specific cooking techniques, all tailored to achieve a certain level of linguistic complexity.

### Let's use a metaphorical math formula to describe the parameters in an investment expert model: 

* **Total Parameters = (Financial Data + Analytical Algorithms) × Risk Appetite Financial Data:**
* Just like in investing, different types of financial data serve as the raw ingredients for analysis, including stock prices, company financial reports, market trends, etc. Analytical Algorithms: These represent the mathematical models and algorithms used to process and analyze the financial data, such as regression analysis, machine learning models, sentiment analysis, etc. Risk Appetite: This factor represents the investor's willingness to take on risk. It influences the complexity and depth of analysis required, as well as the types of investments recommended. So, the total number of parameters in an investment expert model can be seen as a result of combining financial data with analytical algorithms, all tailored to match a particular investor's risk appetite and investment goals.

### An example for temprature

        import openai
    
        # Set your OpenAI API key
        openai.api_key = 'your-api-key-here'

        # Define the function to send a request to the OpenAI API
        def get_response_from_llm(prompt, model="text-davinci-003", max_tokens=150, temperature=0.7):
        
        response = openai.Completion.create(
        engine=model,
        prompt=prompt,
        max_tokens=max_tokens,
        n=1,
        stop=None,
        temperature=temperature
        )
        return response.choices[0].text.strip()

        # Example prompt
        prompt = "Please provide 5 advices of activities for Valentine's Day"

        # Get the responses
        response_low_temp = get_response_from_llm(prompt, temperature=0.2)
        
        response_high_temp = get_response_from_llm(prompt, temperature=2.0)

        # Print the responses
        print("Response with Low Temperature (0.2):")
        print(response_low_temp)
        print("\nResponse with High Temperature (2.0):")
        print(response_high_temp)

|Advice Activity|Low Temperature (0.2)|High Temperature (2.0)|
|-|-|-|
|Dinner|Have a romantic dinner at your favorite restaurant.|Host a surprise masquerade ball in your living room.|
|Outdoor Activity|Take a walk in a nearby park or along the beach.|Explore an abandoned building and create an urban adventure.|
|Creative Writing|Write love letters to each other.|Write and perform a love song together on the street.|
|Movie Night|Watch a romantic movie together.|Watch a foreign film without subtitles and make up your own dialogue.|
|Stargazing/Camping|Spend the evening stargazing.|Spend the night camping on the roof and making shadow puppets.|

### Large Language Models application customization engineering

|Method|Definition|Primary use case|Data requirements|Advantages|Considerations|
|-|-|-|-|-|-|
|Pre-training|Training a LLM from scratch|Unique tasks or domain-specific corpora|Large datasets (billions to trillions of tokens)|Maximum control, tailored for specific needs|Extremely resource-intensive|
|Fine-tuning|Adapting a pretrained Large Language Models to specific datasets or domains|Domain or task specialization|Thousands of domain-specific or instruction examples|Granular control, high specialization|Requires labeled data, computational cost|
|Prompt engineering|Crafting specialized prompts to guide Large Language Models behavior|Quick, on-the-fly model guidance|None|Fast, cost-effective, no training required|Less control than fine-tuning|
|**Retrieval augmented generation (RAG)**|Combining a LLM with external knowledge retrieval|**Dynamic datasets and external knowledge**|External knowledge base or database (e.g., vector database)|Dynamically updated context, enhanced accuracy|Increases prompt length and inference computation|

### Pre-training, fine-tuning and inferencing

|Compare|Pre-training|Fine-tuning|Inferencing|
|-|-|-|-|
|Objective|Train a model on a large dataset to learn general features and patterns|Further train a pre-trained model on a smaller dataset to adapt to a specific task or domain|Apply the trained model to new data to make predictions or generate outputs|
|Dataset|Large, diverse dataset|Smaller, task-specific dataset|New, unseen data|
|Training Time|Can take days to weeks|Usually shorter, from hours to days|Near real-time or batch processing|
|Resource Usage|High computational and memory resources|Less computational resources compared to pre-training|Requires less computational resources|
|Tunability|Generalizes across tasks and domains|Task-specific fine-tuning|Limited to the capabilities learned during pre-training|
|Performance|Higher potential for generalization|Improved performance on specific task or domain|Depends on the quality of pre-training and fine-tuning|
|Use Cases|Initial model development|Adapting to new tasks or domains|Making predictions or generating outputs|
|Metaphorical|Like learning various basic cooking techniques and knowledge when you start cooking.|Like specializing in French cuisine, delving deeper into related professional skills.|Like using your knowledge to prepare and serve a delicious crème brûlée.|

### RLHF (Reinforcement Learning from Human Feedback)

It is a technique used to train AI models, particularly in situations where the task is too complex for the cost function to be defined explicitly, or where human judgment is a critical component. RLHF incorporates human feedback into the reinforcement learning cycle to guide the model toward desired outcomes.

* **Step 1. Pre-training:** The model is pre-trained on a large dataset with supervised learning to initialize its parameters with a broad understanding of the world.
* **Step 2. Fine-tuning with human feedback:** Human trainers review and score the model’s outputs or compare different outputs, which is used to create a reward model. This feedback helps define what good model behavior looks like.
* **Step 3. Proximal Policy Optimization (PPO):** This is a deep reinforcement learning algorithm used to optimize the model’s policy (i.e., the way it behaves or decides on actions), trying to maximize the expected human-generated rewards.
* **Iteration:** Steps 2 and 3 are repeated, with human feedback collected at each step to constantly refine the reward model and improve the policy.

**OpenAI** has implemented RLHF in training some of its most advanced language models. For instance, models such as GPT-3.5, which is an iteration on GPT-3, and ChatGPT, a variant of GPT-3 specially fine-tuned for generating conversational text, have been trained using variations of the RLHF process. In these models, the RLHF technique is used to align the models’ responses more closely with human values and preferences, thus making them more useful and safer in practice.

Here's an example of how RLHF could be implemented using Python, TensorFlow (a popular machine learning framework), and a simple interactive user interface.

    import tensorflow as tf

    # Define the text generation model (for demonstration purposes, a simple LSTM model)
    class TextGenerationModel(tf.keras.Model):
        def __init__(self):
            super(TextGenerationModel, self).__init__()
            self.embedding = tf.keras.layers.Embedding(vocab_size, embedding_dim)
            self.lstm = tf.keras.layers.LSTM(units)
            self.output_layer = tf.keras.layers.Dense(vocab_size, activation='softmax')

        def call(self, inputs):
            x = self.embedding(inputs)
            x = self.lstm(x)
            return self.output_layer(x)

    # Initialize the text generation model
    model = TextGenerationModel()

    # Define functions for collecting and processing user feedback
    def collect_feedback(user_input, generated_output):
        # Simulate collecting user feedback, for example, through a user interface
        feedback = input("Was the generated response appropriate? (yes/no): ")
        return feedback.lower() == "yes"

    # Update model parameters based on feedback (not implemented in this example)
    # This could involve retraining the model with user-provided correct responses.
    def process_feedback(feedback, user_input, generated_output):
        if feedback:
            print("Great! Model generated a correct response.")
        else:
            print("Oops! Model needs improvement.")

    # Main loop for generating responses and collecting feedback
    
    while True:
        user_input = input("Enter your query: ")
    
        # Generate response using the model
        generated_output = model.generate_response(user_input)
        print("Generated response:", generated_output)
    
        # Collect user feedback
        feedback = collect_feedback(user_input, generated_output)
    
        # Process feedback and update model
        process_feedback(feedback, user_input, generated_output)

* We define a simple text generation model using TensorFlow.
* We simulate collecting user feedback through a simple command-line interface where the user can provide feedback ("yes" or "no") on whether the generated response was appropriate.
* Based on the feedback, we can further process and potentially update the model parameters (not implemented in this example).
* The loop continues indefinitely, allowing for iterative improvement of the model based on user feedback.

---

## Build and deploy an AI model

|Stage|Process|
|-|-|
|**Data Collection**|This is the process of gathering relevant data from various sources. It's crucial to have high-quality and representative data to train a machine learning model effectively.|
|**Training**|In this step, the collected data is used to train a machine learning model. The model learns patterns and relationships from the data during this training phase.|
|**Conversion**|Once the model is trained, it often needs to be converted into a format suitable for deployment on the target platform. This might involve converting it to a more efficient runtime format or optimizing it for inference speed.|
|**Inferencing**|This is the stage where the trained model is used to make predictions or decisions on new, unseen data. Inferencing involves feeding new data into the trained model and obtaining predictions or classifications based on the learned patterns.|
|**Deployment**|After the model has been trained and converted (if necessary), it's deployed into production where it can be used to make real-world predictions or decisions. Deployment involves integrating the model into the target environment, whether that's a web application, a mobile app, an IoT device, or some other system.|

**Let's walk through an example of building an AI investment expert.**
|Stage|Process|
|-|-|
|Data Collection|Collect financial data from various sources such as stock prices, company financial reports, economic indicators, news articles, and social media sentiment. For example, gather historical stock price data from financial databases like Yahoo Finance, company financial reports from sources like SEC filings, and news articles from financial news websites.|
|Training|Train a machine learning model to predict stock prices or make investment recommendations. Use techniques like regression for price prediction or classification for buy/sell recommendations.The model would learn patterns and relationships from the historical data, such as correlations between stock prices and various factors like earnings reports, market sentiment, or economic indicators.|
|Conversion|It might need to be converted into a format suitable for deployment. This could involve optimizing the model for speed and efficiency, especially if it's going to be deployed in a real-time trading environment.Depending on the deployment platform, you might need to convert the model into a format compatible with the target system, such as TensorFlow Lite for mobile devices or ONNX for edge devices.|
|Inferencing|The trained model is used to make predictions on new data. For an investment expert, this would involve feeding in current market data and obtaining predictions on which stocks to buy or sell. The model might analyze real-time market data such as current stock prices, company news, economic indicators, and social media sentiment to make its predictions.|
|Deployment|Once the model is trained and converted, it's deployed into production where it can be used to assist with investment decisions.This could involve integrating the model into a trading platform, a financial app, or an investment advisory service. Users could interact with the AI investment expert through a user interface, receiving recommendations on which stocks to trade based on the model's predictions.|

|Stage|Possible methods|
|-|-|
|Data Collection|Python libraries such as Pandas, NumPy, and BeautifulSoup could be used for data manipulation and web scraping. APIs provided by financial data providers like Alpha Vantage, Yahoo Finance, or Quandl can be utilized to access historical stock prices and other financial data.|
|Training|Popular machine learning frameworks like TensorFlow or PyTorch can be used for building and training the model.Libraries such as scikit-learn can provide implementations of various machine learning algorithms for regression or classification tasks. Jupyter Notebooks can be used for interactive development and experimentation.|
|Conversion|Tools like TensorFlow Serving or ONNX Runtime can be used to convert and serve machine learning models in production environments. TensorFlow Model Optimization Toolkit can be used to optimize and compress models for deployment, reducing their size and improving inference speed.|
|Inferencing|Depending on the deployment environment, inference can be performed on cloud platforms, edge devices, or mobile devices. If deploying to edge devices or mobile devices, tools like TensorFlow Lite Converter can be used to convert models to formats optimized for inference on resource-constrained devices.|
|Deployment|Web frameworks like Flask or Django can be used to build RESTful APIs for serving model predictions to clients. Docker containers can be used to package the application and its dependencies, making it easy to deploy and manage across different environments. Kubernetes can be used for container orchestration in production environments.|

---

## How to Use AI Tools to Boost Your Productivity

### Promprt Engineering

* **Prompt, Refine, Repeat**, if your initial prompt doesn’t return the result you were looking for, let the AI know, specifically, how it can improve.
* [Promprt Engineering](https://www.promptingguide.ai/)

### Using AI for Day-to-Day Tasks

* Task Management
* Brainstorming
* Research Assistance
* Writing Support
* Language Learning
* Language Correction and Translation
* Time Management
* Skill Development
* Personal Reflection
* Decision Making
* Coding-related tasks
* Relaxation and Mindfulness

### Create hand-drawn like diagrams with AI

* ChatGPT
* Mermaid code (A JavaScript-based tool to connect the prompt and Excalidraw)
* Excalidraw (It supports flowchart, sequence diagram and class diagram.)
* Step 1: Ask ChatGPT to create description for the logic tree.
* Step 2: Ask ChatGPT to generate Mermaid code.
* Step 3: Generate the diagram in Excalidraw.

### Efficiency in Streamlining Content Creation and Documentation

* ChatGPT
* VScode (Markdown extensions available)
* Browser
* Step 1: Ask ChatGPT to create description.
* Step 2: Ask ChatGPT to generate Markdown code.
* Step 3: Copy and paste it your Markdown document within VSCode.
* Step 4: Export it to a HTML file.

### Excel Skills with ChatGPT

* Data Analysis
* Troubleshooting
* Formulas and Functions
* Data Cleaning
* Automation
* Visualization
* Excel Tips and Tricks

### Use Keywords

* Please **list** the famous Hollywood actors **in table**.
* Please use **Markdown** to illustrate the information above.
* Please use **H1, H2**, and **bold formatting to summarize.**
* Please translate them into Chinese.
