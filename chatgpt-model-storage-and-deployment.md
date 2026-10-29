# ChatGPT: Model Storage and Deployment After Training

## 1. What Happens After Training?

After training, the neural network contains learned numerical parameters called **weights**.

These weights are adjusted during training to help the model recognise patterns and relationships in text.

The trained model is then saved so it can be evaluated, improved and eventually deployed.

## 2. Where Is the Trained Model Stored?

The trained model is saved in **persistent storage systems** within cloud or data-centre infrastructure.

The saved model typically includes:

- **Model weights:** Numerical parameters learned during training.
- **Model configuration:** Information about the neural network architecture.
- **Tokenizer information:** Rules and vocabulary used to convert text into tokens.
- **Training checkpoints:** Saved training states that may also include optimiser information.

Distributed file systems and cloud object storage are examples of technologies used for storing large AI models.

The exact storage technologies and locations used for current ChatGPT models are not publicly disclosed.

## 3. What Happens Before Deployment?

Initial pretraining is not necessarily the final stage of model development.

Additional stages may include:

- **Supervised fine-tuning:** Training the model using examples of desired responses.
- **Preference-based optimisation:** Improving responses using human or other feedback signals.
- **Safety testing and evaluation:** Assessing model capabilities, limitations and potential risks.

These stages help prepare the model for use as a conversational AI assistant.

## 4. Model Deployment

Deployment means making a trained model available for real-world use.

A selected model is loaded from persistent storage into the memory of servers equipped with GPUs or other AI accelerators.

These servers run the model and process incoming user requests.

**Relevant technologies:**
- Data-centre and cloud infrastructure
- GPUs and AI accelerators
- Model-serving software
- Networking and request-management systems

## 5. Inference: How ChatGPT Answers Questions

Once deployed, ChatGPT performs **inference**.

Inference means generating responses using an already-trained model rather than updating its weights through training.

**Example:**

User question: `What is machine learning?`

The process is:

1. The user's question is sent to ChatGPT's servers.
2. A tokenizer converts the text into token IDs.
3. The trained transformer processes the tokens using its learned weights.
4. The model generates output tokens.
5. The output tokens are converted into readable text.
6. The response is returned to the user.

The model normally generates responses using its learned parameters rather than searching the original training documents. Separate tools, such as web search or document retrieval, may provide additional information when enabled.

## 6. Training vs Inference

| Training | Inference |
|---|---|
| Uses training datasets | Uses the user's input |
| Predicts tokens and calculates training loss | Generates response tokens |
| Updates neural-network weights | Normally keeps weights unchanged |
| Requires substantial computing resources | Uses deployed computing resources |
| Develops the model | Uses the trained model |

## 7. Complete ChatGPT Development Process

1. **Data collection** — Gather training data from permitted sources.
2. **Data cleaning** — Filter, deduplicate and prepare the data.
3. **Data storage** — Save the prepared training dataset.
4. **Tokenisation** — Convert text into numerical token IDs.
5. **Pretraining** — Train the transformer through next-token prediction.
6. **Post-training** — Improve instruction following, usefulness and safety.
7. **Model storage** — Save trained weights and related model files.
8. **Evaluation** — Test model performance and safety.
9. **Deployment** — Load the selected model onto inference servers.
10. **Inference** — Process user requests and generate responses.

These stages may overlap or repeat during model development.

## Key Understanding

The original training data and the trained model are different.

**Training data** consists of documents and other material used during learning.

**Model weights** are numerical parameters adjusted through training.

After training, the weights are saved in persistent storage. During deployment, the trained model is loaded onto computing hardware to generate responses.

**Overall process:**

Training Data → Neural Network Training → Learned Weights → Model Storage → Deployment → Inference → User Response

## References

- OpenAI. *Introducing ChatGPT*. https://openai.com/index/chatgpt/
- OpenAI. *GPT-4 Technical Report*. https://arxiv.org/abs/2303.08774
- OpenAI. *Learning from Human Preferences*. https://openai.com/index/learning-from-human-preferences/
- Vaswani et al. (2017). *Attention Is All You Need*. https://arxiv.org/abs/1706.03762
