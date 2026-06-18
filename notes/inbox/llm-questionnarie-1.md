# Questionnaire

Purpose: `Test current LLM knowledge and reveal weak areas`
Status: `Answered`
Date: `06:17:2026`

---

Answer these in your own words. Short answers are fine. The point is to reveal weak areas.

## A. Tokens and input processing

1. What is the difference between a word, a character, and a token?

    Answer 1

        Word: It is a collection of characters with a semantic meaning.
        Character: It is a symbol used in written language
        Token: It is the numerical representation, LLMs work with for inputs and outputs.

2. If two models receive the exact same visible text, can they produce different token sequences before inference starts? Why?

    Answer 1

        Tokenization is deterministic, so if they use the same algorithms, then they could produce the same tokens and the sequence only depends on the input sequence, so if the input sequence is the same, the token sequence will be the same.


3. What extra hidden formatting can change the actual tokens a chat model receives?

    Answer 1

        Chat template.
        System inputs.
        Tokenization module.

4. Why does stable JSON/key ordering matter for token counts and prefix caching?

    Answer 1

        Tokens can be different for any minimal change, like letter case, blank spaces, etc.
        So, a well define structure and order, can make it easier to create the exact same part of an input, and if this input is in the same order at the start, then the model engine could caught prefix.

## B. Prefill, decode, and KV cache

1. What happens during prefill?

    Answer 1

        Each input token is process through all layers. And the resulting key+value pairs on each layer are saved on the layer cache.  
2. What happens during decode?

    Answer 1

        The output of the LLM is a prediction to the new token, that is an output token, this token is process through all layers, creating new key+value pairs, and changing the output to the next new output token.
3. Why can prefill be more parallel-friendly than output generation?

    Answer 1

        On prefill you already have all of the tokens values, and on the processing of each token, the important reference is the token sequence before them, with the initial values that we already had.

        In comparison, each new output token, depends on the prefill KV values and KV values of the previous token. Basically the output token depends on the entire state of all layers, that is dependent on the exact token sequence.
4. Why does output generation usually happen one token at a time?

    Answer 1

        Output generation is dependent on all of the available KV values on the LLM, for its queries and that includes the KV values added by each generated output token.

5. What does the KV cache store?

    Answer 1

        It stores a tokenize representation of the result of the token query, in the specific context of the token sequence it was calculated with.

6. Why does the KV cache store K and V, but not usually old Q?

    Answer 1

        Q is only necessary during the calculation of the V value, once this is calculated, it doesn't change.
7. Why is the same word/token not enough for KV cache reuse?

    Answer 1

        Because the KV cache is token sequence dependent, that means it isn't enough that is the same value, it also needs to have the same prior sequence of tokens.
8. When does a reusable prefix stop being reusable?

    Answer 1

        When it changes. Even a minimal change makes it a different result, that you can't know how it will result, until it is prefill.

9. What is the difference between a semantic context block and a KV cache block?

    Answer 1

        A semantic context block, is a block of information with identifiable meaning, like a prompt input. And a KV cache block is opaque and not easily classifiable. 
10. Why is KV cache useful but not a durable memory system?

    Answer 1

        It is useful to not have to do prefill of the same repeated information that is used during output generation and even during multiple calls in some cases.

        But it isn't mutable, it doesn't have a semantic meaning that could be understood, and it is extremely strict on the exact reuse conditions.

## C. Attention basics

1. In simple terms, what is a query?

    Answer 1

        Is a search for useful values, that are use during the calculation of one or more values.
2. What is a key?

    Answer 1

        A key is how a value declares what information it is providing.
3. What is a value?

    Answer 1

        Numerical representation of the result of one or more queries on an exact previous context.
4. What does an attention head do?

    Answer 1

        Don't know
5. What is the difference between query heads and KV heads?

    Answer 1

        Query heads, is the number of queries a token can have. And KV heads, is the number of key+value pairs a token can have.
6. Why do GQA/MQA reduce KV cache size?

    Answer 1

        I don't recognize the abbreviations. But I suppose  you are referring to some kind of quantization, where the weights, values and calculations have a reduce number of bits.

## D. Training and adaptation

1. What is the difference between full fine-tuning and LoRA?

    Answer 1

        Full fine tuning, changes the weights of the entire LLM during training. And LoRA only some modules, and with an adapter, instead of directly changing the base model weights, so the model can still work the same if use without the adapter.
