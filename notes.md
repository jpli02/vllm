# vLLM code structure

## Modules
* Entry point (LLM, API server)
* Engine
* Scheduler
* KV cache manager
  * Paged Attention (LMcache, prodcution stack)
* Evictor
  * **Prefix caching**
  * KV cache optimization
    * Deepseek MLA
* Worker
* Model executor (Model runner)
* Modelling
  * Llama is a good start: vllm/model_executor/models/llama.py
* Attention backend
  * FlashAttention: different kernel for PD

## Feature
* distributed inference
  * TP, DP, PP: vllm/distributed/parallel_state.py
* sepculative decoding
  * ngram
  * egales
  * online sd
  * code: vllm/spec_decode/medusa_worker.py

## Tricks
* 1B parameter model -> 2GB