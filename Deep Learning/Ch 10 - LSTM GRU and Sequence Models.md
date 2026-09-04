# Chapter 10: LSTM GRU and Sequence Models

## LSTM

### Intuition

Long Short-Term Memory (LSTM) is a type of Recurrent Neural Network (RNN) that addresses the vanishing gradient problem by introducing a memory cell and gating mechanisms. It uses input, forget, and output gates to control the flow of information into and out of the memory cell, allowing it to capture long-term dependencies in sequential data.

### Problem Solved

LSTM enables the modeling of long-term dependencies in sequential data, making it suitable for tasks like time series prediction, natural language processing, and speech recognition.

### Step-by-Step Working

1. **Input Layer**: Receives the input data at each time step
2. **LSTM Layer**: Processes the input data and the hidden state from the previous time step to produce the current hidden state and memory cell state
3. **Output Layer**: Produces the final output based on the current hidden state

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the LSTM class
class LSTM:
    def __init__(self, input_size, hidden_size, output_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.output_size = output_size
        self.weights_ih = np.random.randn(input_size, 4 * hidden_size)
        self.weights_hh = np.random.randn(hidden_size, 4 * hidden_size)
        self.weights_ho = np.random.randn(hidden_size, output_size)
        self.bias = np.zeros(4 * hidden_size)

    def forward(self, input_sequence):
        hidden_state = np.zeros(self.hidden_size)
        cell_state = np.zeros(self.hidden_size)
        outputs = []
        for input_t in input_sequence:
            gates = np.dot(input_t, self.weights_ih) + np.dot(hidden_state, self.weights_hh) + self.bias
            input_gate, forget_gate, output_gate, candidate_cell = np.split(gates, 4, axis=1)
            input_gate = 1 / (1 + np.exp(-input_gate))
            forget_gate = 1 / (1 + np.exp(-forget_gate))
            output_gate = 1 / (1 + np.exp(-output_gate))
            candidate_cell = np.tanh(candidate_cell)
            cell_state = forget_gate * cell_state + input_gate * candidate_cell
            hidden_state = output_gate * np.tanh(cell_state)
            output_t = np.dot(hidden_state, self.weights_ho)
            outputs.append(output_t)
        return outputs

# Example usage
lstm = LSTM(input_size=10, hidden_size=20, output_size=5)
input_sequence = [np.random.randn(10) for _ in range(5)]
outputs = lstm.forward(input_sequence)
print(outputs)
```

### Example

Consider a dataset of time series data representing stock prices. An LSTM can be trained to predict future stock prices based on the historical data and the long-term dependencies captured by the memory cell and gating mechanisms.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

LSTM is complete for modeling long-term dependencies in sequential data.

### Optimality

LSTM is optimal for modeling long-term dependencies in sequential data.

### Advantages

- Models long-term dependencies in sequential data
- Suitable for tasks like time series prediction, natural language processing, and speech recognition

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## GRU

### Intuition

Gated Recurrent Unit (GRU) is a type of RNN that simplifies the LSTM architecture by combining the forget and input gates into a single update gate and merging the cell state and hidden state. It uses a reset gate and an update gate to control the flow of information in the network.

### Problem Solved

GRU enables the modeling of temporal dependencies in sequential data with a simpler architecture compared to LSTM, making it suitable for tasks like time series prediction, natural language processing, and speech recognition.

### Step-by-Step Working

1. **Input Layer**: Receives the input data at each time step
2. **GRU Layer**: Processes the input data and the hidden state from the previous time step to produce the current hidden state
3. **Output Layer**: Produces the final output based on the current hidden state

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the GRU class
class GRU:
    def __init__(self, input_size, hidden_size, output_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.output_size = output_size
        self.weights_ih = np.random.randn(input_size, 3 * hidden_size)
        self.weights_hh = np.random.randn(hidden_size, 3 * hidden_size)
        self.weights_ho = np.random.randn(hidden_size, output_size)
        self.bias = np.zeros(3 * hidden_size)

    def forward(self, input_sequence):
        hidden_state = np.zeros(self.hidden_size)
        outputs = []
        for input_t in input_sequence:
            gates = np.dot(input_t, self.weights_ih) + np.dot(hidden_state, self.weights_hh) + self.bias
            reset_gate, update_gate, candidate_hidden = np.split(gates, 3, axis=1)
            reset_gate = 1 / (1 + np.exp(-reset_gate))
            update_gate = 1 / (1 + np.exp(-update_gate))
            candidate_hidden = np.tanh(candidate_hidden)
            hidden_state = (1 - update_gate) * hidden_state + update_gate * candidate_hidden
            output_t = np.dot(hidden_state, self.weights_ho)
            outputs.append(output_t)
        return outputs

# Example usage
gru = GRU(input_size=10, hidden_size=20, output_size=5)
input_sequence = [np.random.randn(10) for _ in range(5)]
outputs = gru.forward(input_sequence)
print(outputs)
```

### Example

Consider a dataset of time series data representing stock prices. A GRU can be trained to predict future stock prices based on the historical data and the temporal dependencies captured by the reset gate and update gate.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

GRU is complete for modeling temporal dependencies in sequential data with a simpler architecture compared to LSTM.

### Optimality

GRU is optimal for modeling temporal dependencies in sequential data with a simpler architecture compared to LSTM.

### Advantages

- Models temporal dependencies in sequential data with a simpler architecture compared to LSTM
- Suitable for tasks like time series prediction, natural language processing, and speech recognition

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Sequence Models

### Intuition

Sequence models are a type of neural network architecture used for tasks that involve processing sequential data, such as time series, natural language, and speech. They use recurrent connections to maintain a hidden state that captures information from previous time steps, allowing them to model temporal dependencies.

### Problem Solved

Sequence models enable the modeling of temporal dependencies in sequential data, making them suitable for tasks like time series prediction, natural language processing, and speech recognition.

### Step-by-Step Working

1. **Input Layer**: Receives the input data at each time step
2. **Recurrent Layer**: Processes the input data and the hidden state from the previous time step to produce the current hidden state
3. **Output Layer**: Produces the final output based on the current hidden state

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the sequence model class
class SequenceModel:
    def __init__(self, input_size, hidden_size, output_size):
        self.input_size = input_size
        self.hidden_size = hidden_size
        self.output_size = output_size
        self.weights_ih = np.random.randn(input_size, hidden_size)
        self.weights_hh = np.random.randn(hidden_size, hidden_size)
        self.weights_ho = np.random.randn(hidden_size, output_size)
        self.bias_h = np.zeros(hidden_size)
        self.bias_o = np.zeros(output_size)

    def forward(self, input_sequence):
        hidden_state = np.zeros(self.hidden_size)
        outputs = []
        for input_t in input_sequence:
            hidden_state = np.tanh(np.dot(input_t, self.weights_ih) + np.dot(hidden_state, self.weights_hh) + self.bias_h)
            output_t = np.dot(hidden_state, self.weights_ho) + self.bias_o
            outputs.append(output_t)
        return outputs

# Example usage
sequence_model = SequenceModel(input_size=10, hidden_size=20, output_size=5)
input_sequence = [np.random.randn(10) for _ in range(5)]
outputs = sequence_model.forward(input_sequence)
print(outputs)
```

### Example

Consider a dataset of time series data representing stock prices. A sequence model can be trained to predict future stock prices based on the historical data and the temporal dependencies captured by the hidden state.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Sequence models are complete for modeling temporal dependencies in sequential data.

### Optimality

Sequence models are optimal for modeling temporal dependencies in sequential data.

### Advantages

- Models temporal dependencies in sequential data
- Suitable for tasks like time series prediction, natural language processing, and speech recognition

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Conclusion

LSTM, GRU, and sequence models are fundamental architectures in deep learning. Understanding these architectures is essential for developing effective deep learning models and applications for sequential data tasks.