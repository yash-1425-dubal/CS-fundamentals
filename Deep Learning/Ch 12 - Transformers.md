# Chapter 12: Transformers

## Transformers

### Intuition

Transformers are a type of neural network architecture that uses self-attention mechanisms to process sequential data. They consist of an encoder network that processes the input data and a decoder network that generates the output data, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Problem Solved

Transformers enable the modeling of long-range dependencies in sequential data, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Encoder Network**: Processes the input data using self-attention mechanisms to capture long-range dependencies
2. **Decoder Network**: Generates the output data using self-attention mechanisms and cross-attention with the encoder's output
3. **Output Layer**: Produces the final output based on the decoder's hidden state

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the transformer class
class Transformer:
    def __init__(self, input_size, hidden_size, num_heads, num_layers):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.num_heads = num_heads
        self.num_layers = num_layers
        self.encoder_layers = [MultiHeadAttention(input_size, hidden_size, num_heads) for _ in range(num_layers)]
        self.decoder_layers = [MultiHeadAttention(input_size, hidden_size, num_heads) for _ in range(num_layers)]
        self.weights_o = np.random.randn(hidden_size, input_size)

    def forward(self, input_sequence, target_sequence):
        # Encode the input sequence
        encoder_output = input_sequence
        for layer in self.encoder_layers:
            encoder_output = layer.forward(encoder_output)

        # Decode the target sequence
        decoder_output = target_sequence
        for layer in self.decoder_layers:
            decoder_output = layer.forward(decoder_output, encoder_output)

        # Generate the final output
        output = np.dot(decoder_output, self.weights_o)
        return output

# Example usage
transformer = Transformer(input_size=10, hidden_size=20, num_heads=2, num_layers=2)
input_sequence = np.random.randn(5, 10)
target_sequence = np.random.randn(5, 10)
output = transformer.forward(input_sequence, target_sequence)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. A transformer can be trained to translate English sentences to French by processing the input English sentence with the encoder network and generating the corresponding output French sentence with the decoder network.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Transformers are complete for modeling long-range dependencies in sequential data.

### Optimality

Transformers are optimal for modeling long-range dependencies in sequential data.

### Advantages

- Models long-range dependencies in sequential data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Encoder

### Intuition

The encoder network in a transformer processes the input data using self-attention mechanisms to capture long-range dependencies. It consists of multiple layers of self-attention and feed-forward networks, allowing it to model complex patterns and relationships in the input data.

### Problem Solved

The encoder network enables the modeling of long-range dependencies in the input data, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Self-Attention Layer**: Processes the input data using self-attention mechanisms to capture long-range dependencies
2. **Feed-Forward Network**: Applies a non-linear transformation to the output of the self-attention layer
3. **Residual Connection**: Adds the input to the output of the feed-forward network to help with gradient flow
4. **Layer Normalization**: Normalizes the output of the residual connection to stabilize the training process

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the encoder class
class Encoder:
    def __init__(self, input_size, hidden_size, num_heads):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.num_heads = num_heads
        self.self_attention = MultiHeadAttention(input_size, hidden_size, num_heads)
        self.feed_forward = FeedForward(hidden_size, hidden_size)
        self.layer_norm = LayerNormalization(hidden_size)

    def forward(self, input_sequence):
        # Self-attention layer
        attention_output = self.self_attention.forward(input_sequence)

        # Feed-forward network
        feed_forward_output = self.feed_forward.forward(attention_output)

        # Residual connection
        residual_output = input_sequence + feed_forward_output

        # Layer normalization
        output = self.layer_norm.forward(residual_output)
        return output

# Example usage
encoder = Encoder(input_size=10, hidden_size=20, num_heads=2)
input_sequence = np.random.randn(5, 10)
output = encoder.forward(input_sequence)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. The encoder network can be used to process the input English sentence and capture long-range dependencies using self-attention mechanisms.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

The encoder network is complete for modeling long-range dependencies in the input data.

### Optimality

The encoder network is optimal for modeling long-range dependencies in the input data.

### Advantages

- Models long-range dependencies in the input data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Decoder

### Intuition

The decoder network in a transformer generates the output data using self-attention mechanisms and cross-attention with the encoder's output. It consists of multiple layers of self-attention, cross-attention, and feed-forward networks, allowing it to generate complex patterns and relationships in the output data.

### Problem Solved

