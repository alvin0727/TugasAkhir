# Phishing Website Classification Using CNN and Multi-Head Attention

This project aims to classify phishing websites using a combination of **Convolutional Neural Network (CNN)** and **Multi-Head Attention**. Preprocessing is carried out to prepare the URL data before being fed into the model.

--- 

## Preprocessing

The preprocessing process is done in several stages:

1. **Tokenization**:
   - The URL is broken down into a list of individual characters.
   - Example: `"https://example.com"` will be transformed into `['h', 't', 't', 'p', 's', ':', '/', '/', 'e', 'x', 'a', 'm', 'p', 'l', 'e', '.', 'c', 'o', 'm']`.

2. **Encoding**:
   - Each character is converted into an integer representation using a predefined character dictionary.
   - Unknown characters are encoded as a special value `UNK`.
   - Example: `'a'` will be encoded as `1`, `'A'` as `27`, and `'0'` as `53`.

3. **Padding or Truncating**:
   - The encoded URL is processed to have a fixed length (`max_length`).
   - If the URL is longer than `max_length`, it will be truncated.
   - If the URL is shorter than `max_length`, padding with a default value (`0`) will be added.
   - Example: If `max_length = 50`, the URL will be processed to a length of 50 characters.

---

## Model Architecture

This model uses a combination of **CNN** and **Multi-Head Attention** with the following architecture:

1. **Embedding Layer**:
   - Converts the integer representations of the URL characters into embedding vectors.
   - The embedding dimension (`embedding_dim`) can be adjusted.

2. **Positional Encoding**:
   - Adds positional information of characters in the sequence using sinusoidal encoding.
   - Helps the model understand the order of characters in the URL.

3. **Attention Block**:
   - Uses **Multi-Head Attention** to capture relationships between characters in the URL.
   - Equipped with residual connections to preserve original information.

4. **Feature Block**:
   - Uses a **Convolutional Layer (Conv1D)** to extract local features from the character sequence.
   - Equipped with residual connections to combine information from previous layers.

5. **Output Block**:
   - Combines the outputs of the **Attention Block** and **Feature Block**.
   - Uses **Multi-Head Attention** again to strengthen relationships between the extracted features.
   - The output is flattened and passed through a dense layer to generate the final prediction.
   - Sigmoid activation is used for binary classification (phishing or not phishing).

---

## Proposed Hyperparameters

- **Embedding Dimensions**: `[64, 128, 256]`
- **Batch Sizes**: `[32, 64, 128]`
- **Learning Rates**: `[1e-5, 2e-5, 3e-5]`
- **Number of Epochs**: `[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]`

---

## Dataset

The dataset consists of labeled phishing and non-phishing URLs. The data undergoes preprocessing before being fed into the model.
The dataset is sourced from the **Aalto University’s research portal**:
[Phishing URL Dataset](https://research.aalto.fi/en/datasets/phishstorm-phishing-legitimate-url-dataset)

---

## Results

### Confusion Matrix

|                   | Predicted Negative | Predicted Positive |
|-------------------|-------------------|-------------------|
| **Actual Negative** | 8901              | 694               |
| **Actual Positive** | 877               | 6974              |

--- 
### Metrics
- **Accuracy**: 0.9100
- **Precision**: 0.9095
- **Recall**: 0.8883

The best configuration is embedding dimension 128, batch size 32, learning rate 3×10−5, and epoch 20.

![Evaluate](https://i.imgur.com/your-image-id.png)
![Evaluate](https://i.imgur.com/your-image-id.png)

--- 
## Gui
![Evaluate](https://i.imgur.com/your-image-id.png)
![Evaluate](https://i.imgur.com/your-image-id.png)


This project is expected to produce an accurate model for identifying phishing URLs based on characteristic patterns in the URL.