2. During LoRA training, what is frozen and what is trainable?

    Answer 1

        The whole base model is frozen. And the LoRA adapter weights is trainable.
4. Does LoRA run through the whole model during inference?

    Answer 1

        LoRA only runs in the adapter section, usually some specific layers.
5. Why can a small LoRA adapter affect model behavior even though most weights are frozen?

    Answer 1

        Because the model behavior isn't define by a single section, instead it is distributed around all layers, so even when just changing an specific one, it usually has consequences on multiple behaviors.
6. What is the main purpose of QLoRA?

    Answer 1

        QLoRA is used when there are hardware limitations during training.
7. Does QLoRA produce a smaller base model, or does it make training possible with less memory?

    Answer 1

        It makes training possible with less memory.
8. Why should a QLoRA-trained adapter be recalibrated on the final deployment runtime?

    Answer 1

        If it is used on the base model, it most likely will need to be recalibrated because it was trained on a quantized version of the model.

## E. Runtime-efficiency concepts

1. What is quantization trying to reduce?

    Answer 1
    
        Memory use and calculation power needed.
2. What are the main tradeoffs of quantization?

    Answer 1

        Less precision and different behavior.


4. What is the difference between quantizing model weights and quantizing the KV cache?

    Answer 1

        Outside of one being on the model weights and the other in the KV cache. I'm not sure about the runtime implications.

        I suppose that on the case of the weights, the calculations needed are less demanding and precise.

        And in the cache case, there is less memory needed.
5. What is sparsity?

    Answer 1

        Is when certain weights are zero or not use.
6. Why does sparsity not automatically mean faster inference?

    Answer 1

        Not suer, I thought its main risk was less quality.
7. What is pruning?

    Answer 1

        Pruning is a type of sparsity where certain nodes are removed.
8. Why is pruning risky for LLMs?

    Answer 1

        It has the same risk as sparsity, it doesn't guarantee the same quality of results or some exact capabilities.
9. What is MoE?

    Answer 1

        Mixture of experts, is where the input is routed to certain modules/regions of the LLM. 
10. Why can MoE reduce active compute but still require lots of memory? 

    Answer 1

        It doesn't calculates the entire LLM nodes, but it could still load the entire LLM.
11. Why is MoE interesting for your hardware constraints?

    Answer 1

        Because the most difficult and expensive part to get of the hardware is the gpu and vram that are use to compute the LLM.

## F. Workbench-specific understanding

1. In your workbench, what should be stored in external memory instead of relying on model memory?

    Answer 1

        Mutable working memory. Because of the dynamic nature of this memory, it can't be prefix and use across calls.

        Long lasting knowledge.
2. Why should Track C/D context packets remain the source of truth instead of KV cache?

    Answer 1

        KV cache isn't easily mutable, controlled or semantically classifiable.
3. What parts of a workbench prompt should be stable prefix?

    Answer 1

        Some examples I can think of are the next in the exact sequence.
        1. Artifacts templates.
        2. Architecture rules.
        3. Lasting instructions between calls.

        Lasting instructions between calls, should be between the lasts prefixs, because it is something more prone to change.        


4. What parts should be dynamic suffix?

    Answer 1

        Working memory. Given that this one is constantly changing on each call.

        This could be "next steps", "require changes", "ids", etc.
5. How could training reduce runtime cost without making the model physically smaller?

    Answer 1

        By reducing error margin. It prevents or reduces reruns or escalations.
6. What would be a good first training target for your 14B model: general coding, context.evaluate, context.fold, or large-file patching? Why?

    Answer 1

        Probably context.evaluate or context.fold
        Given that training for general coding, large-file or patching, probably would need a full fine-tuning, to actually improve the model capabilities.
        And on the other two cases, it could be improve by less example cases, and using LoRA.
        But I don't think I could explain this on a deeper level.
7. How would you know that training improved the model?

    Answer 1

        You could use a deterministic evaluator that simply accepts or rejects the model output.

        Or you could use a human or better model, to grade on a more semantic level the output of the model.
8. Why is “fewer retries per accepted operation” a runtime improvement?

    Answer 1

        Each retry adds latency and on the case of paid models, cost.