The decoder network enables the generation of complex patterns and relationships in the output data, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Self-Attention Layer**: Processes the target data using self-attention mechanisms to capture long-range dependencies
2. **Cross-Attention Layer**: Processes the encoder's output using cross-attention mechanisms to focus on relevant parts of the input data
3. **Feed-Forward Network**: Applies a non-linear transformation to the output of the cross-attention layer
4. **Residual Connection**: Adds the input to the output of the feed-forward network to help with gradient flow
5. **Layer Normalization**: Normalizes the output of the residual connection to stabilize the training process

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the decoder class
class Decoder:
    def __init__(self, input_size, hidden_size, num_heads):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.num_heads = num_heads
        self.self_attention = MultiHeadAttention(input_size, hidden_size, num_heads)
        self.cross_attention = MultiHeadAttention(input_size, hidden_size, num_heads)
        self.feed_forward = FeedForward(hidden_size, hidden_size)
        self.layer_norm = LayerNormalization(hidden_size)

    def forward(self, target_sequence, encoder_output):
        # Self-attention layer
        self_attention_output = self.self_attention.forward(target_sequence)

        # Cross-attention layer
        cross_attention_output = self.cross_attention.forward(self_attention_output, encoder_output)

        # Feed-forward network
        feed_forward_output = self.feed_forward.forward(cross_attention_output)

        # Residual connection
        residual_output = self_attention_output + feed_forward_output

        # Layer normalization
        output = self.layer_norm.forward(residual_output)
        return output

# Example usage
decoder = Decoder(input_size=10, hidden_size=20, num_heads=2)
target_sequence = np.random.randn(5, 10)
encoder_output = np.random.randn(5, 10)
output = decoder.forward(target_sequence, encoder_output)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. The decoder network can be used to generate the output French sentence using self-attention mechanisms and cross-attention with the encoder's output.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

The decoder network is complete for generating complex patterns and relationships in the output data.

### Optimality

The decoder network is optimal for generating complex patterns and relationships in the output data.

### Advantages

- Generates complex patterns and relationships in the output data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Positional Encoding

### Intuition

Positional encoding is a technique used in transformers to provide information about the position of each element in the input sequence. It adds positional information to the input data, allowing the model to capture the order of elements and their relative positions.

### Problem Solved

Positional encoding enables the model to capture the order of elements and their relative positions in the input sequence, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Positional Encoding**: Using sine and cosine functions to create positional information
2. **Add Positional Encoding**: To the input data to provide positional information
3. **Process the Input Data**: Using the encoder network to capture long-range dependencies

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the positional encoding class
class PositionalEncoding:
    def __init__(self, max_len, hidden_size):
        self.max_len = max_len
        self.hidden_size = hidden_size
        self.positional_encoding = np.zeros((max_len, hidden_size))
        for pos in range(max_len):
            for i in range(0, hidden_size, 2):
                self.positional_encoding[pos, i] = np.sin(pos / (10000 ** (2 * i / hidden_size)))
                self.positional_encoding[pos, i + 1] = np.cos(pos / (10000 ** (2 * i / hidden_size)))

    def add_positional_encoding(self, input_sequence):
        return input_sequence + self.positional_encoding[:input_sequence.shape[0]]

