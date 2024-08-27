# Understanding LLMs: A Comprehensive Overview from Training to Inference

* [Source:](https://arxiv.org/abs/2401.02038) *A Comprehensive Overview from Training to Inference*

## Introduction

* The primary objective of this paper is to provide a comprehensive overview of LLMs training and inference techniques to equip researchers with the knowledge required for developing, deploying, and applying LLMs.
* [Section 2](https://github.com/AlleninTaipei/Artificial-Intelligence-Introduction-for-Beginners/blob/main/A%20Comprehensive%20Overview%20from%20Training%20to%20Inference.md#background-knowledge), will introduce the relevant background and foundational knowledge of LLMs.
* [Section 3](https://github.com/AlleninTaipei/Artificial-Intelligence-Introduction-for-Beginners/blob/main/A%20Comprehensive%20Overview%20from%20Training%20to%20Inference.md#training-of-large-language-models-llms), will delve into the technical aspects of training LLMs.
* [Section 4](https://github.com/AlleninTaipei/Artificial-Intelligence-Introduction-for-Beginners/blob/main/A%20Comprehensive%20Overview%20from%20Training%20to%20Inference.md#inference-with-large-language-models), will explore the technologies related to LLM’s inference and deployment.
* [Section 5](https://github.com/AlleninTaipei/Artificial-Intelligence-Introduction-for-Beginners/blob/main/A%20Comprehensive%20Overview%20from%20Training%20to%20Inference.md#utilization-of-llms), will discuss the utilization of LLMs.
* [Section 6](https://github.com/AlleninTaipei/Artificial-Intelligence-Introduction-for-Beginners/blob/main/A%20Comprehensive%20Overview%20from%20Training%20to%20Inference.md#future-directions-and-implications), will explore the future directions and their implications for LLMs.

## Background Knowledge

|Transformer|Introduced in 2017, replaced the traditional recurrent neural network (RNN) architecture in machine translation tasks and became the state-of-the-art model. The core components are the Encoder, the Decoder, and the attention mechanism within these modules.|
|-|-|
|**Self-Attention**|Self-attention helps the model focus on important parts of the input data by weighing the relevance of different words in a sequence. Involves calculating query, key, and value vectors for words, and using these to determine attention weights through a softmax function. Multi-head attention extends this mechanism by performing multiple self-attention operations in parallel, capturing various aspects of input.|
|**Encoder**|Composed of multiple identical layers with multi-head attention and feed-forward neural networks. Captures dependencies between different positions in the input sequence and extracts features through layer stacking.|
|**Decoder**|Similar to the encoder but includes an additional encoder-decoder attention mechanism. Uses masks to ensure the generation process adheres to grammar rules by focusing only on past and current positions, not future ones.|
|**Positional Embedding**|Transformers lack inherent position/order sense, which is addressed by positional embeddings. Two main types: Absolute Positional Encoding (using sine and cosine functions) and Relative Positional Encoding (focusing on distances between words). Methods like RoPE and ALiBi further enhance positional encoding by representing relative positions and adding bias to attention scores, respectively.|

|Prompt Learning|Notes|
|-|-|
|**Background and Overview**|A machine learning approach used in NLP to guide pre-trained models to perform specific tasks through carefully designed prompts. Replaces the pre-train and fine-tune paradigm with pre-trained, prompts, and predictions. Allows models like GPT-3 to handle various tasks efficiently without updating underlying parameters.|
|**Basic components and process of Prompt learning**|Involves prompt templates, answer mappings, and pre-trained language models. Common prompt templates include fill-in-the-blank and prefix-based generation. Answer mapping (Verbalizer) evaluates possible answers and maps them to appropriate categories. Workflow includes using pre-trained models, adding context with a mask position, projecting labels to label words, and bridging the gap between pre-training and fine-tuning.|
|**Learning strategy**|Various strategies for prompt learning include pre-training then fine-tuning, tuning-free promotion, fixed LM prompt tuning, fixed prompt LM tuning, and combined prompt+LM tuning. The choice of strategy depends on task requirements, with each offering different benefits in terms of precision, resource efficiency, and control.|

## Training of Large Language Models (LLMs)

|Training Steps|Notes|
|-|-|
|**Data Collection and Processing**|Gathering and preparing large datasets for training.|
|**Pre-training Process**|Determining model architecture and pre-training tasks, employing parallel training algorithms.|
|**Fine-tuning and Alignment**|Adjusting the model for specific tasks using appropriate datasets and techniques.|

### Data Preparation and Preprocessing

|Dataset|Training LLMs requires vast and diverse text datasets. Common sources include web text, books, conversations, and professional domain-specific texts. High-quality, large-scale datasets significantly enhance model performance and generalization capabilities.|
|-|-|
|**Books**|BookCorpus and Gutenberg provide a wide range of literary genres, contributing to diverse language understanding.|
|**CommonCrawl**|A repository of over 250 billion web pages, frequently used but requires preprocessing to filter low-quality data.|
|**Reddit Links**|Valuable for high-quality text due to its upvote/downvote system, e.g., PushShift.io and OpenWebText.|
|**Wikipedia**|A vast repository of high-quality, encyclopedic content in multiple languages.|
|**Code**|Limited availability; sources include GitHub and Stack Overflow.|

|Data Preprocessing Steps|Notes|
|-|-|
|**Filtering Quality Data**|Heuristic-based and classifier-based methods to remove low-quality text.|
|**Deduplication**|Removing repetitive content to avoid instability and dataset contamination.|
|**Privacy Scrubbing**|Ensuring sensitive information is removed to prevent privacy breaches.|
|**Filtering Out Toxic and Biased Text**|Implementing moderation techniques to eliminate harmful and biased content.|
|**Expanding Vocabulary**|Adding relevant words and phrases, especially for domain-specific applications.|

|Encoder-decoder Architecture|Decoder-only Architecture|
|-|-|
|Encoder encodes input sequences using multiple layers of self-attention, and the Decoder generates target sequences using cross-attention over the encoded representation.|Focuses on sequentially generating tokens by attending to preceding tokens without an explicit encoding phase.|
|Examples: T5, flan-T5, BART.|Causal Decoder: Each token attends to past tokens and itself, using unidirectional attention (e.g., GPT series, BLOOM, OPT, Gopher, LLaMA).|
||Prefix Decoder: Combines bidirectional attention for prefix tokens with unidirectional attention for subsequent tokens (e.g., PaLM, GLM).|

### Pre-training Tasks

* Language Modeling: The primary task involves predicting the next word in a context, helping the model learn vocabulary, grammar, semantics, and text structure.
* Objective: Maximize the likelihood of the text sequence using cross-entropy loss.

### Model Training

|Model Training Strategies|Notes|
|-|-|
|**Parallel Training**|**Data Parallelism**: Distributes data across GPUs; gradients are aggregated for model updates.|
||**Distributed Data Parallelism**: Uses all-reduce on gradients for consistent updates across GPUs.|
||**Model Parallelism**: Distributes model parameters across GPUs for parallel processing.|
||**ZeRO (Zero Redundancy Optimizer)**: Reduces memory usage by partitioning gradients and parameters across GPUs.|
||**Pipeline Parallelism**: Assigns different model layers to different GPUs for sequential processing.|
|**Mixed Precision Training**|Utilizes 16-bit floating-point numbers (FP16) to reduce memory usage while maintaining computational speed, with FP32 used for parameter updates to avoid underflow.|
|**Offloading**|Moves optimizer parameters from GPU to CPU to reduce GPU memory load, leveraging ZeRO3 for efficient parameter and gradient management.|
|**Overlapping**|Asynchronous memory operations overlap with computations, optimizing forward propagation by pre-fetching parameters for subsequent layers.|
|**Checkpoint**|Saves memory by retaining only certain checkpoints during forward propagation, recomputing intermediate results as needed during backward propagation.|

### Fine-Tuning

|Fine-tuning LLMs involves three main approaches|Notes|
|-|-|
|**Supervised Fine-Tuning (SFT)**|Adjusts the model using labeled datasets to adapt to specific tasks. Instruction Tuning is a specific form of SFT, using (instruction, output) pairs to enhance model capabilities and controllability. Common datasets: static-hh, OIG, Self-Instruct, Natural Instructions, P3, Promptsource, WebGPT, Flan, MVPCorpus.|
|**Alignment Tuning**|Ensures LLMs are helpful, honest, and harmless. Often uses Reinforcement Learning with Human Feedback (RLHF) to align model outputs with human intentions.Techniques include using human feedback to train reward models and employing Proximal Policy Optimization (PPO).|
|**Parameter-Efficient Tuning**|Reduces computational and memory overhead by fine-tuning only a subset of model parameters. Methods include Low-Rank Adaptation (LoRA), Prefix Tuning, and P-Tuning, enabling efficient tuning even with limited resources.|

### Evaluation

|Evaluating LLMs involves various methods to ensure performance and safety.|Notes|
|-|-|
|**Static testing dataset**|Datasets for validation include ImageNet, Open Images, GLUE, SuperGLUE, MMLU, CMMLU, XTREME, MATH, GSM8K, HumanEval, MBPP, and several others for reasoning and medical knowledge.|
|**Open Domain Q&A Evaluation**|Uses datasets like SquAD and Natural Questions with metrics such as F1 score and Exact-Match accuracy (EM) to evaluate LLMs' question-answering abilities.|
|**Security Evaluation**|Addresses potential biases, privacy protection, and robustness against adversarial attacks. Tools and methods to mitigate these issues include controlled text generation algorithms and privacy neuron detection and editing.|
|**Evaluation Methods**|Combines automated metrics (e.g., BLEU, ROUGE, BERTScore) and manual evaluation to comprehensively assess LLM performance.|

### LLM Framework

Training large-scale LLMs is facilitated by distributed training frameworks that leverage GPUs, CPUs, and NVMe memory. 

|Key frameworks|Notes|
|-|-|
|**Transformers (Hugging Face)**|Open-source library for building models with Transformer architecture.|
|**DeepSpeed (Microsoft)**|Optimization library supporting ZeRO technology and various optimizations for efficient training.|
|**BMTrain (Tsinghua University)**|Toolkit for distributed training of large models without extensive code refactoring.|
|**Megatron-LM (NVIDIA)**|Library for training large-scale language models using model and data parallelism, mixed-precision training, and FlashAttention.|

## Inference with Large Language Models

As large language models (LLMs) continue to scale, they demand significant computational resources and energy, leading to a focus on reducing their computational and storage costs while maintaining reasoning capabilities.

|Efficient LLM inference through four main strategies|Notes|
|-|-|
|**Model Compression**|**Knowledge Distillation**: Transfers knowledge from a large (teacher) model to a smaller (student) model by matching their outputs, providing more information than direct labels. Techniques like PKD and Tiny BERT improve this by using intermediate layers and various model components for better distillation.|
||**Model Pruning**: Removes redundant parts of a model's parameter matrices, categorized into unstructured (random weights) and structured pruning (specific patterns or units). Studies show structured pruning can retain model performance even when significant portions of the model are pruned.|
||**Model Quantization**: Reduces the precision of model computations from floating-point to fixed-precision to save on computation and storage costs. Methods like BinaryBERT optimize low-precision quantization to maintain performance.|
||**Weight Sharing**: Uses the same parameters across multiple parts of the model, reducing the number of parameters and enhancing efficiency. ALBERT is an example that uses cross-layer parameter-sharing to improve performance.|
||**Low-rank Approximation**: Decomposes matrices into lower-rank forms to reduce model size and computational demands, effective for resource-constrained deployments. Techniques like DRONE achieve significant performance and speed improvements.|
|**Memory Scheduling**|Efficient memory management is crucial for deploying LLMs on consumer-grade GPUs. Strategies like BMInf use virtual memory principles to smartly schedule model parameters between GPU and CPU, optimizing memory usage and inference speed.|
|**Parallelism**|**Data Parallelism**: Distributes data across multiple GPUs to increase throughput.|
||**Tensor Parallelism**: Partitions model parameters across multiple units for large models that cannot fit into a single GPU's memory.|
||**Pipeline Parallelism**: Splits model layers across GPUs, often combined with tensor parallelism, to enhance performance and device utilization.|
|**Structural Optimization**|Minimizing memory access during forward propagation is key to speeding up inference. Techniques like FlashAttention and PagedAttention use chunked computation to reduce memory overhead and access times, enhancing computational speed.|
|**Inference Frameworks**|Mainstream frameworks incorporate parallel computing, model compression, memory scheduling, and structural optimizations to facilitate the deployment and inference of LLMs. These frameworks provide the necessary infrastructure and tools, with selection depending on project needs, hardware, and user preferences.|

## Utilization of LLMs

LLMs have a wide range of applications across various specialized domains. They are primarily utilized by designing prompts for different tasks, leveraging their zero-shot and few-shot capabilities, and incorporating reasoning processes like chain-of-thought prompts.

|Utilization Approaches|Notes|
|-|-|
|**Zero-shot Learning**|Tasks are accomplished by guiding LLMs with straightforward prompts, exploiting their powerful zero-shot capabilities without additional training.|
|**Few-shot Learning**|For more complex tasks, in-context learning is employed. This involves providing a few examples within the prompt to guide the LLM in task completion. Enhancing in-context learning with chain-of-thought prompts introduces a reasoning process, improving performance on tasks requiring logical steps.|
|**Intermediate Representations**|In some research areas, such as neuroscience, intermediate layer representations of LLMs are utilized. For example, embedding representations help investigate brain function activation regions.|

|Deployment Methods|Notes|
|-|-|
|**Accessing Proprietary Models**|Utilizing robust proprietary models through open API services, such as ChatGPT, allows users to leverage powerful LLM capabilities without managing infrastructure.|
|**Deploying Open-source LLMs Locally**|Open-source LLMs can be deployed for local use, offering flexibility and control over the model and its applications.|
|**Fine-tuning Open-source LLMs**|Fine-tuning open-source LLMs to meet specific domain standards allows for tailored applications in particular fields. These fine-tuned models can then be deployed locally.

In summary, LLMs are versatile tools used across diverse fields by designing prompts for zero-shot and few-shot learning, accessing proprietary APIs, deploying open-source models locally, or fine-tuning them for specialized applications. Incorporating chain-of-thought prompts and utilizing intermediate representations further enhance their usability in complex tasks and research.

## Future Directions and Implications

This section explores the future trends and impact of Large Language Models (LLMs), divided into three parts: advancements in LLM technology, directions for AI researchers, and societal impacts.

|Developmental Trends in LLM Technology|Notes|
|-|-|
|**Expansion of Model Scale**|LLMs are expected to continue growing in scale, enhancing their learning capabilities and performance.|
|**Multimodal Data Processing**|Current LLMs primarily handle text, but future models may incorporate multimodal data (images, videos, speech), broadening their application scope.|
|**Efficiency in Training and Deployment**|Techniques like knowledge distillation, model compression, and quantization will focus on reducing training and inference costs.|
|**Domain-Specific Training**|LLMs will be fine-tuned for specific sectors, improving their adaptability and understanding of industry-specific contexts.|
|**New Architectures**|While transformers dominate, RNN-based models like RWKV show potential, offering competitive performance and possibly overcoming some transformer limitations.|

|Developmental Directions for AI Researchers|Notes|
|-|-|
|**Interdisciplinary Collaboration**|AI development will increasingly require collaboration across various industries, combining expertise from different fields.|
|**Comprehensive Skills for Researchers**|Researchers need proficiency in large-scale data management and distributed parallel training, highlighting the importance of engineering skills or effective collaboration with engineers.|

|Societal Impact of LLMs|Notes|
|-|-|
|**Ethical Concerns and Model Bias**|Ongoing development will focus on managing biases and mitigating misuse risks.|
|**Privacy and Security**|Future LLMs might adopt federated learning and decentralized approaches to enhance performance while protecting user privacy.|
|**Interdisciplinary Standards and Ethical Frameworks**|Collaboration with experts in decision-making, legal studies, and sociology is crucial to establish ethical standards.|
|**Public Awareness and Education|Mandatory training for the public will enhance understanding of LLM capabilities and limitations, promoting responsible use.|

## Conclusion

* The introduction of ChatGPT has revolutionized LLMs, significantly impacting their use in various tasks and highlighting the importance of cost-effective training and deployment. This paper reviewed the evolution of LLM training techniques and deployment technologies, emphasizing the shift towards low-cost development. The dominance of models like GPT and the pivotal release of ChatGPT by OpenAI underscore the need for domain-specific models and improvements in training processes.

* Key challenges in LLM development include handling large-scale data and distributed parallel training, requiring collaboration between researchers and engineers. Future directions for LLMs involve advancements in model architectures, training efficiency, and broader applications. The insights provided aim to equip researchers with the necessary knowledge to navigate the complexities of LLM development, fostering innovation and progress in AI. As LLMs evolve, they will continue to shape the future of natural language processing and intelligent systems.