# Tokens (in AI/LLMs)

**Tags:** #AI #LLM #NLP #Tokenization

## Core Concept

In the context of Artificial Intelligence (AI), particularly **Large Language Models (LLMs)**, **Tokens** are the **fundamental units of text** that the model processes. Think of them as pieces of words, whole words, or even punctuation marks and characters that text is broken down into before the AI can understand or generate language. Models don't see raw text; they see sequences of these tokens, which are then typically converted into numbers (token IDs) [^1].

> **In essence:** Tokens are the building blocks, like Lego bricks, that AI models use to read, understand, and write text.

---

## In-Depth Information

### What is Tokenization?

**Tokenization** is the process of converting raw text into a sequence of tokens. It's a necessary first step because AI models operate on numerical data, not raw strings of characters [^1].

-   A program or algorithm called a **tokenizer** performs this process.
-   Each tokenizer has a predefined **vocabulary** – the set of all possible unique tokens it knows [^2].

### Why Use Tokens Instead of Words or Characters?

Using tokens, especially **subword tokens** (parts of words), offers several advantages:

1.  **Handling Complexity:** Subword tokens allow models to handle complex language, including new or rare words, typos, and different word forms, by breaking them down into known smaller pieces. This is more flexible than strict word-based tokenization (struggles with unknown words) or character-based tokenization (creates very long sequences) [^3][^4].
2.  **Efficiency:** Provides a good balance between vocabulary size (number of unique tokens) and sequence length (number of tokens per text piece), managing computational load effectively [^4].
3.  **Numerical Representation:** Enables conversion of text into sequences of numbers (token IDs), which are then transformed into **embeddings** (vector representations) capturing semantic meaning for the model [^1].

### Common Tokenization Methods

1.  **Word Tokenization:** Splits text based on spaces and punctuation. Simple but limited.
2.  **Character Tokenization:** Splits text into individual characters. Handles any word but creates long sequences.
3.  **Subword Tokenization:** (Most common in modern LLMs) Breaks words into smaller, meaningful units. Frequent words might be single tokens; rare words are broken down. Common algorithms include:
    *   **Byte-Pair Encoding (BPE):** Starts with characters/bytes, iteratively merges the most frequent pairs. Used by GPT models [^3][^5]. Byte-level BPE ensures any character can be represented.
    *   **WordPiece:** Similar to BPE, but merges pairs based on maximizing the likelihood of the training data. Used by BERT [^6].
    *   **SentencePiece:** Treats text as a raw sequence (including spaces), uses BPE or Unigram methods. Good for multilingual models. Used by T5, ALBERT [^7].

### Significance of Tokens

1.  **Model Input/Output Limits (Context Window):** LLMs have a maximum limit on the number of tokens they can process at once (e.g., 4096, 8192, 128k tokens). This "context window" affects how much information the model can consider or generate [^8].
2.  **Cost:** Many LLM APIs charge based on the number of tokens processed (input + output) [^9]. Understanding token count is crucial for cost management. *(Rough guide: ~4 characters or ~¾ of a word per token in English)*.
3.  **Performance and Behavior:** Tokenization choice impacts model performance, computational load, and sometimes causes unexpected behavior (e.g., issues with spelling, arithmetic) [^2].

### Example Tokenization

-   **Text:** `Tokenization is important!`
-   **Word Tokens (Example):** `["Tokenization", "is", "important!"]`
-   **Subword Tokens (Example - BPE):** `["Token", "ization", " is", " important", "!"]` *(Note: space often included in subsequent tokens)*
-   **Character Tokens:** `["T", "o", "k", "e", "n", "i", "z", "a", "t", "i", "o", "n", " ", "i", "s", " ", "i", "m", "p", "o", "r", "t", "a", "n", "t", "!"]`
-   **Numerical Representation (Example Token IDs):** `[23 TokenID, 45izationID, 67isID, 89importantID, 101!ID]` (Actual IDs depend on the specific tokenizer vocabulary).

---

## Sources

[^1]: Vaswani, A., et al. (2017). *Attention Is All You Need.* (While focusing on the Transformer architecture, tokenization and embeddings are fundamental prerequisites). [https://arxiv.org/abs/1706.03762](https://arxiv.org/abs/1706.03762)
[^2]: Hugging Face Documentation. *Summary of the tokenizers.* Accessed April 22, 2025. [https://huggingface.co/docs/transformers/main_classes/tokenizer](https://huggingface.co/docs/transformers/main_classes/tokenizer)
[^3]: Sennrich, R., Haddow, B., & Birch, A. (2016). *Neural Machine Translation of Rare Words with Subword Units.* (Introduced BPE for NLP). [https://arxiv.org/abs/1508.07909](https://arxiv.org/abs/1508.07909)
[^4]: OpenAI Documentation. *What are tokens and how to count them?* Accessed April 22, 2025. [https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them)
[^5]: Karpathy, A. (Blog Post). *The unreasonable effectiveness of Recurrent Neural Networks*. (Provides context on character-level vs. word-level, relevant background for subword motivation). Accessed April 22, 2025. [http://karpathy.github.io/2015/05/21/rnn-effectiveness/](http://karpathy.github.io/2015/05/21/rnn-effectiveness/) (Illustrative, not BPE specific). *See also GPT-2/3 papers for BPE usage.*
[^6]: Devlin, J., Chang, M. W., Lee, K., & Toutanova, K. (2019). *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.* (Mentions use of WordPiece). [https://arxiv.org/abs/1810.04805](https://arxiv.org/abs/1810.04805)
[^7]: Kudo, T., & Richardson, J. (2018). *SentencePiece: A simple and language independent subword tokenizer and detokenizer for Neural Text Processing.* [https://arxiv.org/abs/1808.06226](https://arxiv.org/abs/1808.06226)
[^8]: Various LLM Documentation (e.g., OpenAI, Anthropic, Google AI). Context window limits are specified in model documentation and API references. (Example: OpenAI Models page accessed April 22, 2025. [https://platform.openai.com/docs/models](https://platform.openai.com/docs/models))
[^9]: OpenAI API Documentation. *Pricing.* Accessed April 22, 2025. [https://openai.com/pricing](https://openai.com/pricing) (Illustrates token-based pricing).