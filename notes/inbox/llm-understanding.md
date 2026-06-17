# LLM Models Understanding

Purpose: `Write reviewable current understanding of LLM models.`
Status: `Initial draft - v1`
Date: `06:17:2026`

---

## Concept

A LLM or large language model, is a neural or layers of neural networks, trained to predict what is next on a semantic input. In this sense, LLMs don't really think in the human sense of the word, they just predict what is the most likely response that makes sense from its trained weights and the input.


A better model (LLM) is usually the result of a bigger neural network trained on a large amount of examples of good quality.


## Tokens

LLMs don't see their input as words, letters or semantic meanings. They divide the input on tokens, the definition of these tokens depends on the algorithm and formula use, and its usually model family specific.

## Tokens Vector

Each token is usually transform to a numerical array representation.

## Prefill

The tokens are pass through all of the layers of the LLM, usually in parallel, where each token can query the values of the previous tokens to recalculate its own value. 

They can be process in parallel, because their value only depends on the original values of the sequence of tokens before them.

    token 1 -> 
    token 1 + token 2 ->
    token 1 + token 2 + token 3 ->
    ...
This doesn't mean that the value of previous tokens is necessarily use, it just means that the current calculated token can see the previous tokens for its queries, and if one match it can use the value in the recalculation.

### Q/K/V

As mention before each token does a query or multiple queries, that is represent as Q, each query could be pair with one personal key+value pair or share the key+value pair with other queries.
In that sense a single token could generate multiple key+values pair.

Example:

One key+value pair per query. 

    Q: 32 K: 32 V:32
Queries share key+value pair.

    Q: 32 K: 8 V: 8

This process is repeated per layer, and generates key+value pairs per layer, the number of these pair per token is called KV heads.

### KV cache

Each key+value pair generated at each layer, is saved on the specific layer cache, so if the exact same token is needed, then it could be reuse. But because of their sequence dependant nature, the reuse is very strict.

## Generative Output

After the prefill, the LLM creates what it predicts to be the most probable next token, this token also needs to pass through all the layers, to create its own KV cache values, then the LLM creates the new token prediction and repeats the same process, until it is stop either by a stop token, or something external.

## Cache Reuse

Cache reuse is needed on the generative output, but after the call ends, there isn't any guarantee that the next call will make use of cache reuse. 
And actually without a define structure, it is pretty difficult for the next call to make use of it, because from the point a token doesn't match the exact same value and position as in the previous call, those token won't be able to use any of the previous call cache.

### Preffix/Suffix

For cross-call cache reuse, there exist preffix and suffix. Where preffix is the stable exact same input that wants to be reuse, and suffix is the dynamic input.

Example:

    call 1: [preffix A] [suffix A]
    call 2: [preffix A] [suffix B]

In the previous example, because the exact same input (preffix A) is enter with the same value and the same position on both calls, it doesn't need to be prefill again on the second call. If the LLM engine can caught preffixs.

## Runtime Heaviness Improvement

There exist various methods to reduce a LLM process requirements, but a lot of these have important tradeoffs.

### Quantization

The most straight forward way to reduce a LLM process requirements, is to reduce the nodes numerical precision, which reduces the calculations precision. This is usually done by changing the values, from float point 16 bytes number, to 8, 7, 6, 5, or 4 bits numbers.

The obvious result is less power needed on calculations, but also less precision on the results of the model.

Quantization can also be done on the KV cache specifically, to reduce memory.
### Sparsity

On runtime a LLM runs all of its layers, requiring all of the nodes calculations per token. But not always all of these nodes have an equal importance on all of the tokens calculated. That is way the concept of sparsity exists.
Where some nodes are zero or not use, resulting in less calculations needed.

### Pruning

Pruning is a type of sparsity, where parts of the layers consider not necessary are completely remove. But this is extremely risky, because the knowledge and native skills of a LLM are distributed across each different nodes weights and even layers.

Here there are two cases where you could be using pruning.

- When you are trying to remove irrelevant nodes, that could be not really contributing anything to the LLM.
- When you want to create a reduce LLM that specializes in some kind of topic/task.

### MoE

Mixture of Experts also tries to reduce needed calculations, by running less nodes, but it tries to not compromise on the LLMs capabilities, by using multiple specialize LLMs.
This setup creates the necessity of a router, that can route the prompt to the correct LLM.

Flexibility could be lost on this setup, and it doesn't necessarily guarantees that the whole model won't be load.

## Training

As neural network, LLM define its internal behavior by the neural network nodes weights. So, to change this behavior, you need to practically change the weights of the nodes.

### LoRA

Low Rank Adapter, is a technique of fine-tunning specific regions of the LLM by adding and adapter, that only changes the regions of interest.
The base model is kept the same, but during training the adapter weights are fine tuned, so if the LLM is use with the adapter, then its internal behavior will be different. 

### QLoRA

Quantization LoRA, is basically the same as LoRA, but it reduces the hardware requirements of the training, by doing the training on a quantize version of the LLM. That doesn't mean you need to run the adapter with a quantize LLM, you could still try to use it on the same base model, but it would most likely need some testing.

### Distillation

On distillation, you try to make a less capable model, learn from a more capable one, by training it on the behavior of the more capable one.
