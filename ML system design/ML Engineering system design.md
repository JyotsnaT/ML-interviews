# ML Engineering system design



## Machine Learnign system desgin flow

Planning phase
  - Problem statement
  - Business metrics of the system
  - 

Data collection and labelling
  - Data collection strategies
    - internal labellers
    - external labellers
    - manual annotation of edge cases
  - ML data storage
    - Data lakes to data warehouse and databases
    - Workflow orchestration of data pipelines using AirFlow, Prefect, Dagster
    - Data versioning :
Model training
  - Model training
    - Data vs Model parallelism
    - Saving trained model on model store or registery
    - Feature fetcher
  -  CI/CD : Continuous integration, Continuous delivery and deployment
    - CI : Merge code changes faster assisted with automated checks
    - CD(Delivery) : Enable changes to the production automatically after the changes have been passed through a single click for freqeunt releases.
    - CD(Deployment) : Deploy changes to production automatically after a code change has been passed.
    - example : CircleCI, Github actions
 Testing
  - Unit tests, Integration test, End-to-end tests, production testing (shadow mode testing, canary deployment, AB testing)
  - A/B test
Deployment
  - Inference service : REST api
  - Model serving frameword
Monitoring
   

Model training

Model deployment 
  serving, inference

## Example cases
### Case1:
 - ML training platform [experiment velocity, standardisation]
- Serving [Model cloud, rayserve]
- Feature fetcher & store [Frame]
- Database [Vector Database, FAISS (approximate nearest neighbour ANN algorithms)]
- Execution DAG - proxima

### Case2: [Expedia] MLOps : EG's unified platform to train, deploy, maintain features, maintain models versioning, monitor health
- Model development is done in databricks notebooks.
- GitHub is used for code maintainance and version controlling. Changes pushed to prod only after integration tests are finished.
- Data source is s3 and acessed using Hive. Data pipelines are writtin in spark on kubernetes.
- EG compute platform : Kubernetes based container on which models are trained and scored. Individual step is containarized. The platform supports ops like logging, metrics, scheduling, security, tracing.
- Model repository service : To manage models and their versions
- Airflow for workflow orchestration : Useful for batch inferencing using multiple models.
- Machine learning workflows are deployed through pre configuerd CI/CD pipelines. CI/CD workflow implemented using Github actions, spinnaker and artifactory.
- DataDog for infra monitoring. Alert mechanisms for training and scoring jobs, cluster health, job status, workload, logs investigation(splunk).
- messaging queue

# LLM system design
Preparing for a machine learning system design interview, especially for a role focused on developing foundational Large Language Models (LLMs), requires a comprehensive understanding of several key areas. Here’s a structured plan to guide your preparation, along with some high-quality resources:

### Key Areas to Focus On

1. **Understanding LLM Architecture:**
   - Get a deep understanding of transformer models, especially architectures like GPT, BERT, and their variants.
   - Study the nuances of self-attention mechanisms, positional encodings, and multi-head attention.

2. **Training Large Models:**
   - Learn about the various stages of training large models, from data collection and preprocessing to model training and fine-tuning.
   - Understand distributed training techniques, handling large datasets, and optimizing training efficiency.

3. **Evaluation and Deployment:**
   - Familiarize yourself with evaluation metrics specific to language models, such as perplexity, BLEU scores, and human evaluation methods.
   - Understand the challenges and strategies for deploying large models, including serving infrastructure, latency, and cost optimization.

4. **Scalability and Optimization:**
   - Study techniques to scale LLMs, including model parallelism, data parallelism, and mixed precision training.
   - Explore methods for model compression and optimization, like distillation, pruning, and quantization.

5. **Ethical Considerations and Bias:**
   - Be aware of ethical implications, bias, and fairness issues in language models.
   - Understand methods for detecting and mitigating biases in training data and model outputs.

### Recommended Resources

#### Articles and Blogs
1. **Transformer Models and Architecture:**
   - [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) by Jay Alammar
   - [BERT Explained: What it is and how does it work?](https://towardsdatascience.com/bert-explained-state-of-the-art-language-model-for-nlp-f8b21a9b6270) by Rani Horev

2. **Training and Scaling Large Models:**
   - [Training Generative Recurrent Networks for Large Scale Language Modeling](https://openai.com/research/language-models) by OpenAI
   - [Efficient Large-Scale Language Model Training on GPU Clusters](https://research.fb.com/publications/efficient-large-scale-language-model-training-on-gpu-clusters/) by Facebook AI

3. **Evaluation and Deployment:**
   - [Evaluating Natural Language Processing Models](https://blog.exploratory.io/evaluating-natural-language-processing-models-cc8758a45c29) by Exploratory Blog
   - [Best Practices for Deploying Deep Learning Models](https://blog.tensorflow.org/2020/09/best-practices-for-deploying-deep-learning-models.html) by TensorFlow Blog

4. **Scalability and Optimization:**
   - [Model Parallelism in Deep Learning](https://medium.com/@theshanbhag/model-parallelism-in-deep-learning-50dbf486f347) by Shubham Shanbhag
   - [An Overview of Model Compression Techniques for Deep Learning](https://rpradeepmenon.medium.com/an-overview-of-model-compression-techniques-for-deep-learning-153a742e30e7) by R. Pradeep Menon

5. **Ethical Considerations and Bias:**
   - [Addressing Bias in Machine Learning](https://ai.googleblog.com/2019/05/addressing-bias-in-machine-learning.html) by Google AI Blog
   - [Fairness and Bias in AI: A Review](https://arxiv.org/abs/1908.09635) by Arvind Narayanan et al.

#### Books and Papers
- **Books:**
  - *Deep Learning* by Ian Goodfellow, Yoshua Bengio, and Aaron Courville
  - *Natural Language Processing with Transformers* by Lewis Tunstall, Leandro von Werra, and Thomas Wolf

- **Papers:**
  - [Attention is All You Need](https://arxiv.org/abs/1706.03762) by Vaswani et al.
  - [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) by Devlin et al.

#### Online Courses and Lectures
- [Stanford CS224N: Natural Language Processing with Deep Learning](http://web.stanford.edu/class/cs224n/)
- [DeepLearning.AI’s Natural Language Processing Specialization](https://www.coursera.org/specializations/natural-language-processing)

### Practical Experience

1. **Projects:**
   - Work on implementing LLMs using frameworks like Hugging Face Transformers or TensorFlow.
   - Try fine-tuning pre-trained models on specific tasks like text classification or summarization.

2. **Competitions:**
   - Participate in NLP competitions on platforms like Kaggle or DrivenData to get hands-on experience with real-world datasets.

### Mock Interviews and Discussions

1. **Mock Interviews:**
   - Schedule mock interviews with peers or use platforms like Pramp to simulate the interview environment.

2. **Discussion Forums:**
   - Engage in discussions on forums like Stack Overflow, Reddit’s r/MachineLearning, or specialized NLP communities.

By systematically studying these resources and gaining hands-on experience, you'll be well-prepared for your ML system design interview. Good luck!
