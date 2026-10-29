# ChatGPT Training Process: After Data Cleaning

## 1. Storing Cleaned Training Data

After data collection and cleaning, the prepared text is stored in large-scale storage systems within data-centre infrastructure.

Distributed storage allows large datasets to be stored across multiple devices or servers. The training system reads data from storage and transfers smaller portions to computing resources for processing.

**Examples of relevant technologies:**
- Distributed file systems and object storage, such as Azure Blob Storage
- Python for data processing
- Apache Spark for large-scale distributed data processing

OpenAI documented using Apache Spark in its GPT-3 data preparation process. The exact storage and processing technologies used for current ChatGPT models are not fully disclosed.

## 2. Preparing the Training Dataset

The stored documents are organised and selected for training. Data may be sampled from different sources, but it does not need to be separated into individual subjects such as science, history or mathematics.

The model learns from text covering many topics.

## 3. Tokenisation

The cleaned text is converted into smaller units called **tokens**.

Tokens may represent words, parts of words or punctuation. Each token is assigned a numerical ID.

**Example:**

Original text:
`Machine learning uses data.`

Illustrative tokens:
`["Machine", " learning", " uses", " data", "."]`

These token IDs become the numerical input used by the model.

**Technology:** Byte Pair Encoding (BPE) is a tokenisation technique used in GPT-family models. OpenAI also provides the `tiktoken` library.

## 4. Creating Training Sequences and Batches

Token IDs are organised into sequences while preserving their order.

Multiple sequences are grouped into **batches**, allowing GPUs to process many training examples efficiently.

The entire training dataset is not loaded into a GPU at once. Smaller batches are processed repeatedly.

**Technologies:** Data-loading pipelines, batching software and distributed training systems.

## 5. Processing Data Through the Transformer

The token IDs are converted into numerical vectors called **embeddings**.

These embeddings are processed by the transformer neural network.

The transformer uses **self-attention** to identify relationships between tokens within the available context.

**Main technologies:**
- Transformer neural network architecture
- Embedding layers
- Causal self-attention
- GPUs for parallel numerical computation
- Deep-learning frameworks such as PyTorch

## 6. Predicting the Next Token

During pretraining, the model learns by predicting the next token in a sequence.

**Example training sentence:**

`The capital of New Zealand is Wellington.`

The model uses preceding tokens to predict the next token.

For example:

Input: `The capital of New Zealand is`

Expected next token: `Wellington`

In practice, the transformer can learn from predictions at many positions in a training sequence. Causal masking prevents each position from accessing future tokens.

The model does not require manually prepared incomplete sentences.

## 7. Calculating Errors and Updating Weights

The model compares its predictions with the actual next tokens from the training text.

Three important processes are involved:

- **Loss function:** Measures the prediction error, commonly using cross-entropy loss.
- **Backpropagation:** Calculates gradients showing how the model's parameters contributed to the error.
- **Optimiser:** Updates the model's numerical weights to improve future predictions.

Optimisers such as Adam or AdamW are commonly used in large-scale neural-network training.

This process is repeated across many batches of training data.

## 8. Saving Model Checkpoints

During training, the system periodically saves checkpoints containing model weights and other information needed to continue training.

These checkpoints are stored in persistent storage.

After initial pretraining, additional training stages may include supervised fine-tuning and preference-based optimisation to improve instruction following and conversational responses.

## Training Process Summary

1. **Cleaned data storage** — Store prepared documents in large-scale storage systems.
2. **Dataset preparation** — Organise and select training data.
3. **Tokenisation** — Convert text into numerical token IDs.
4. **Batching** — Group token sequences for efficient processing.
5. **Embeddings** — Convert token IDs into numerical vectors.
6. **Transformer processing** — Analyse token relationships using attention.
7. **Next-token prediction** — Predict tokens based on preceding context.
8. **Loss calculation** — Measure prediction errors.
9. **Backpropagation and optimisation** — Update neural-network weights.
10. **Repeat and checkpoint** — Continue training and save progress.

## Key Understanding

ChatGPT does not learn by simply storing documents or organising information into topic folders.

During pretraining, the transformer learns statistical patterns and relationships from text by repeatedly predicting tokens and updating its numerical parameters.

The core training process is:

**Cleaned Data → Storage → Tokenisation → Batching → Embeddings → Transformer → Prediction → Loss → Weight Updates**

The exact implementation details of current ChatGPT models are proprietary, but this describes the established principles of GPT-style language-model pretraining.

## References

- Vaswani et al. (2017). *Attention Is All You Need*. https://arxiv.org/abs/1706.03762
- Brown et al. (2020). *Language Models are Few-Shot Learners*. https://arxiv.org/abs/2005.14165
- OpenAI. *GPT-4 Technical Report*. https://arxiv.org/abs/2303.08774
- OpenAI. *tiktoken*. https://github.com/openai/tiktoken
