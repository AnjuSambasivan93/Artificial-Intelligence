# ChatGPT: How the Transformer and Attention Work

## 1. What Is a Transformer?

A **Transformer** is a type of neural network architecture used in ChatGPT.

Its main job is to process token representations, use information from the available context and help predict the next token.

Before text reaches the Transformer, it goes through two important stages:

1. **Tokenisation:** Text is broken into tokens and converted into token IDs.
2. **Embeddings:** Each token ID is converted into a learned vector of numbers.

**Example:**

Sentence: `The cat drinks milk.`

Illustrative embeddings:

| Token | Embedding vector |
|---|---|
| The | [0.1, 0.3] |
| cat | [0.8, 0.2] |
| drinks | [0.4, 0.6] |
| milk | [0.1, 0.9] |

These numbers are invented for explanation. Real models use much larger vectors.

The Transformer receives these numerical representations along with positional information.

## 2. Why Does the Transformer Need Attention?

Consider this sentence:

**"The cat drank milk because it was thirsty."**

The word **"it"** most likely refers to **"cat"**.

To process this relationship, the model needs to use information from other parts of the sentence.

This is where **attention** becomes useful.

Attention allows the Transformer to combine information from different token positions.

It does this using mathematical calculations rather than manually written grammar rules.

## 3. What Are Query, Key and Value?

The Transformer creates three numerical representations for each token:

- **Query (Q):** Used to determine which token positions are relevant.
- **Key (K):** Used to calculate how well a token matches a Query.
- **Value (V):** Contains information that can be combined into the attention result.

These are vectors of numbers, not actual questions, keywords or sentences.

The model creates Q, K and V by multiplying token representations by three different learned weight matrices.

The matrices are called:

- Query weight matrix: `W_Q`
- Key weight matrix: `W_K`
- Value weight matrix: `W_V`

The values in these matrices are learned during model training.

## 4. How Does Attention Actually Work?

Attention can be understood in four simple steps.

### Step 1: Create Query, Key and Value Vectors

Imagine the model is processing the word **"it"**.

For a simplified example, suppose:

Query for "it":

`[1, 1]`

Keys for earlier tokens:

| Token | Key vector |
|---|---|
| cat | [2, 1] |
| milk | [0, 1] |

All these numbers are invented.

### Step 2: Calculate Matching Scores

The Transformer compares the Query with each Key using a mathematical operation called a **dot product**.

A dot product multiplies corresponding numbers and adds the results.

For "cat":

`(1 × 2) + (1 × 1) = 3`

For "milk":

`(1 × 0) + (1 × 1) = 1`

The results are:

| Token | Matching score |
|---|---|
| cat | 3 |
| milk | 1 |

In this example, "cat" has a higher matching score than "milk".

The actual attention mechanism also scales these scores before converting them into weights.

### Step 3: Convert Scores into Attention Weights

The Transformer uses a mathematical function called **softmax**.

Softmax converts matching scores into attention weights that add up to 100%.

For illustration, suppose the weights are:

| Token | Example attention weight |
|---|---|
| cat | 80% |
| milk | 20% |

These percentages are simplified examples, not exact results calculated from the scores above.

This means that, in our example, information from "cat" will contribute more strongly to the attention result.

In real attention, the model considers all permitted token positions, not just these two words.

### Step 4: Combine the Value Vectors

The Transformer uses the attention weights to combine Value vectors.

Imagine:

Value for "cat": `[1, 0]`

Value for "milk": `[0, 1]`

Using the example weights:

`80% × [1, 0] + 20% × [0, 1]`

Result:

`[0.8, 0.2]`

This new vector contains a larger contribution from "cat" than from "milk".

The result is then used in further neural-network calculations.

**Important:** The Transformer does not literally write "it = cat" inside the model. It processes numerical information that can help represent relationships between tokens.

## 5. What Is Self-Attention?

The process described above is called **self-attention**.

It is called self-attention because tokens are compared with other tokens in the same input sequence.

For example:

"The cat drank milk because it was thirsty."

When processing "it", attention can use information from earlier tokens such as "cat", "drank" and "milk".

This helps the model build context-dependent representations.

## 6. What Is Causal Masking?

ChatGPT uses a GPT-style **decoder-only Transformer**.

During next-token prediction, it uses causal attention.

Causal masking prevents a token position from accessing future token positions.

For example:

Sentence: `The cat drinks milk`

When processing "drinks", the model can attend to:

- "The"
- "cat"
- "drinks"

But it cannot attend to the future token "milk" at that position.

This prevents the model from using future answers during next-token prediction.

## 7. What Happens After Attention?

Attention is only one part of a Transformer block.

A GPT-style Transformer also contains:

**Multi-head attention:** Multiple attention heads perform different learned attention calculations. These can capture different relationships in the text.

**Feed-forward neural network:** Further transforms the numerical representation of each token.

**Residual connections:** Help preserve and pass information through the network.

**Normalisation:** Helps maintain stable numerical processing.

These operations are repeated through multiple Transformer blocks.

The final token representations are used to calculate scores for possible next tokens.

## 8. How Does the Transformer Learn Attention?

The Query, Key and Value weight matrices are not manually programmed with language rules.

They are learned during training.

The process works as follows:

1. The model receives token sequences.
2. Embeddings and Transformer layers process the tokens.
3. The model predicts the next tokens.
4. A loss function measures prediction errors.
5. Backpropagation calculates gradients.
6. An optimiser updates the model's weights, including the Query, Key and Value matrices.
7. The process repeats across many training examples.

Over time, the Transformer learns numerical patterns that help improve predictions.

The attention weights are calculated dynamically for each input using the learned parameters.

## 9. Complete Process

**When ChatGPT receives text:**

`User text`

↓

`Tokenisation`

↓

`Token IDs`

↓

`Embedding vectors + positional information`

↓

`Transformer`

↓

`Query, Key and Value calculations`

↓

`Attention scores and weights`

↓

`Weighted combination of Value vectors`

↓

`Further Transformer processing`

↓

`Next-token prediction`

The model repeats the generation process to produce additional tokens and build a response.

## 10. Key Points to Remember

- **Transformer:** The neural network architecture that processes token representations.
- **Attention:** A mathematical method for combining information from different token positions.
- **Query:** Used to find relevant token information.
- **Key:** Used to calculate a matching score.
- **Value:** Supplies the numerical information being combined.
- **Softmax:** Converts attention scores into weights.
- **Causal masking:** Prevents access to future tokens during next-token prediction.
- **Training:** Learns the weights used in attention and other Transformer calculations.

### Simple Summary

Embeddings give each token a numerical representation.

Attention helps the Transformer combine information from different tokens.

The Transformer processes these representations through multiple layers and uses the resulting information to predict the next token.

## References

- Vaswani, A., et al. (2017). *Attention Is All You Need*. https://arxiv.org/abs/1706.03762
- Radford, A., et al. (2018). *Improving Language Understanding by Generative Pre-Training*. https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf
- Brown, T., et al. (2020). *Language Models are Few-Shot Learners*. https://arxiv.org/abs/2005.14165