# Example usage
positional_encoding = PositionalEncoding(max_len=100, hidden_size=20)
input_sequence = np.random.randn(5, 20)
input_with_positional_encoding = positional_encoding.add_positional_encoding(input_sequence)
print(input_with_positional_encoding)
```

### Example

Consider a dataset of English-French sentence pairs. Positional encoding can be used to add positional information to the input English sentence, allowing the encoder network to capture the order of words and their relative positions.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Positional encoding is complete for providing positional information to the input data.

### Optimality

Positional encoding is optimal for providing positional information to the input data.

### Advantages

- Provides positional information to the input data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Feed-Forward Networks

### Intuition

Feed-forward networks are used in transformers to apply a non-linear transformation to the output of the self-attention and cross-attention layers. They consist of two linear transformations with a non-linear activation function in between, allowing the model to capture complex patterns and relationships in the data.

### Problem Solved

Feed-forward networks enable the model to capture complex patterns and relationships in the data, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **First Linear Transformation**: Applies a linear transformation to the input data
2. **Non-Linear Activation Function**: Applies a non-linear activation function to the output of the first linear transformation
3. **Second Linear Transformation**: Applies a linear transformation to the output of the non-linear activation function

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the feed-forward network class
class FeedForward:
    def __init__(self, input_size, hidden_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.weights1 = np.random.randn(input_size, hidden_size)
        self.weights2 = np.random.randn(hidden_size, input_size)
        self.bias1 = np.zeros(hidden_size)
        self.bias2 = np.zeros(input_size)

    def forward(self, input_sequence):
        # First linear transformation
        hidden_output = np.dot(input_sequence, self.weights1) + self.bias1
        # Non-linear activation function
        hidden_output = np.maximum(0, hidden_output)
        # Second linear transformation
        output = np.dot(hidden_output, self.weights2) + self.bias2
        return output

# Example usage
feed_forward = FeedForward(input_size=10, hidden_size=20)
input_sequence = np.random.randn(5, 10)
output = feed_forward.forward(input_sequence)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. Feed-forward networks can be used to apply a non-linear transformation to the output of the self-attention and cross-attention layers, allowing the decoder network to capture complex patterns and relationships in the output French sentence.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Feed-forward networks are complete for capturing complex patterns and relationships in the data.

### Optimality

Feed-forward networks are optimal for capturing complex patterns and relationships in the data.

### Advantages

- Captures complex patterns and relationships in the data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Residual Connections

### Intuition

Residual connections are used in transformers to add the input to the output of the feed-forward network. They help with gradient flow by allowing the model to learn residual functions, making it easier for the model to train deep networks.

### Problem Solved

Residual connections enable the model to learn residual functions, making it easier for the model to train deep networks, and making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Add the Input**: To the output of the feed-forward network to create a residual connection
2. **Process the Residual Output**: Using layer normalization to stabilize the training process

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the residual connection class
class ResidualConnection:
    def __init__(self, hidden_size):
        self.hidden_size = hidden_size
        self.layer_norm = LayerNormalization(hidden_size)

    def forward(self, input_sequence, feed_forward_output):
        # Add the input to the feed-forward output
        residual_output = input_sequence + feed_forward_output
        # Layer normalization
        output = self.layer_norm.forward(residual_output)
        return output

# Example usage
residual_connection = ResidualConnection(hidden_size=20)
input_sequence = np.random.randn(5, 20)
feed_forward_output = np.random.randn(5, 20)
output = residual_connection.forward(input_sequence, feed_forward_output)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. Residual connections can be used to add the input to the output of the feed-forward network, allowing the encoder and decoder networks to learn residual functions and making it easier for the model to train deep networks.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Residual connections are complete for enabling the model to learn residual functions.

### Optimality

Residual connections are optimal for enabling the model to learn residual functions.

### Advantages

- Enables the model to learn residual functions
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Layer Normalization

### Intuition

Layer normalization is a technique used in transformers to normalize the output of the residual connection. It stabilizes the training process by normalizing the activations of the network, making it easier for the model to learn and converge.

### Problem Solved

Layer normalization enables the model to stabilize the training process, making it easier for the model to learn and converge, and making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Compute the Mean and Variance**: Of the activations across the features
2. **Normalize the Activations**: Using the mean and variance
3. **Scale and Shift**: The normalized activations using learnable parameters

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the layer normalization class
class LayerNormalization:
    def __init__(self, hidden_size):
        self.hidden_size = hidden_size
        self.gamma = np.ones(hidden_size)
        self.beta = np.zeros(hidden_size)

    def forward(self, input_sequence):
        # Compute the mean and variance
        mean = np.mean(input_sequence, axis=1, keepdims=True)
        variance = np.var(input_sequence, axis=1, keepdims=True)
        # Normalize the activations
        normalized_output = (input_sequence - mean) / np.sqrt(variance + 1e-8)
        # Scale and shift the normalized activations
        output = self.gamma * normalized_output + self.beta
        return output

# Example usage
layer_normalization = LayerNormalization(hidden_size=20)
input_sequence = np.random.randn(5, 20)
output = layer_normalization.forward(input_sequence)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. Layer normalization can be used to normalize the output of the residual connection, stabilizing the training process and making it easier for the encoder and decoder networks to learn and converge.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Layer normalization is complete for stabilizing the training process.

### Optimality

Layer normalization is optimal for stabilizing the training process.

### Advantages

- Stabilizes the training process
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Causal Masking

### Intuition

Causal masking is a technique used in transformers to prevent the decoder network from attending to future positions in the target sequence during training. It ensures that the decoder network only attends to the past and present positions, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Problem Solved

Causal masking enables the decoder network to only attend to the past and present positions, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Create a Mask**: To prevent the decoder network from attending to future positions
2. **Apply the Mask**: To the attention scores before applying the softmax function
3. **Compute Attention Weights**: Using the masked attention scores
4. **Compute Weighted Sum**: Of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the causal masking class
class CausalMasking:
    def __init__(self, max_len):
        self.max_len = max_len
        self.mask = np.tril(np.ones((max_len, max_len)))

    def apply_mask(self, attention_scores):
        # Apply the mask to the attention scores
        masked_attention_scores = attention_scores * self.mask[:attention_scores.shape[0], :attention_scores.shape[1]]
        return masked_attention_scores

# Example usage
causal_masking = CausalMasking(max_len=100)
attention_scores = np.random.randn(5, 5)
masked_attention_scores = causal_masking.apply_mask(attention_scores)
print(masked_attention_scores)
```

### Example

Consider a dataset of English-French sentence pairs. Causal masking can be used to prevent the decoder network from attending to future positions in the target French sentence during training, ensuring that the decoder network only attends to the past and present positions.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Causal masking is complete for preventing the decoder network from attending to future positions.

### Optimality

Causal masking is optimal for preventing the decoder network from attending to future positions.

### Advantages

- Prevents the decoder network from attending to future positions
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Conclusion

Transformers, including encoder, decoder, positional encoding, feed-forward networks, residual connections, layer normalization, and causal masking, are fundamental architectures in deep learning. Understanding these components is essential for developing effective deep learning models and applications for tasks like machine translation, text summarization, and image captioning.