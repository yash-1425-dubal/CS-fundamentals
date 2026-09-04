# Chapter 11: Attention Mechanisms

## Attention Mechanisms

### Intuition

Attention mechanisms are a type of neural network architecture that allows the model to focus on specific parts of the input data while processing it. They use a set of queries, keys, and values to compute attention scores that determine the importance of each part of the input data.

### Problem Solved

Attention mechanisms enable the model to focus on relevant parts of the input data, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Query, Key, Value Vectors**: Generate query, key, and value vectors from the input data
2. **Attention Scores**: Compute attention scores using the dot product of query and key vectors
3. **Attention Weights**: Apply a softmax function to the attention scores to obtain attention weights
4. **Weighted Sum**: Compute the weighted sum of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the attention mechanism class
class AttentionMechanism:
    def __init__(self, input_size, hidden_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.weights_q = np.random.randn(input_size, hidden_size)
        self.weights_k = np.random.randn(input_size, hidden_size)
        self.weights_v = np.random.randn(input_size, hidden_size)

    def forward(self, input_sequence):
        queries = np.dot(input_sequence, self.weights_q)
        keys = np.dot(input_sequence, self.weights_k)
        values = np.dot(input_sequence, self.weights_v)

        attention_scores = np.dot(queries, keys.T) / np.sqrt(self.hidden_size)
        attention_weights = np.exp(attention_scores) / np.sum(np.exp(attention_scores), axis=1, keepdims=True)

        weighted_sum = np.dot(attention_weights, values)
        return weighted_sum

# Example usage
attention_mechanism = AttentionMechanism(input_size=10, hidden_size=20)
input_sequence = np.random.randn(5, 10)
weighted_sum = attention_mechanism.forward(input_sequence)
print(weighted_sum)
```

### Example

Consider a dataset of English-French sentence pairs. An attention mechanism can be used to translate English sentences to French by focusing on relevant parts of the input sentence and generating the corresponding output sentence.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Attention mechanisms are complete for focusing on relevant parts of the input data.

### Optimality

Attention mechanisms are optimal for focusing on relevant parts of the input data.

### Advantages

- Enables the model to focus on relevant parts of the input data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Query

### Intuition

Query vectors are used in attention mechanisms to represent the current input data that the model is trying to focus on. They are used to compute attention scores with key vectors to determine the importance of each part of the input data.

### Problem Solved

Query vectors enable the model to represent the current input data and compute attention scores with key vectors, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Query Vectors**: From the input data using a linear transformation
2. **Compute Attention Scores**: Using the dot product of query and key vectors
3. **Apply Softmax**: To obtain attention weights
4. **Compute Weighted Sum**: Of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the query class
class Query:
    def __init__(self, input_size, hidden_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.weights_q = np.random.randn(input_size, hidden_size)

    def generate(self, input_sequence):
        queries = np.dot(input_sequence, self.weights_q)
        return queries

# Example usage
query = Query(input_size=10, hidden_size=20)
input_sequence = np.random.randn(5, 10)
queries = query.generate(input_sequence)
print(queries)
```

### Example

Consider a dataset of English-French sentence pairs. Query vectors can be used to represent the current English sentence and compute attention scores with key vectors to determine the importance of each word in the sentence.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Query vectors are complete for representing the current input data and computing attention scores with key vectors.

### Optimality

Query vectors are optimal for representing the current input data and computing attention scores with key vectors.

### Advantages

- Enables the model to represent the current input data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Key

### Intuition

Key vectors are used in attention mechanisms to represent the input data that the model is comparing with the query vectors. They are used to compute attention scores with query vectors to determine the importance of each part of the input data.

### Problem Solved

Key vectors enable the model to represent the input data and compute attention scores with query vectors, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Key Vectors**: From the input data using a linear transformation
2. **Compute Attention Scores**: Using the dot product of query and key vectors
3. **Apply Softmax**: To obtain attention weights
4. **Compute Weighted Sum**: Of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the key class
class Key:
    def __init__(self, input_size, hidden_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.weights_k = np.random.randn(input_size, hidden_size)

    def generate(self, input_sequence):
        keys = np.dot(input_sequence, self.weights_k)
        return keys

# Example usage
key = Key(input_size=10, hidden_size=20)
input_sequence = np.random.randn(5, 10)
keys = key.generate(input_sequence)
print(keys)
```

### Example

Consider a dataset of English-French sentence pairs. Key vectors can be used to represent the input French sentence and compute attention scores with query vectors to determine the importance of each word in the sentence.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Key vectors are complete for representing the input data and computing attention scores with query vectors.

### Optimality

Key vectors are optimal for representing the input data and computing attention scores with query vectors.

### Advantages

- Enables the model to represent the input data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Value

### Intuition

Value vectors are used in attention mechanisms to represent the output data that the model is generating. They are used to compute the weighted sum of the value vectors using the attention weights obtained from the query and key vectors.

### Problem Solved

Value vectors enable the model to represent the output data and compute the weighted sum of the value vectors using the attention weights, making them suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Value Vectors**: From the input data using a linear transformation
2. **Compute Attention Scores**: Using the dot product of query and key vectors
3. **Apply Softmax**: To obtain attention weights
4. **Compute Weighted Sum**: Of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the value class
class Value:
    def __init__(self, input_size, hidden_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.weights_v = np.random.randn(input_size, hidden_size)

    def generate(self, input_sequence):
        values = np.dot(input_sequence, self.weights_v)
        return values

# Example usage
value = Value(input_size=10, hidden_size=20)
input_sequence = np.random.randn(5, 10)
values = value.generate(input_sequence)
print(values)
```

### Example

Consider a dataset of English-French sentence pairs. Value vectors can be used to represent the output French sentence and compute the weighted sum of the value vectors using the attention weights obtained from the query and key vectors.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Value vectors are complete for representing the output data and computing the weighted sum of the value vectors using the attention weights.

### Optimality

Value vectors are optimal for representing the output data and computing the weighted sum of the value vectors using the attention weights.

### Advantages

- Enables the model to represent the output data
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Self-Attention

### Intuition

Self-attention is a type of attention mechanism where the query, key, and value vectors are all derived from the same input data. It allows the model to focus on different parts of the input data at different positions, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Problem Solved

Self-attention enables the model to focus on different parts of the input data at different positions, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Query, Key, Value Vectors**: From the input data using linear transformations
2. **Compute Attention Scores**: Using the dot product of query and key vectors
3. **Apply Softmax**: To obtain attention weights
4. **Compute Weighted Sum**: Of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the self-attention class
class SelfAttention:
    def __init__(self, input_size, hidden_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.weights_q = np.random.randn(input_size, hidden_size)
        self.weights_k = np.random.randn(input_size, hidden_size)
        self.weights_v = np.random.randn(input_size, hidden_size)

    def forward(self, input_sequence):
        queries = np.dot(input_sequence, self.weights_q)
        keys = np.dot(input_sequence, self.weights_k)
        values = np.dot(input_sequence, self.weights_v)

        attention_scores = np.dot(queries, keys.T) / np.sqrt(self.hidden_size)
        attention_weights = np.exp(attention_scores) / np.sum(np.exp(attention_scores), axis=1, keepdims=True)

        weighted_sum = np.dot(attention_weights, values)
        return weighted_sum

# Example usage
self_attention = SelfAttention(input_size=10, hidden_size=20)
input_sequence = np.random.randn(5, 10)
weighted_sum = self_attention.forward(input_sequence)
print(weighted_sum)
```

### Example

Consider a dataset of English-French sentence pairs. Self-attention can be used to focus on different parts of the input English sentence at different positions and generate the corresponding output French sentence.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Self-attention is complete for focusing on different parts of the input data at different positions.

### Optimality

Self-attention is optimal for focusing on different parts of the input data at different positions.

### Advantages

- Enables the model to focus on different parts of the input data at different positions
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Cross-Attention

### Intuition

Cross-attention is a type of attention mechanism where the query vectors are derived from one input data, and the key and value vectors are derived from another input data. It allows the model to focus on relevant parts of the input data from different sources, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Problem Solved

Cross-attention enables the model to focus on relevant parts of the input data from different sources, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Query Vectors**: From one input data using a linear transformation
2. **Generate Key and Value Vectors**: From another input data using linear transformations
3. **Compute Attention Scores**: Using the dot product of query and key vectors
4. **Apply Softmax**: To obtain attention weights
5. **Compute Weighted Sum**: Of the value vectors using the attention weights

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the cross-attention class
class CrossAttention:
    def __init__(self, input_size_q, input_size_kv, hidden_size):
        self.input_size_q = input_size_q
        self.input_size_kv = input_size_kv
        self.hidden_size = hidden_size
        self.weights_q = np.random.randn(input_size_q, hidden_size)
        self.weights_k = np.random.randn(input_size_kv, hidden_size)
        self.weights_v = np.random.randn(input_size_kv, hidden_size)

    def forward(self, input_sequence_q, input_sequence_kv):
        queries = np.dot(input_sequence_q, self.weights_q)
        keys = np.dot(input_sequence_kv, self.weights_k)
        values = np.dot(input_sequence_kv, self.weights_v)

        attention_scores = np.dot(queries, keys.T) / np.sqrt(self.hidden_size)
        attention_weights = np.exp(attention_scores) / np.sum(np.exp(attention_scores), axis=1, keepdims=True)

        weighted_sum = np.dot(attention_weights, values)
        return weighted_sum

# Example usage
cross_attention = CrossAttention(input_size_q=10, input_size_kv=15, hidden_size=20)
input_sequence_q = np.random.randn(5, 10)
input_sequence_kv = np.random.randn(5, 15)
weighted_sum = cross_attention.forward(input_sequence_q, input_sequence_kv)
print(weighted_sum)
```

### Example

Consider a dataset of English-French sentence pairs. Cross-attention can be used to focus on relevant parts of the input English sentence and the corresponding output French sentence, allowing the model to generate the correct translation.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Cross-attention is complete for focusing on relevant parts of the input data from different sources.

### Optimality

Cross-attention is optimal for focusing on relevant parts of the input data from different sources.

### Advantages

- Enables the model to focus on relevant parts of the input data from different sources
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Multi-Head Attention

### Intuition

Multi-head attention is a type of attention mechanism that uses multiple sets of query, key, and value vectors to compute attention scores in parallel. It allows the model to focus on different aspects of the input data simultaneously, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Problem Solved

Multi-head attention enables the model to focus on different aspects of the input data simultaneously, making it suitable for tasks like machine translation, text summarization, and image captioning.

### Step-by-Step Working

1. **Generate Multiple Sets of Query, Key, Value Vectors**: From the input data using linear transformations
2. **Compute Attention Scores**: Using the dot product of query and key vectors for each set
3. **Apply Softmax**: To obtain attention weights for each set
4. **Compute Weighted Sum**: Of the value vectors using the attention weights for each set
5. **Concatenate the Weighted Sums**: From all sets and apply a linear transformation to obtain the final output

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the multi-head attention class
class MultiHeadAttention:
    def __init__(self, input_size, hidden_size, num_heads):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.num_heads = num_heads
        self.head_size = hidden_size // num_heads
        self.weights_q = np.random.randn(input_size, hidden_size)
        self.weights_k = np.random.randn(input_size, hidden_size)
        self.weights_v = np.random.randn(input_size, hidden_size)
        self.weights_o = np.random.randn(hidden_size, hidden_size)

    def forward(self, input_sequence):
        queries = np.dot(input_sequence, self.weights_q)
        keys = np.dot(input_sequence, self.weights_k)
        values = np.dot(input_sequence, self.weights_v)

        queries = np.split(queries, self.num_heads, axis=-1)
        keys = np.split(keys, self.num_heads, axis=-1)
        values = np.split(values, self.num_heads, axis=-1)

        weighted_sums = []
        for i in range(self.num_heads):
            attention_scores = np.dot(queries[i], keys[i].T) / np.sqrt(self.head_size)
            attention_weights = np.exp(attention_scores) / np.sum(np.exp(attention_scores), axis=1, keepdims=True)
            weighted_sum = np.dot(attention_weights, values[i])
            weighted_sums.append(weighted_sum)

        weighted_sum = np.concatenate(weighted_sums, axis=-1)
        output = np.dot(weighted_sum, self.weights_o)
        return output

# Example usage
multi_head_attention = MultiHeadAttention(input_size=10, hidden_size=20, num_heads=2)
input_sequence = np.random.randn(5, 10)
output = multi_head_attention.forward(input_sequence)
print(output)
```

### Example

Consider a dataset of English-French sentence pairs. Multi-head attention can be used to focus on different aspects of the input English sentence simultaneously and generate the corresponding output French sentence.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Multi-head attention is complete for focusing on different aspects of the input data simultaneously.

### Optimality

Multi-head attention is optimal for focusing on different aspects of the input data simultaneously.

### Advantages

- Enables the model to focus on different aspects of the input data simultaneously
- Suitable for tasks like machine translation, text summarization, and image captioning

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Conclusion

Attention mechanisms, including query, key, value, self-attention, cross-attention, and multi-head attention, are fundamental architectures in deep learning. Understanding these mechanisms is essential for developing effective deep learning models and applications for tasks like machine translation, text summarization, and image captioning.