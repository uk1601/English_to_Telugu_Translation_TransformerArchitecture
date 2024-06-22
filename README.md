# Language Translation using Transformer Architecture: English to Telugu

## Objective
The objective of this project is to develop a neural machine translation model using the Transformer architecture. The model is trained to translate text from English to another language, leveraging advanced techniques such as attention mechanisms and positional encoding to improve translation accuracy and efficiency.

## Steps Involved
1. Data Preparation
2. Model Architecture
3. Training
4. Translation Methods
5. Evaluation

## Detailed Explanation of Each Step

### 1. Data Preparation
- **Dataset**: The project utilizes a bilingual dataset of parallel sentences in English and the target language. Each sentence pair consists of an English sentence and its corresponding translation.[Dataset](https://huggingface.co/datasets/Telugu-LLM-Labs/telugu_alpaca_yahma_cleaned_filtered_romanized/tree/main)
- **Preprocessing**: 
  - **Tokenization**: Text data is split into smaller units called tokens, typically words or subwords, using techniques such as Byte Pair Encoding (BPE) to handle rare words efficiently.
  - **Encoding**: Tokens are mapped to integer indices using a vocabulary built from the training data.
  - **Padding**: Sequences are padded to a fixed length to ensure uniform input length, which is essential for efficient batch processing.

### 2. Model Architecture
- **Transformer Model**: Implemented using the architecture introduced by Vaswani et al., featuring:
  - **Multi-head Attention Mechanisms**: Allows the model to focus on different parts of the input sequence simultaneously. Each head performs scaled dot-product attention, and their outputs are concatenated and linearly transformed.
  - **Positional Encoding**: Injects information about the position of each token within the sequence, enabling the model to understand the order of words. This is done using sine and cosine functions of different frequencies.
- **Components**:
  - **Encoder**: Comprises multiple layers, each containing a multi-head self-attention mechanism and a position-wise fully connected feed-forward network. It processes the input sentence and generates contextualized embeddings.
  - **Decoder**: Also consists of multiple layers, each with a multi-head self-attention mechanism, an encoder-decoder attention mechanism, and a position-wise feed-forward network. It generates the translation by attending to both the encoder's output and the previously generated tokens.

### 3. Training
- **Training Loop**: The model is trained over multiple epochs using the Adam optimizer with learning rate scheduling based on the warmup steps strategy.
- **Loss Function**: The Cross-Entropy Loss function is used to measure the difference between the predicted and actual token probabilities, guiding the model's parameter updates.
- **Regularization**: Techniques such as dropout are employed to prevent overfitting by randomly setting a fraction of input units to zero during training.

### 4. Translation Methods
- **Greedy Search**: A straightforward decoding method that selects the most probable next token at each step, forming the translation in a left-to-right manner. While fast, it may lead to suboptimal translations as it does not consider alternative sequences.
- **Beam Search**: An advanced decoding strategy that keeps multiple hypotheses (beams) active at each decoding step. It balances exploration and exploitation by considering the top-k probable tokens and sequences, ultimately selecting the highest scoring translation path. This method significantly improves translation quality by avoiding local optima.

### 5. Evaluation
- **Sample Translations**: Example sentences are translated using both Greedy Search and Beam Search methods. This provides a qualitative comparison of their outputs.
- **Comparison**: The translations produced by both methods are analyzed to demonstrate the effectiveness of Beam Search in generating more accurate and fluent translations compared to Greedy Search.


## Conclusion
The Transformer-based translation model demonstrates the effectiveness of modern neural machine translation techniques. Greedy Search provides quick translations, while Beam Search enhances accuracy by considering multiple hypotheses, making it more effective for practical applications.
