# Questionnaire

Purpose: `Test current LLM knowledge and reveal weak areas`
Status: `Reviewed`
Date: `06:17:2026`

---

Answer these in your own words. Short answers are fine. The point is to reveal weak areas.

## A. Tokens and input processing       `7.5/10 Good practical understanding; token vs embedding needs separation`

1. What is the difference between a word, a character, and a token?

    Answer

        Word: It is a collection of characters with a semantic meaning.
        Character: It is a symbol used in written language
        Token: It is the numerical representation, LLMs work with for inputs and outputs.

    Review

        Token is not exactly the numerical representation. The token is the unit/ID; the numerical vector is usually the embedding.
2. If two models receive the exact same visible text, can they produce different token sequences before inference starts? Why?

    Answer 

        Tokenization is deterministic, so if they use the same algorithms, then they could produce the same tokens and the sequence only depends on the input sequence, so if the input sequence is the same, the token sequence will be the same.

    Review

        Correct if same tokenizer and same chat template. Different models can produce different token sequence from the same visible text.

3. What extra hidden formatting can change the actual tokens a chat model receives?

    Answer

        Chat template.
        System inputs.
        Tokenization module.

    Review

        Good. Add: special tokens and role formatting can also change actual input
4. Why does stable JSON/key ordering matter for token counts and prefix caching?

    Answer 

        Tokens can be different for any minimal change, like letter case, blank spaces, etc.
        So, a well define structure and order, can make it easier to create the exact same part of an input, and if this input is in the same order at the start, then the model engine could caught prefix.

    Review

        Good. Small wording: the engine "catches" or "matches" prefix reuse only if runtime supports it.

## B. Prefill, decode, and KV cache     `7/10 Correct workflow direction; KV cache content needs precision`

1. What happens during prefill?

    Answer 

        Each input token is process through all layers. And the resulting key+value pairs on each layer are saved on the layer cache.  

    Review

        Good. More precise: prefill creates K/V tensors per attention layer for each prompt token.

2. What happens during decode?

    Answer 

        The output of the LLM is a prediction to the new token, that is an output token, this token is process through all layers, creating new key+value pairs, and changing the output to the next new output token.

    Review

        The generated token does not "change the output to the next token"; it is appended, processed, cached, then used to predict the next token.

3. Why can prefill be more parallel-friendly than output generation?

    Answer 

        On prefill you already have all of the tokens values, and on the processing of each token, the important reference is the token sequence before them, with the initial values that we already had.

        In comparison, each new output token, depends on the prefill KV values and KV values of the previous token. Basically the output token depends on the entire state of all layers, that is dependent on the exact token sequence.

    Review

        Good direction. Correction: prefill is parallel-friendly because all prompt positions are known, even though attention still uses causal masking.

4. Why does output generation usually happen one token at a time?

    Answer 

        Output generation is dependent on all of the available KV values on the LLM, for its queries and that includes the KV values added by each generated output token.

    Review

        Good. The missing phrase is: output token n+1 cannot be computed until output token n exists.

5. What does the KV cache store?

    Answer 

        It stores a tokenize representation of the result of the token query, in the specific context of the token sequence it was calculated with.

    Review

        KV cache does not store a "tokenized representation". It stores numerical K/V tensors generated from hidden states.

6. Why does the KV cache store K and V, but not usually old Q?

    Answer 

        Q is only necessary during the calculation of the V value, once this is calculated, it doesn't change.

    Review

        Q is not used to calculate the V value. Q is used to compare against K; old Q is usually not needed for future tokens.

7. Why is the same word/token not enough for KV cache reuse?

    Answer 

        Because the KV cache is token sequence dependent, that means it isn't enough that is the same value, it also needs to have the same prior sequence of tokens.

    Review

        Good.

8. When does a reusable prefix stop being reusable?

    Answer 

        When it changes. Even a minimal change makes it a different result, that you can't know how it will result, until it is prefill.

    Review

        Better: prefix reuse stops at the first different token ID, not just "when it changes" generally.

