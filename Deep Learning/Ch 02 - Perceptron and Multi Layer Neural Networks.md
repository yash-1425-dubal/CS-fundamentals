# Chapter 2: Perceptron and Multi Layer Neural Networks

## Perceptron

### Intuition

The perceptron is the simplest form of a neural network, consisting of a single layer of neurons. It is a binary classifier that makes its predictions based on a linear combination of the input features.

### Problem Solved

The perceptron can solve linearly separable problems, where the classes can be separated by a straight line or hyperplane.

### Step-by-Step Working

1. **Input Layer**: Receives the input features
2. **Weights and Bias**: Compute the weighted sum of the inputs plus the bias
3. **Activation Function**: Apply the step function to the weighted sum to produce the output

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the perceptron class
class Perceptron:
    def __init__(self, input_size, learning_rate=0.01, epochs=100):
        self.weights = np.zeros(input_size + 1)
        self.learning_rate = learning_rate
        self.epochs = epochs

    def predict(self, X):
        weighted_sum = np.dot(X, self.weights[1:]) + self.weights[0]
        return 1 if weighted_sum > 0 else 0

    def train(self, X, y):
        for _ in range(self.epochs):
            for i in range(len(X)):
                prediction = self.predict(X[i])
                error = y[i] - prediction
                self.weights[1:] += self.learning_rate * error * X[i]
                self.weights[0] += self.learning_rate * error

# Create a perceptron
perceptron = Perceptron(input_size=2)

# Train the perceptron
X = np.array([[1, 2], [2, 3], [3, 4]])
y = np.array([0, 0, 1])
perceptron.train(X, y)

# Make a prediction
prediction = perceptron.predict(np.array([4, 5]))
print(prediction)
```

### Example

Consider a dataset of two classes, where each data point is represented by two features. The perceptron can be trained to classify new data points based on their features.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

The perceptron is complete for solving linearly separable problems.

### Optimality

The perceptron is optimal for solving linearly separable problems.

### Advantages

- Simple and easy to implement
- Can solve linearly separable problems

### Limitations

- Limited to linearly separable problems
- Cannot solve non-linear problems

## Multi Layer Neural Networks

### Intuition

Multi Layer Neural Networks (MLNNs) are neural networks with multiple layers of interconnected neurons. They are capable of learning complex patterns and relationships in data.

### Problem Solved

MLNNs can solve non-linear problems, where the classes cannot be separated by a straight line or hyperplane.

### Step-by-Step Working

1. **Input Layer**: Receives the input data
2. **Hidden Layers**: Process the input data through interconnected neurons
3. **Output Layer**: Produces the final output

### Pseudocode

```python
# Import necessary libraries
import numpy as np

# Define the multi layer neural network class
class MultiLayerNeuralNetwork:
    def __init__(self, input_size, hidden_size, output_size):
        self.weights1 = np.random.randn(input_size, hidden_size)
        self.weights2 = np.random.randn(hidden_size, output_size)

    def forward(self, X):
        self.hidden = np.dot(X, self.weights1)
        self.output = np.dot(self.hidden, self.weights2)
        return self.output

# Create a multi layer neural network
mlnn = MultiLayerNeuralNetwork(input_size=2, hidden_size=3, output_size=1)

# Forward pass
X = np.array([[1, 2]])
output = mlnn.forward(X)
print(output)
```

### Example

Consider a dataset of house prices with features like size, number of bedrooms, and location. A multi layer neural network can be trained to predict the price of a new house based on these features.

### Time Complexity

- **O(n)**: Where n is the number of training samples

### Space Complexity

- **O(n)**: The space required to store the training data and model

### Completeness

MLNNs are complete for learning complex patterns and relationships in data.

### Optimality

MLNNs are optimal for learning complex patterns and relationships in data.

### Advantages

- Can handle complex relationships between features and labels
- Widely used in various applications like classification and regression

### Limitations

- Requires large amounts of labeled data, which can be expensive and time-consuming to obtain
- Limited by the quality and representativeness of the labeled data

## Conclusion

The perceptron and multi layer neural networks are fundamental building blocks of deep learning. Understanding their fundamentals is essential for developing effective deep learning models and applications.