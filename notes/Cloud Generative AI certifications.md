# Introduction to Generative AI
1. Difference between generative and descriminative AI
2. What is prompt?
3. Model garden : Vertex AI foundational models.
4. Model garden : Task specific models.

# Introduction to Large Language Models
- Large Language models are trained on large datasets and have large number of parameters.
- PaLM - Pathways Language Models - leverages new pathway system
- LLM development which is using pre trained APIs needs you to know prompt engineering but not ML expertise.
- Question answering (QA) - Given a question in Natural Language, answer the question automatically. A sub field of NLP where domain knowledge is required.
- Generative QA generates the answer to the quesiton posed as a prompt without a domain knowledge but some context in the prompt.
- Prompt engineering vs Prompt design
- Types of LLMS : Generic LLMs, Instruction tuned, dialogue tuned
- Chain of thought reasoning - Start with the explanation on how to get the answer, model will be likely to give correct answer.
- Fine tuning the LLM - Finetune all model weights. Which might be very expensive.
- PETM : Parameter Efficient tuning methods. Prompt tuning.
- PALM api and makersuite.

# Attention Mechanism
- Attention mechanism is used in an encoder - decoder architecture
- It focuses on specific parts of the input sentence to generate output using weights.
- It involves creating context vector during encoding time which combines the hidden states and weights to each token.
- During decoding step, apart from hidden state the entire context vector is used to geneate the output.
