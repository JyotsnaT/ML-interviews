# LLM inference optimization
The LLM inference process involves 2 phases - 
1. Prefilling
   The input procesing phase of one token after another and storing intemediary stages. The operation is GPU intensive since this can be highly parallelized.
3. Decoding
   The LLM generates ouput token in a sequence where this output token need information from all previous states for generation. This is a memory bound operation and GPU is underutilized. 

## Basic optimization in the decoding phase

1. Batching
   For the multiple queries using the same model, they can all be processed together in a batch
2. Key-value caching
   Since the token during generation depends upon the Key-value tensor or KV tensors or self-attention tensors of all previous tokens, these KV tensors from past including prefilling stage are cached in GPU memory so they are not recomputed every time.
3. LLM memory requirements
   GPU LLM memory is primarily consumed by 2 components
   1. Model weights
   2. KV cache
      KV cache can exponentially grow in size since for each token in request the KV cache needs to be computed and can limit the thoughput. 
### Model parallelization
When the model's weights are too large to be contained by the memory of a device the model can be distributed over several machines. There are differnt ways of parallelizing the model based on how the model weights are split.
1. Pipeline parallelism
   The model is sharded vertically where each part is a quarter of the entire model and parts are connected in sequence.
   Large models can be processed well where the weights do not fit in one machine alone.
   However, this can result in 'pipeline bubbles' since some parts of the pipeline will be idle.
   To tackle this to some extent, batches are chunked into micro batches as well.
2. Tensor parallelism
   Then model is sharded horizontally where individual layers of the model are split to independent units those execute on different machines.
   Multi-headed self attention block: Different heads or group of heads can execute independently in parallel.
   MLP block: Weight matrices can be split so that outputs can be computed separately on same batch on different devices.
3. Sequence parallelism
   Spliting LayerNorm and DropuOut along the sequence dimension since these are inexpensive but memory intensive operations.
## Attention mechanism optimization

   

## References
1. [Mastering LLM Techniques: Inference Optimization](https://developer.nvidia.com/blog/mastering-llm-techniques-inference-optimization/)

# Model inference optimization

# Other general techniques