9. What is the difference between a semantic context block and a KV cache block?

    Answer 

        A semantic context block, is a block of information with identifiable meaning, like a prompt input. And a KV cache block is opaque and not easily classifiable. 

    Review

        Good.

10. Why is KV cache useful but not a durable memory system?

    Answer 

        It is useful to not have to do prefill of the same repeated information that is used during output generation and even during multiple calls in some cases.

        But it isn't mutable, it doesn't have a semantic meaning that could be understood, and it is extremely strict on the exact reuse conditions.

    Review

        Good.

## C. Attention basics      `3.5 Good Main weak area. Q/K/V is still fuzzy; heads/GQA/MQA need review`

1. In simple terms, what is a query?

    Answer 

        Is a search for useful values, that are use during the calculation of one or more values.

    Review

        Good analogy. More precise: Q is a vector representing what the current token/position is trying to attend to.

2. What is a key?

    Answer 

        A key is how a value declares what information it is providing.

    Review

        Good analogy.

3. What is a value?

    Answer 

        Numerical representation of the result of one or more queries on an exact previous context.

    Review

        Value is not the result of queries. Value is the information vector retrieved/weighted when attention selects that token.

4. What does an attention head do?

    Answer 

        Don't know

    Review

        An attention head is one parallel attention subspace/view that computes its own Q/K/V attention pattern.

5. What is the difference between query heads and KV heads?

    Answer 

        Query heads, is the number of queries a token can have. And KV heads, is the number of key+value pairs a token can have.

    Review

        Close but too literal. Query heads are parallel attention heads; KV heads are how many K/V groups are stored/shared.

6. Why do GQA/MQA reduce KV cache size?

    Answer 

        I don't recognize the abbreviations. But I suppose  you are referring to some kind of quantization, where the weights, values and calculations have a reduce number of bits.

    Review

        GQA/MQA are not quantization. They reduce KV cache size by sharing fewer K/V heads across more query heads.

## D. Training and adaptation       `7.5/10 Good LoRA/QLoRA level; LoRA runtime wording needs refinement`

1. What is the difference between full fine-tuning and LoRA?

    Answer 

        Full fine tuning, changes the weights of the entire LLM during training. And LoRA only some modules, and with an adapter, instead of directly changing the base model weights, so the model can still work the same if use without the adapter.

    Review

        Good.

2. During LoRA training, what is frozen and what is trainable?

    Answer 

        The whole base model is frozen. And the LoRA adapter weights is trainable.

    Review

        Good.

3. Does LoRA run through the whole model during inference?

    Answer 

        LoRA only runs in the adapter section, usually some specific layers.

    Review

        The whole model runs; LoRA computations only occur at the selected target modules.

4. Why can a small LoRA adapter affect model behavior even though most weights are frozen?

    Answer 

        Because the model behavior isn't define by a single section, instead it is distributed around all layers, so even when just changing an specific one, it usually has consequences on multiple behaviors.

    Review

        Good intuition. More precise: LoRA changes intermediate hidden states at strategic points, and those changes propagate through later layers.

5. What is the main purpose of QLoRA?

    Answer 

        QLoRA is used when there are hardware limitations during training.

    Review

        Good.

6. Does QLoRA produce a smaller base model, or does it make training possible with less memory?

    Answer 

        It makes training possible with less memory.

    Review

        Good.

7. Why should a QLoRA-trained adapter be recalibrated on the final deployment runtime?

    Answer 

        If it is used on the base model, it most likely will need to be recalibrated because it was trained on a quantized version of the model.

    Review

        Good. Add: deployment quantization/full precision/runtime format can change behavior, so recalibrate the exact deployed combination.

## E. Runtime-efficiency concepts       `5.5/10 Good intuition; sparsity/pruning/MoE mechanics need cleanup`

1. What is quantization trying to reduce?

    Answer 
    
        Memory use and calculation power needed.

    Review

        Mostly good. Better: quantization reduces memory/storage/bandwidth and can reduce compute cost if hardware/runtime supports it.

2. What are the main tradeoffs of quantization?

    Answer 

        Less precision and different behavior.

    Review

        Good.

