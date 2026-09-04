# Chapter 3: Activation Functions Forward Propagation and Loss

## Activation Functions

### Intuition

Activation functions introduce non-linearity into the neural network, allowing it to learn complex patterns and relationships in the data. They determine whether a neuron should be activated or not based on the input it receives.

### Problem Solved

Activation functions enable neural networks to learn and model non-linear relationships in the data, making them suitable for a wide range of tasks such as classification, regression, and clustering.

### Step-by-Step Working

1. **Input Layer**: Receives the input data
2. **Hidden Layers**: Apply the activation function to the weighted sum of the inputs
3. **Output Layer**: Produces the final output

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the activation functions
class ActivationFunctions:
    @staticmethod
    def sigmoid(x):
        return 1 / (1 + np.exp(-x))

    @staticmethod
    def tanh(x):
        return np.tanh(x)

    @staticmethod
    def relu(x):
        return np.maximum(0, x)

    @staticmethod
    def leaky_relu(x, alpha=0.01):
        return np.where(x > 0, x, alpha * x)

    @staticmethod
    def gelu(x):
        return 0.5 * x * (1 + np.tanh(np.sqrt(2 / np.pi) * (x + 0.044715 * x**3)))

    @staticmethod
    def softmax(x):
        exp_x = np.exp(x - np.max(x))
        return exp_x / exp_x.sum(axis=0)

# Example usage
activation_functions = ActivationFunctions()
x = np.array([1, 2, 3])
print(activation_functions.sigmoid(x))
print(activation_functions.tanh(x))
print(activation_functions.relu(x))
print(activation_functions.leaky_relu(x))
print(activation_functions.gelu(x))
print(activation_functions.softmax(x))
```

### Example

Consider a neural network with a single hidden layer. The activation function can be applied to the weighted sum of the inputs to introduce non-linearity and enable the network to learn complex patterns and relationships in the data.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Activation functions are complete for introducing non-linearity into the neural network.

### Optimality

Activation functions are optimal for introducing non-linearity into the neural network.

### Advantages

- Introduce non-linearity into the neural network
- Enable the network to learn complex patterns and relationships in the data

### Limitations

- Can lead to vanishing or exploding gradients during training
- May require careful tuning of hyperparameters

## Forward Propagation

### Intuition

Forward propagation is the process of passing the input data through the neural network to produce an output. It involves computing the weighted sum of the inputs and applying the activation function to each neuron.

### Problem Solved

Forward propagation enables the neural network to make predictions based on the input data.

### Step-by-Step Working

1. **Input Layer**: Receives the input data
2. **Hidden Layers**: Compute the weighted sum of the inputs and apply the activation function to each neuron
3. **Output Layer**: Produces the final output

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the neural network class
class NeuralNetwork:
    def __init__(self, input_size, hidden_size, output_size):
        self.weights1 = np.random.randn(input_size, hidden_size)
        self.weights2 = np.random.randn(hidden_size, output_size)

    def forward(self, X):
        self.hidden = np.dot(X, self.weights1)
        self.hidden_activation = 1 / (1 + np.exp(-self.hidden))  # Sigmoid activation
        self.output = np.dot(self.hidden_activation, self.weights2)
        return self.output

# Create a neural network
nn = NeuralNetwork(input_size=2, hidden_size=3, output_size=1)

# Forward pass
X = np.array([[1, 2]])
output = nn.forward(X)
print(output)
```

### Example

Consider a neural network with a single hidden layer. Forward propagation can be used to make predictions based on the input data.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Forward propagation is complete for making predictions based on the input data.

### Optimality

Forward propagation is optimal for making predictions based on the input data.

### Advantages

- Enables the neural network to make predictions based on the input data
- Can handle complex relationships between features and labels

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Loss

### Intuition

Loss is a measure of the difference between the predicted output and the actual output. It is used to evaluate the performance of the neural network and guide the learning process.

### Problem Solved

Loss enables the neural network to learn from its mistakes and improve its performance over time.

### Step-by-Step Working

1. **Compute the predicted output**: Using forward propagation
2. **Compute the loss**: Using a loss function such as mean squared error or cross-entropy
3. **Update the weights and biases**: Using gradient descent or other optimization algorithms

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the loss functions
class LossFunctions:
    @staticmethod
    def mean_squared_error(y_true, y_pred):
        return np.mean((y_true - y_pred) ** 2)

    @staticmethod
    def cross_entropy(y_true, y_pred):
        return -np.mean(y_true * np.log(y_pred) + (1 - y_true) * np.log(1 - y_pred))

# Example usage
loss_functions = LossFunctions()
y_true = np.array([1, 0, 1])
y_pred = np.array([0.9, 0.1, 0.8])
print(loss_functions.mean_squared_error(y_true, y_pred))
print(loss_functions.cross_entropy(y_true, y_pred))
```

### Example

Consider a neural network trained on a dataset of house prices. The loss function can be used to evaluate the performance of the neural network and guide the learning process.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

Loss is complete for evaluating the performance of the neural network and guiding the learning process.

### Optimality

Loss is optimal for evaluating the performance of the neural network and guiding the learning process.

### Advantages

- Enables the neural network to learn from its mistakes and improve its performance over time
- Can handle complex relationships between features and labels

### Limitations

- Limited by the quality and representativeness of the input data
- May require careful tuning of hyperparameters

## Conclusion

Activation functions, forward propagation, and loss are fundamental concepts in deep learning. Understanding these concepts is essential for developing effective deep learning models and applications.