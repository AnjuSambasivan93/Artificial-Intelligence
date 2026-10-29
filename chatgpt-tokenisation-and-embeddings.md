# ChatGPT: Tokenisation and Embeddings

## 1. What Is Tokenisation?

Tokenisation is the process of breaking text into smaller units called **tokens** so that a neural network can process them.

Tokens can represent complete words, parts of words, punctuation or spaces combined with text.

**Example:**

Original sentence:

`I love cats.`

Illustrative tokens:

`["I", " love", " cats", "."]`

Each token is assigned a numerical identifier called a **token ID**.

| Token | Example token ID |
|---|---|
| I | 10 |
| love | 25 |
| cats | 48 |
| . | 7 |

The sentence is represented as:

`[10, 25, 48, 7]`

These IDs are illustrative, not actual ChatGPT token IDs.

### Technology Used: Byte Pair Encoding (BPE)

GPT-family models use tokenisation techniques based on Byte Pair Encoding.

BPE builds a vocabulary by repeatedly merging frequently occurring adjacent text units. Common sequences may become single tokens, while less common words may be divided into multiple tokens.

OpenAI provides a tokenizer library called **tiktoken**.

## 2. Why Are Token IDs Not Enough?

A token ID is simply a numerical identifier.

For example:

- `48` represents "cats".
- `52` represents "dogs".
- `89` represents "car".

These numbers do not describe the meaning of the tokens.

The number 48 does not mean that "cats" is more important than "dogs".

The neural network therefore needs a different numerical representation.

## 3. What Are Embeddings?

An **embedding** is a numerical vector representing a token.

The embedding layer uses each token ID to look up a vector in a learned embedding table.

**Example:**

| Token | Token ID | Illustrative embedding |
|---|---|---|
| cat | 48 | [0.2, 0.8, -0.3] |
| dog | 52 | [0.3, 0.7, -0.2] |
| car | 89 | [-0.6, 0.1, 0.9] |

These are invented three-dimensional vectors. Real GPT embeddings contain many more numerical dimensions.

Embeddings provide representations that the transformer can use for mathematical calculations.

## 4. How Are Embedding Values Created?

The embedding table is part of the neural network's trainable parameters.

At the beginning of training, embedding values are typically initialised with small random numbers.

Initially, these values do not contain useful learned relationships.

During training, the values are gradually adjusted.

### Example Training Sentences

- "The cat eats food."
- "The dog eats food."
- "The cat is an animal."
- "The dog is an animal."
- "The car needs fuel."

The model uses the embeddings and other neural-network parameters to predict tokens.

For example:

Input: `The cat eats`

Expected next token: `food`

If the model assigns a low probability to the correct next token, the training system calculates a prediction error.

## 5. How Do Embeddings Improve During Training?

Three important processes are involved:

1. **Loss function:** Measures how poorly the model predicted the correct tokens.
2. **Backpropagation:** Calculates gradients showing how changes to model parameters would affect the loss.
3. **Optimiser:** Uses the gradients to update the embedding values and other neural-network weights.

**Illustrative embedding update:**

Before training update:

`cat = [0.12, -0.08, 0.31]`

After training update:

`cat = [0.13, -0.06, 0.29]`

These numbers are examples only. Actual updates depend on the calculated gradients and optimiser.

The process repeats across many training batches.

## 6. How Does the Model Learn Relationships?

Words and tokens that occur in similar contexts may develop representations that capture related patterns.

For example, "cat" and "dog" often occur in sentences involving animals, food and behaviour.

Through repeated training, their embeddings may reflect some of these similarities.

However, the model is not directly instructed to make these embeddings similar. The values are learned by improving token predictions.

Meaning and context are also represented through the transformer's later layers, not only through the initial embeddings.

## 7. What Happens When ChatGPT Receives a User Question?

When a user types a question into ChatGPT:

1. The tokenizer breaks the text into tokens.
2. Each token is converted into a token ID.
3. The embedding layer retrieves the learned vector for each token ID.
4. The embeddings are passed into the transformer neural network.
5. The transformer processes the available context and generates output tokens.

During normal inference, ChatGPT uses its already-learned embeddings rather than creating new random values or retraining them for each question.

## Process Summary

**Text → Tokenisation → Token IDs → Embedding Lookup → Numerical Vectors → Transformer**

During training:

**Prediction → Loss Calculation → Backpropagation → Optimiser → Updated Embeddings and Weights**

## Key Understanding

- **Tokenisation** converts text into smaller pieces and numerical IDs.
- **Embeddings** convert token IDs into learned numerical vectors.
- **Training** adjusts embedding values to improve the model's predictions.
- **Inference** uses the learned embeddings to process new user questions.

Tokenisation and embeddings are the first major stages of preparing text for processing by a GPT-style transformer neural network.

## References

- OpenAI. *tiktoken — Fast BPE Tokeniser*. https://github.com/openai/tiktoken
- OpenAI. *What Are Tokens and How to Count Them?* https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them
- Vaswani et al. (2017). *Attention Is All You Need*. https://arxiv.org/abs/1706.03762
- Brown et al. (2020). *Language Models are Few-Shot Learners*. https://arxiv.org/abs/2005.14165