4. What is the difference between quantizing model weights and quantizing the KV cache?

    Answer 

        Outside of one being on the model weights and the other in the KV cache. I'm not sure about the runtime implications.

        I suppose that on the case of the weights, the calculations needed are less demanding and precise.

        And in the cache case, there is less memory needed.

    Review

        Good uncertainty. Small correction: weight quantization mainly reduces model weight memory/bandwidth; KV quantization reduces memory used by long context/cache.

5. What is sparsity?

    Answer 

        Is when certain weights are zero or not use.

    Review

        Good.

6. Why does sparsity not automatically mean faster inference?

    Answer 

        Not suer, I thought its main risk was less quality.

    Review

        Key correction: sparsity only speeds inference if the runtime/hardware can skip sparse work efficiently.

7. What is pruning?

    Answer 

        Pruning is a type of sparsity where certain nodes are removed.

    Review

        Good enough, but say "weights/heads/layers/structures" instead of only "nodes".

8. Why is pruning risky for LLMs?

    Answer 

        It has the same risk as sparsity, it doesn't guarantee the same quality of results or some exact capabilities.

    Review

        Good.

9. What is MoE?

    Answer 

        Mixture of experts, is where the input is routed to certain modules/regions of the LLM. 

    Review

        Correction: MoE usually routes tokens to experts inside layers, not the whole input to separate LLMs.

10. Why can MoE reduce active compute but still require lots of memory? 

    Answer 

        It doesn't calculates the entire LLM nodes, but it could still load the entire LLM.

    Review

        Good.

11. Why is MoE interesting for your hardware constraints?

    Answer 

        Because the most difficult and expensive part to get of the hardware is the gpu and vram that are use to compute the LLM.

    Review

        Good.

## F. Workbench-specific understanding      `8/10 Strongest section; you're connecting this well to your architecture`

1. In your workbench, what should be stored in external memory instead of relying on model memory?

    Answer 

        Mutable working memory. Because of the dynamic nature of this memory, it can't be prefix and use across calls.

        Long lasting knowledge.

    Review

        Good idea, but refine: external memory should store durable facts, decisions, evidence, action gates, and current task state. Dynamic working memory may be suffix, not necessarily prefix.

2. Why should Track C/D context packets remain the source of truth instead of KV cache?

    Answer 

        KV cache isn't easily mutable, controlled or semantically classifiable.

    Review

        Good.

3. What parts of a workbench prompt should be stable prefix?

    Answer 

        Some examples I can think of are the next in the exact sequence.
        1. Artifacts templates.
        2. Architecture rules.
        3. Lasting instructions between calls.

        Lasting instructions between calls, should be between the lasts prefixs, because it is something more prone to change.        

    Review

        Good direction. Better stable prefix examples: protocol, schema, task objective, stable constraints, current accepted context snapshot. Anything prone to change should be versioned or moved later.

4. What parts should be dynamic suffix?

    Answer 

        Working memory. Given that this one is constantly changing on each call.

        This could be "next steps", "require changes", "ids", etc.


    Review

        Good.

5. How could training reduce runtime cost without making the model physically smaller?

    Answer 

        By reducing error margin. It prevents or reduces reruns or escalations.

    Review

        Good.

6. What would be a good first training target for your 14B model: general coding, context.evaluate, context.fold, or large-file patching? Why?

    Answer 

        Probably context.evaluate or context.fold
        Given that training for general coding, large-file or patching, probably would need a full fine-tuning, to actually improve the model capabilities.
        And on the other two cases, it could be improve by less example cases, and using LoRA.
        But I don't think I could explain this on a deeper level.

    Review

        Good decision. Small correction: general coding can sometimes improve with LoRA too, but it is harder to measure and needs broader data; context.evaluate/fold are better first because they are narrow, structured, and validator-friendly.

7. How would you know that training improved the model?

    Answer 

        You could use a deterministic evaluator that simply accepts or rejects the model output.

        Or you could use a human or better model, to grade on a more semantic level the output of the model.


    Review

        Good.

8. Why is “fewer retries per accepted operation” a runtime improvement?

    Answer 

        Each retry adds latency and on the case of paid models, cost.

    Review

        Good.