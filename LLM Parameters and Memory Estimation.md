# LLM: Parameters and Memory Estimation

## General understanding of VRAM requirements

|Estimate Memory Usage for Inference|float precision|BF16 precision|int8 precision|int4 precision|
|-|-|-|-|-|
|7B|28 GB|14 GB|7 GB|3.5 GB|
|13B|52 GB|26 GB|13 GB|6.5 GB|
|34B|136 GB|68 GB|34 GB|17 GB|
|70B|280 GB|150 GB|70 GB|35 GB|

|Estimate Memory Usage for Training and Fine-Tuning|VRAM for Model Parameters|VRAM for Gradients and Optimizer States|Total VRAM Requirement|
|-|-|-|-|
|7B|28 GB|84 GB|112 GB|
|13B|52 GB|156 GB|208 GB|
|34B|136 GB|408 GB|544 GB|
|70B|280 GB|840 GB|1120 GB|
  
|Find practical memory pptimizatio solutions on the Internet|Model Size|Total VRAM Size|
|-|-|-|
|[Mentor-100](https://drive.google.com/file/d/1-umJYfhbdZ3Iaka3V4bP_MFiyLEvXuG3/view)|33B+|40 GB|
|[Mentor-200](https://drive.google.com/file/d/1-umJYfhbdZ3Iaka3V4bP_MFiyLEvXuG3/view)|70B+|80 GB|
|[Mentor-300](https://drive.google.com/file/d/1-umJYfhbdZ3Iaka3V4bP_MFiyLEvXuG3/view)|180B+|192 GB|
|[Mentor-400](https://drive.google.com/file/d/1-umJYfhbdZ3Iaka3V4bP_MFiyLEvXuG3/view)|180B+|384 GB|
|[MAINGEAR SHODAN 64](https://maingear.com/product/pro-ai-shodan-64-reservation/)|70B|64 GB|
|[MAINGEAR SHODAN 96](https://maingear.com/product/pro-ai-shodan-96-reservation/)|70B|96 GB|
|[MAINGEAR SHODAN 192](https://maingear.com/product/pro-ai-shodan-192-reservation/)|70B|192 GB|
|[Answer.AI](https://www.answer.ai/posts/2024-03-06-fsdp-qlora.html)|70B|24GB x 2|

## [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)

* Scaling laws in the context of LLMs highlight the relationship between the model size, data, and computational resources with the performance and capabilities of the models. While the number of parameters is a major factor, precision, data quality, model architecture, and training techniques also play vital roles. Balancing these elements against their respective challenges and trade-offs is essential for developing and deploying efficient and powerful LLMs.
* As models get bigger (more parameters) or are trained on more data, they tend to get better at their tasks in a predictable way.
* By framing the information in terms of scaling laws, it becomes clear how each factor contributes to the overall performance and what trade-offs must be considered when scaling up LLMs.
* [Stanford cs224n](https://www.youtube.com/watch?v=UFem7xa3Q2Q)
* [Stanford cs324](https://stanford-cs324.github.io/winter2022/assets/pdfs/Scaling%20laws%20pdf.pdf)

|Key Factors|Importance|Challenges and Trade-offs|
|-|-|-|
|**Number of Parameters**|Larger models with more parameters have a higher capacity to learn and represent complex patterns, which typically results in better performance across a variety of tasks.|Increased computational resources, memory, and processing power are required. There is also a higher cost and environmental impact associated with training larger models.|
|**Precision**|Precision, especially lower precision computations (like FP16 instead of FP32), helps reduce memory usage and increase computational speed, enabling the training of larger models more efficiently.|Lower precision can lead to numerical instability or reduced accuracy if not managed correctly. Techniques like mixed precision training are employed to balance these issues.|
|**Data Quality and Quantity**| Both the quality and the quantity of the training data are critical. High-quality and extensive datasets allow models to generalize better and perform well on diverse tasks.|Acquiring high-quality, diverse datasets is challenging and costly. Training a large model on poor-quality data leads to suboptimal performance.|
|**Architecture and Optimization**|Advances in model architectures (such as Transformer-based models) and optimization techniques (like the Adam optimizer) have significantly enhanced the performance of LLMs.|Continuous innovation requires ongoing research and development. New architectures and optimizers may involve initial implementation challenges and computational costs.|
|**Training Techniques**|Techniques like transfer learning, fine-tuning, and reinforcement learning from human feedback (RLHF) are crucial for improving model performance and adapting models to specific tasks.|These techniques require additional computational resources and time. Effective application demands expertise and careful management to avoid issues like overfitting.|

## Model Size and Application

|LLaMA 2|Large Language Model Meta AI|
|-|-|
|**Improved Performance**|Enhanced architecture and training techniques to provide better accuracy and efficiency in various NLP tasks.|
|**Open-Source**|Available for researchers and developers to use, modify, and contribute to, fostering collaboration and innovation in the field of AI.|
|**Scalability**|Designed to handle large-scale datasets and complex language tasks, making it suitable for a wide range of applications.|
|**Versatility**|Can be used for tasks such as text generation, language translation, summarization, question answering, and more.|

|LLaMA 2 - 7B|It is well-suited for applications that require fast response times and can operate on limited computational resources.|
|-|-|
|**Customer Support Chatbots**|Automating responses to common customer inquiries.<br>Reduces the need for human agents, providing instant support, improving customer satisfaction.|
|**Content Moderation**|Filtering and moderating user-generated content on social media platforms.<br>Ensures community guidelines are followed, reduces manual moderation workload.|
|**Email Filtering and Categorization**|Automatically categorizing and prioritizing emails.<br>Enhances productivity by helping users manage their inbox efficiently.|
|**Examples**|**Notes**|
|[Zendesk Answer Bot](https://www.chatbase.co/?gad_source=1&gclid=Cj0KCQjw9vqyBhCKARIsAIIcLMFMz2-AVPEfakCZOzhWIcRjR7mo1yNR9wRLUFLb2OzCDHyyr2ulzjsaAoWaEALw_wcB)|Automates customer support by providing instant responses to common questions.|
|[OpenAI Moderation API](https://platform.openai.com/docs/api-reference/moderations)|Helps platforms detect and filter inappropriate content in real-time.|
|[Google's Gmail Smart Compose](https://support.google.com/mail/answer/9116836?hl=en&co=GENIE.Platform%3DDesktop)|Suggests responses and helps categorize emails, making email management more efficient.|

|LLaMA 2 - 13B|It offers a balance between performance and resource requirements, suitable for moderately complex tasks.|
|-|-|
|**Personalized Marketing**|Generating personalized marketing content and product recommendations.<br>Increases engagement and conversion rates by targeting customers with relevant content.|
|**Virtual Personal Assistants**|Assisting with scheduling, reminders, and routine tasks.<br>Improves efficiency and productivity for individuals and professionals.|
|**Sentiment Analysis**|Analyzing customer feedback and social media sentiment.<br>Provides insights into customer opinions, aiding in strategic decision-making.|
|**Examples**|**Notes**|
|[Adobe Experience Cloud](https://business.adobe.com/)|Uses AI to deliver personalized marketing experiences and product recommendations.|
|[Google Assistant](https://assistant.google.com/)|Assists users with tasks like scheduling, reminders, and information retrieval.|
|[Brandwatch](https://www.brandwatch.com/)|Analyzes social media and customer feedback to gauge public sentiment and opinions.|

|LLaMA 2 - 33B|It is designed for more complex tasks requiring deeper language understanding and generation capabilities.|
|-|-|
|**Advanced Document Understanding**|Extracting insights and summarizing long documents, legal contracts, and research papers.<br>Saves time and resources in analyzing detailed and extensive texts.|
|**Automated Content Creation**|Generating high-quality articles, reports, and creative writing.<br>Assists in content marketing and publishing by producing drafts that require minimal editing.|
|**Fraud Detection**|Analyzing transactional data and identifying potentially fraudulent activities.<br>Enhances security and reduces financial losses due to fraud.|
|**Examples**|**Notes**|
|[Kira Systems](https://kirasystems.com/)|Uses AI to extract information from legal documents and contracts, aiding legal professionals.|
|[Copy.ai](https://www.copy.ai/)|Generates marketing copy, blog posts, and other content, reducing the workload for content creators.|
|[Darktrace](https://darktrace.com/)|Utilizes AI to detect and respond to cyber threats and potential fraud in real-time.|

|LLaMA 2 - 70B|The 70B model, being the most powerful, is ideal for highly complex and resource-intensive tasks.|
|-|-|
|**Comprehensive AI Research and Development**|Building and testing sophisticated AI models and simulations.<br>Advances innovation in AI technology, pushing the boundaries of what's possible.|
|**Language Translation and Localization**|Providing high-accuracy translations for multiple languages, including context-specific nuances.<br>Enables global businesses to communicate effectively across different regions and cultures.|
|**In-Depth Predictive Analytics**|Analyzing large datasets to forecast trends and behaviors.<br>Assists in strategic planning and decision-making with high accuracy.|
|**Examples**|**Notes**|
|[DeepL Translator](https://www.deepl.com/translator)|Provides highly accurate translations, taking into account context and nuances in multiple languages.|
|[IBM Watson](https://www.ibm.com/watson)|Offers predictive analytics solutions across various industries, including healthcare and finance, to forecast trends and behaviors.|

---

## Memory Optimization Techniques for Efficient Model Training

* By leveraging these techniques, you can achieve state-of-the-art model performance without the need for extremely high-end hardware, making advanced AI more accessible and practical.
* This collective term and explanation provide a clear and concise way to communicate the benefits of these advanced techniques to buyers, emphasizing both their practical applications and their cost-saving advantages.

|Strategies|Primary Use Case|Key Benefit|Main Drawback|
|-|-|-|-|
|**Data Parallelism**|Distributing data across GPUs|Simple and scalable approach|Synchronization overhead|
|**Tensor Parallelism**|Splitting tensors across GPUs|Efficient use of GPU resources|Complexity in implementation|
|**Model Parallelism**|Handling large models|Enables training of very large models|Increases inter-GPU communication overhead|
|**ZeRO (Zero Redundancy Optimizer)**|Memory-efficient optimization|Drastically reduces memory footprint|Requires advanced implementation|
|**FSDP (Fully Sharded Data Parallel)**|Efficient distributed training|Combines benefits of data and model parallelismImplementation complexity and potential communication overhead|
|**Sharded Optimizers**|Reducing per-GPU memory usage|Distributes memory load|Complexity in implementation|
|**Mixed-Precision Training Mechanics**|Reducing memory and speeding up training|Halves memory usage, faster computation|Potential numerical instability|
|**LoRA**|Efficient fine-tuning|Lowers VRAM for fine-tuning|May not be applicable for pre-training|
|**QLoRA**|Efficient fine-tuning with quantization|Further reduces VRAM for fine-tuning|Complexity in implementation|
|**Activation Quantization**|Reducing memory usage|Lowers VRAM by reducing activation precision|Potential loss in model accuracy|
|**Offloading**|Using CPU or NVMe for storage|Extends memory capacity beyond GPU VRAM|Latency due to data transfer|
|**Gradient Checkpointing**|Reducing memory during backpropagation|Decreases VRAM usage|Increases computational overhead|

### [Mixed-Precision Training Mechanics](https://lightning.ai/pages/community/tutorial/accelerating-large-language-models-with-mixed-precision-techniques/)

* It’s called “mixed-“ rather than “low-“precision training because we don’t transfer all parameters and operations to 16-bit floats. Instead, we switch between 32-bit and 16-bit operations during training, hence, the term “mixed” precision.

|Step|Processed|
|-|-|
|1. Convert weights to FP16|The weights (or parameters) of the neural network, which are initially in FP32 format, are converted to lower-precision FP16 format. This reduces the memory footprint and allows for faster computation, as FP16 operations require less memory and can be processed more quickly by the hardware.|
|2. Compute gradients|The forward and backward passes of the neural network are performed using the lower-precision FP16 weights. This step calculates the gradients (partial derivatives) of the loss function with respect to the network’s weights, which are used to update the weights during the optimization process.|
|3. Convert gradients to FP32|After computing the gradients in FP16, they are converted back to the higher-precision FP32 format. This conversion is essential for maintaining numerical stability and avoiding issues such as vanishing or exploding gradients that can occur when using lower-precision arithmetic.|
|4. Multiply by learning rate and update weights|Now in FP32 format, the gradients are multiplied by a learning rate (a scalar value that determines the step size during optimization).|
|Final. FP32 Weights|The product from step 4 is then used to update the original FP32 neural network weights. The learning rate helps control the convergence of the optimization process and is crucial for achieving good performance.|

### [LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685)

* An important paradigm of natural language processing consists of large-scale pre-training on general domain data and adaptation to particular tasks or domains. As we pre-train larger models, full fine-tuning, which retrains all model parameters, becomes less feasible. Using GPT-3 175B as an example -- deploying independent instances of fine-tuned models, each with 175B parameters, is prohibitively expensive. We propose Low-Rank Adaptation, or LoRA, which freezes the pre-trained model weights and injects trainable rank decomposition matrices into each layer of the Transformer architecture, greatly reducing the number of trainable parameters for downstream tasks. Compared to GPT-3 175B fine-tuned with Adam, LoRA can reduce the number of trainable parameters by 10,000 times and the GPU memory requirement by 3 times.

### [Gradient Checkpointing](https://github.com/cybertronai/gradient-checkpointing)

* Memory Usage in Backpropagation: Standard backpropagation stores all activations, leading to memory usage that scales linearly with the number of layers.
* Only a subset of activations (checkpoints) are kept in memory. Nodes between checkpoints are recomputed during the backward pass, reducing memory usage. For example, if a neural network has 100 layers, checkpoints would be placed approximately every 10 layers.
* Additional computation time is around 20%, allowing models more than 10x larger to fit onto a GPU.
* Gradient-checkpointing is a technique used in training deep neural networks to save memory. It works by trading off computation for memory usage. Instead of storing the activations of all layers during the forward pass, it only stores the activations at certain "checkpoint" layers. During the backward pass, the intermediate activations that were not stored are recomputed as needed. This reduces the memory needed to store activations, allowing the training of larger models or using larger batch sizes without running out of memory.

### Quantization

* In computing, a single-precision floating-point number (FP32) occupies 4 bytes, whereas an 8-bit integer (INT-8) only occupies 1 byte. Storing 123.456789 requires a 4-byte FP32, while 123 only needs 1 byte, resulting in a fourfold difference. However, the discrepancy of 0.456789 may seem small, but in neural networks, these errors can be exponentially amplified with increasing layers. Hence, research in quantization focuses on minimizing errors after converting from floating-point to integer operations.
* Quantization reduces the memory and computational requirements of AI models by representing numbers with fewer bits. This results in smaller model sizes, faster inference, lower power consumption, and improved compatibility with hardware accelerators. It also provides a regularization effect and cost savings. However, it may lead to some loss in accuracy and requires careful tuning for optimal performance. Overall, quantization offers significant benefits for deploying AI models efficiently in various applications.

|Conversion|Quantization|
|-|-|
|The process of converting a trained machine learning model from one format to another. This conversion is often necessary to deploy the model on different platforms or runtime environments. For example, you might convert a model trained in TensorFlow to a format compatible with TensorFlow Lite for deployment on mobile devices, or to ONNX (Open Neural Network Exchange) format for deployment across various frameworks.|Reduce the computational and memory requirements of a model by reducing the precision of its weights and activations. In quantization, floating-point values are replaced with lower precision fixed-point or integer representations. This can significantly reduce the model size and make it more efficient for inference, especially on resource-constrained devices like mobile phones or IoT devices.|

---

## Practical understanding of the ideal and maximum size of Large Language Models

|Model Size|Baseline VRAM Requirement|VRAM with Mixed-Precision|VRAM with Gradient Checkpointing|VRAM with LoRA/QLoRA|VRAM with Sharded Optimizers|Consumer GPU Solution (32GB Each)|
|-|-|-|-|-|-|-|
|7B|28GB|14GB|21GB|4-8GB|10-15GB|2 GPUs (64GB total)|

* Using Mixed-Precision: The model needs 14GB VRAM.
* Using Gradient Checkpointing: The memory for activations is reduced, potentially managing within 21GB VRAM.
* Using LoRA: The memory footprint for trainable parameters is reduced to 4-8GB.
* Using Sharded Optimizers: The VRAM required is distributed across GPUs, so each GPU might handle 10-15GB.
* Mixed-Precision Training (14GB) + Gradient Checkpointing (partially reduces activations memory) can make it fit within 32GB. Adding LoRA further reduces memory, making it more efficient and ensuring it fits comfortably.

---

## [Train a 70b model on two 24GB GPUs](https://github.com/AnswerDotAI/fsdp_qlora/tree/main?trk=public_post_comment-text)

* [Fully Sharded Data Parallel (FSDP)](https://engineering.fb.com/2021/07/15/open-source/fsdp/) is the newest tool we’re introducing. It shards an AI model’s parameters across data parallel workers and can optionally offload part of the training computation to the CPUs.
* [QLoRA: Efficient Finetuning of Quantized LLMs](https://arxiv.org/abs/2305.14314)
* QLoRA backpropagates gradients through a frozen, 4-bit quantized pretrained language model into Low Rank Adapters.
* QLoRA introduces a number of innovations to save memory without sacrificing performance: (a) 4-bit NormalFloat (NF4), a new data type that is information theoretically optimal for normally distributed weights (b) double quantization to reduce the average memory footprint by quantizing the quantization constants, and (c) paged optimziers to manage memory spikes.

### QLoRA and FSDP Explained with Chef and Cooking Examples

|QLoRA|Represents efficient resource management and quick adaptation to specific needs in a kitchen, ensuring high performance and responsiveness.|
|:-|:-|
|**Pre-trained Model**|As a master chef, you possess extensive culinary knowledge, capable of preparing a diverse range of dishes.|
|**Quantization**|To enhance efficiency, you store ingredients in smaller, more manageable containers, saving space and resources in your kitchen.|
|**Low-Rank Adaptation**|You make minor adjustments to specific recipes based on customer demands, allowing you to quickly adapt without overhauling your entire skill set.|
|**Summary**|QLoRA is like running an efficient kitchen where you save resources by optimizing storage and make quick, targeted adjustments to meet customer preferences, thus maintaining high performance and adaptability.|

|FSDP|Represents collaborative, parallel efforts in a large kitchen, where tasks are distributed and synchronized to efficiently handle complex and large-scale preparations. Using these culinary analogies helps in understanding how QLoRA and FSDP optimize and manage large models in AI, akin to running an efficient and well-coordinated kitchen.|
|:-|:-|
|**Sharding**|You distribute the preparation tasks among your assistant chefs. Each chef is responsible for a specific portion of the work, such as chopping vegetables or marinating meat. Similarly, in FSDP, model parameters are divided into shards and distributed across multiple devices.|
|**Parallel Processing**|All chefs work in parallel on their assigned tasks, communicating as necessary to ensure everything comes together seamlessly. In FSDP, each device processes its shard while synchronizing with others to ensure cohesive training of the model.|
|**Coordination**|You ensure that the assistant chefs’ tasks integrate smoothly, resulting in a well-prepared banquet. In FSDP, devices coordinate to ensure the model training process is unified and complete.|
|**Summary**|FSDP is like managing a large kitchen where tasks are distributed among multiple chefs, each focusing on their part while working in parallel and coordinating efforts to efficiently prepare a grand banquet.|

---

## Examples of GPU memory options

|GPU|20GB|24GB|32GB|48GB|> 80GB|
|-|-|-|-|-|-|
|AMD|Radeon RX 7900 XT|**Radeon RX 7900 XTX**|Radeon Pro W7800|Radeon Pro W7900|MI300 (128GB or 192GB)|
|Nvida|RTX A4500, RTX 4000 Ada|RTX 4090, RTX A5000, RTX A5500, RTX 4500 Ada|RTX 5000 Ada|RTX A6000, RTX 6000 Ada, RTX 5880 Ada|H100 (80GB)|

### AMD GPUs

* [AMD Radeon 7900 XT/XTX Inference Performance Comparisons](https://www.reddit.com/r/LocalLLaMA/comments/191srof/amd_radeon_7900_xtxtx_inference_performance/)
* [AMD GPU guide (now w/ ROCm info)](https://llm-tracker.info/howto/AMD-GPUs)
* Lamini makes AMD Instinct GPUs available through the [LLM Superstation](https://www.lamini.ai/blog/lamini-llm-finetuning-on-amd-rocm-a-technical-recipe) in both desktop and rack-mount server configurations.
* [ROCm on Radion](https://community.amd.com/t5/ai/amd-extends-support-for-pytorch-machine-learning-development-on/ba-p/637756)
* [LLM Worksheet](https://docs.google.com/spreadsheets/d/1kT4or6b0Fedd-W_jMwYpb63e1ZR3aePczz3zlbJW-Y4/edit?gid=752855929#gid=752855929)

### NVLink VRAM Pooling

* It refers to the ability to combine the video memory (VRAM) of multiple GPUs into a single, large memory pool. This allows for more efficient use of VRAM, especially in workloads that require large amounts of memory, such as deep learning models or complex simulations.
*  **Consumer graphics cards like the RTX 4080 and RTX 4090 do not support NVLink. The RTX 3090 is the last in the consumer lineup to support NVLink.** This means you cannot utilize NVLink for VRAM pooling with the newer RTX 40 series consumer cards.

|Key benefits|Notes|
|-|-|
|**Increased Effective Memory Capacity**|By pooling the VRAM of multiple GPUs, applications can access a larger memory space than what is available on a single GPU. This is particularly beneficial for training large AI models or running large-scale simulations that exceed the VRAM capacity of individual GPUs.|
|**Faster Data Transfer**|NVLink provides significantly higher bandwidth compared to PCIe, enabling faster data transfer between GPUs. This reduces the latency and improves the performance of applications that require frequent communication between GPUs.|
|**Unified Memory Access**|With VRAM pooling, memory management becomes more straightforward as the system can treat the pooled VRAM as a single, unified memory space. This can simplify programming and optimize resource utilization.|

|Use Cases|Notes|
|-|-|
|**AI and Deep Learning**|Training large neural networks often requires vast amounts of memory. NVLink VRAM pooling allows researchers to train models that wouldn't fit into the memory of a single GPU.|
|**Scientific Simulations**|Complex simulations, such as those used in physics, climate modeling, and bioinformatics, can benefit from the increased memory capacity and faster data transfer provided by NVLink VRAM pooling.|
|**High-Performance Computing (HPC)**|HPC applications that require significant computational power and memory can leverage NVLink VRAM pooling to improve performance and efficiency.|

### Multiple gpus work together in a system to train the model (Two RTX 4090 GPUs = 24GB x 2 = 48GB ?)

|Data Distribution|It doesn't increase the VRAM available for a single model instance. Instead, it allows you to distribute the workload, making better use of the combined memory resources.|
|-|-|
|**Model Parallelism**|The model is split across multiple GPUs. Each GPU processes different parts of the model, which allows the workload to use the combined memory of both GPUs.|
||Usage: Suitable for large models that do not fit into the memory of a single GPU.|
||Limitation: Requires efficient communication between GPUs, which might not be optimal without NVLink. Data transfer between GPUs over PCIe is slower than NVLink|
|**Data Parallelism**|Each GPU holds a copy of the entire model but processes different batches of data. This approach scales well across multiple GPUs but does not increase the available memory for a single model instance.|
||Usage: Effective for training on large datasets where each batch is processed independently.|
||Limitation: The memory limit for a single model instance remains the same as the VRAM of a single GPU (24 GB in the case of RTX 4090).|

|Practical Example for Large Language Models (LLMs)|The actual VRAM available to a single process or model instance does not simply add up to 48 GB. Instead, you need to architect your workload to leverage the independent 24 GB VRAM of each GPU.|
|-|-|
|**Data Parallelism**|When training an LLM with two RTX 4090 GPUs, you can distribute different batches of data to each GPU. However, each GPU will still process its own 24 GB VRAM independently.|
|**Model Parallelism**|If the model architecture supports it, you can split the model across two GPUs to use a combined memory of 48 GB, but this requires careful architecture and efficient inter-GPU communication.|
|**Inference and Serving**|For inference, where the model size might exceed 24 GB, you can use model parallelism to split the model across two GPUs, allowing each GPU to handle a portion of the model.|

### RTX 3090 VS RTX 4090

|Data Transmission Rates|Two RTX 3090 GPUs connected via NVLink will have a faster data transmission rate between them compared to two RTX 4090 GPUs connected via PCIe.|
|-|-|
|NVIDIA RTX 3090 with NVLink|NVIDIA RTX 4090 with PCIe|
|NVLink Bandwidth: Each NVLink bridge offers a bidirectional bandwidth of 112.5 GB/s per link. The RTX 3090 supports two NVLink bridges, which can theoretically provide up to 224 GB/s of bandwidth between two GPUs.|PCIe Bandwidth: The RTX 4090 uses PCIe 4.0, which offers up to 16 GB/s per direction for a single x16 slot, resulting in a total of 32 GB/s bidirectional bandwidth. Even with PCIe 5.0, which offers double the bandwidth of PCIe 4.0, the total bidirectional bandwidth would be up to 64 GB/s.|
|Advantage: This high bandwidth allows for faster data exchange between the GPUs, which can be beneficial for applications that require frequent communication between the GPUs, such as certain deep learning models and large-scale simulations.|Limitation: Without NVLink, the GPUs rely on the PCIe bus for communication, which provides significantly less bandwidth compared to NVLink.|

|Performance Implications|RTX 3090|RTX 4090|
|-|-|-|
|**Inter-GPU Communication**|The high bandwidth provided by NVLink allows for efficient inter-GPU communication, which is crucial for workloads that involve frequent data exchange between GPUs.|The reliance on PCIe for inter-GPU communication results in lower bandwidth and potentially higher latency, which can affect performance in workloads that require intensive GPU-to-GPU communication.|
|**Workload Efficiency**|Ideal for tasks that benefit from high-speed data transfer between GPUs, such as distributed training of large neural networks, where data needs to be synchronized across GPUs.| While it has higher raw computational power and improved efficiency, the lack of NVLink means that it may not perform as well in scenarios where fast inter-GPU communication is critical.|
|**Practical Considerations**|Deep Learning: In deep learning, especially with large models, the ability to quickly share data between GPUs can significantly impact training times. The RTX 3090's NVLink can provide an advantage in such cases.|Gaming and General Use: For gaming and general consumer applications, the difference in inter-GPU communication speed may be less noticeable, and the overall performance improvement of the RTX 4090 in terms of raw power and efficiency might be more beneficial.|

### Multiple computers (nodes) work together in a network to train the model

|Practical Examples|Notes|
|-|-|
|**Google's BERT (Bidirectional Encoder Representations from Transformers)**|Google trained BERT using a distributed setup across multiple TPUs (Tensor Processing Units). TPUs are specialized hardware accelerators for machine learning workloads, and they can be used in a multi-node configuration to accelerate training. Google's use of TPUs in a distributed manner significantly reduced the time required to train BERT on massive text corpora.|
|**OpenAI's GPT-3**|GPT-3, one of the largest language models, was trained by OpenAI using a large cluster of GPUs across multiple nodes. OpenAI used NVIDIA V100 GPUs in a distributed setup to manage the immense computational load required to train a model with 175 billion parameters. The training process involved sophisticated data and model parallelism techniques to efficiently utilize the hardware resources.|
|**Microsoft's Turing-NLG (Natural Language Generation)**|Microsoft's Turing-NLG, another large-scale language model, was trained on a distributed system of NVIDIA DGX-2 nodes. Each DGX-2 node contains 16 NVIDIA V100 GPUs, and the distributed setup allowed Microsoft to train the model on a vast amount of data, using techniques like data parallelism and model parallelism to scale the training across multiple nodes.
|**DeepMind's AlphaStar**|Although not a language model, DeepMind's AlphaStar is a notable example of distributed training in reinforcement learning. AlphaStar was trained using a multi-node setup with thousands of TPUs to play the game StarCraft II at a superhuman level. The training process involved complex distributed systems to handle the massive amount of data and computation required.|
|**Facebook AI's RoBERTa**|RoBERTa, a robustly optimized BERT approach, was trained on a distributed setup using PyTorch and NVIDIA GPUs. Facebook AI Research (FAIR) used a large number of GPU nodes to train RoBERTa on diverse datasets, employing techniques like mixed precision training and gradient accumulation to optimize performance across the distributed system.|

|Key Techniques Used in Distributed Training|Notes|
|-|-|
|**Data Parallelism**|Splitting the training data across multiple GPUs/nodes so each processes a different subset of the data.|
|**Model Parallelism**|Dividing the model itself across multiple GPUs/nodes so each processes a different part of the model.|
|**Pipeline Parallelism**|Breaking the model into stages and passing data through these stages sequentially.|
|**Gradient Accumulation**|Accumulating gradients over several batches to effectively increase the batch size without needing additional memory.|
|**Horovod**|An open-source distributed training framework developed by Uber that simplifies the process of training large models across multiple GPUs and nodes.|