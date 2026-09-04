# Chapter 10: KNN, Naive Bayes, and Support Vector Machines

## Introduction to K-Nearest Neighbors (KNN)

K-Nearest Neighbors (KNN) is a supervised learning algorithm that classifies a new data point based on the majority class of its k nearest neighbors in the feature space. Key aspects of KNN include:

- **Intuition**: Classifying a new data point based on the majority class of its k nearest neighbors
- **Problem Solved**: Predicting the class of a new data point based on the classes of its k nearest neighbors
- **Step-by-Step Working**: Collect and prepare labeled data, choose the number of neighbors k, train the model on the labeled data, evaluate the model's performance, and use the trained model to make predictions on new data
- **Pseudocode**: Import necessary libraries, load and prepare data, choose the number of neighbors k, train the model on the labeled data, evaluate the model's performance, and make predictions on new data
- **Example**: Predicting the class of a new data point based on the classes of its k nearest neighbors in a dataset of customer purchase history
- **Time Complexity**: O(n), where n is the number of training samples
- **Space Complexity**: O(n), the space required to store the training data and model
- **Completeness**: KNN is complete for predicting the class of a new data point based on the classes of its k nearest neighbors
- **Optimality**: KNN is optimal for predicting the class of a new data point based on the classes of its k nearest neighbors
- **Advantages**: Simple and easy to understand, can handle complex relationships between features and classes, widely used in various applications like classification, regression, and recommendation systems
- **Limitations**: Limited by the quality and representativeness of the labeled data, the results can be difficult to interpret and validate, can be computationally expensive for large datasets

## Mathematical Foundation of KNN

KNN classifies a new data point based on the majority class of its k nearest neighbors in the feature space. The distance between the new data point and each training data point is calculated using a distance metric, such as Euclidean distance or Manhattan distance. The k nearest neighbors are then selected based on the smallest distances.

## Training KNN

Training KNN involves storing the labeled training data and the distance metric. The model does not learn any parameters during training, as it simply stores the training data and the distance metric.

## Prediction with KNN

Prediction with KNN involves calculating the distance between the new data point and each training data point, selecting the k nearest neighbors based on the smallest distances, and predicting the class of the new data point based on the majority class of its k nearest neighbors.

## Hyperparameters of KNN

KNN has one hyperparameter that needs to be tuned: the number of neighbors k. The number of neighbors k determines the number of nearest neighbors to consider when making predictions.

## Assumptions of KNN

KNN makes several assumptions about the data:

1. **Similarity**: Similar data points are close to each other in the feature space.
2. **Distance metric**: The distance metric used to calculate the distances between data points is appropriate for the data.
3. **No multicollinearity**: The independent variables are not highly correlated with each other.

## Complexity of KNN

The complexity of KNN is determined by the number of training samples and the number of neighbors k. The time complexity for training the model is O(1), as the model simply stores the training data and the distance metric. The time complexity for making predictions is O(n), where n is the number of training samples. The space complexity is O(n), the space required to store the training data and the distance metric.

## Advantages of KNN

- Simple and easy to understand
- Can handle complex relationships between features and classes
- Widely used in various applications like classification, regression, and recommendation systems

## Limitations of KNN

- Limited by the quality and representativeness of the labeled data
- The results can be difficult to interpret and validate
- Can be computationally expensive for large datasets

## Practical Example of KNN

Consider a dataset of customer purchase history with features like purchase date and purchase amount. KNN can be used to train a model to predict the class of a new data point based on the classes of its k nearest neighbors.

## Python Implementation of KNN

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose the number of neighbors k
k = 3

# Train the model on the training set
model = KNeighborsClassifier(n_neighbors=k)
model.fit(X_train, y_train)

# Evaluate the model on the testing set
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred, average='weighted')
recall = recall_score(y_test, y_pred, average='weighted')
f1 = f1_score(y_test, y_pred, average='weighted')
print(f'Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}, F1 Score: {f1}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Scikit-Learn Example of KNN

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose the number of neighbors k
k = 3

# Train the model on the training set
model = KNeighborsClassifier(n_neighbors=k)
model.fit(X_train, y_train)

# Evaluate the model on the testing set
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred, average='weighted')
recall = recall_score(y_test, y_pred, average='weighted')
f1 = f1_score(y_test, y_pred, average='weighted')
print(f'Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}, F1 Score: {f1}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Introduction to Naive Bayes

Naive Bayes is a supervised learning algorithm that classifies a new data point based on the Bayes theorem and the assumption of feature independence. Key aspects of Naive Bayes include:

- **Intuition**: Classifying a new data point based on the Bayes theorem and the assumption of feature independence
- **Problem Solved**: Predicting the class of a new data point based on the probabilities of the features given the class
- **Step-by-Step Working**: Collect and prepare labeled data, choose a suitable Naive Bayes algorithm (Gaussian Naive Bayes, Multinomial Naive Bayes, or Bernoulli Naive Bayes), train the model on the labeled data, evaluate the model's performance, and use the trained model to make predictions on new data
- **Pseudocode**: Import necessary libraries, load and prepare data, choose a suitable Naive Bayes algorithm, train the model on the labeled data, evaluate the model's performance, and make predictions on new data
- **Example**: Predicting the class of a new data point based on the probabilities of the features given the class in a dataset of customer purchase history
- **Time Complexity**: O(n), where n is the number of training samples
- **Space Complexity**: O(n), the space required to store the training data and model
- **Completeness**: Naive Bayes is complete for predicting the class of a new data point based on the probabilities of the features given the class
- **Optimality**: Naive Bayes is optimal for predicting the class of a new data point based on the probabilities of the features given the class
- **Advantages**: Simple and easy to understand, can handle complex relationships between features and classes, widely used in various applications like text classification, spam filtering, and sentiment analysis
- **Limitations**: Limited by the quality and representativeness of the labeled data, the results can be difficult to interpret and validate, assumes feature independence which may not hold in real-world data

## Mathematical Foundation of Naive Bayes

Naive Bayes classifies a new data point based on the Bayes theorem and the assumption of feature independence. The Bayes theorem is given by:

$$ P(y|x) = \frac{P(x|y) P(y)}{P(x)} $$

where:

- P(y|x) is the probability of the class y given the features x
- P(x|y) is the probability of the features x given the class y
- P(y) is the probability of the class y
- P(x) is the probability of the features x

The assumption of feature independence simplifies the calculation of P(x|y) as:

$$ P(x|y) = \prod_{i=1}^{n} P(x_i|y) $$

where:

- x_i is the i-th feature
- n is the number of features

## Training Naive Bayes

Training Naive Bayes involves calculating the probabilities of the features given the class and the probabilities of the classes. The model does not learn any parameters during training, as it simply calculates the probabilities based on the training data.

## Prediction with Naive Bayes

Prediction with Naive Bayes involves calculating the probability of the class given the features using the Bayes theorem and the assumption of feature independence, and predicting the class of the new data point based on the highest probability.

## Hyperparameters of Naive Bayes

Naive Bayes does not have any hyperparameters that need to be tuned, as the model simply calculates the probabilities based on the training data.

## Assumptions of Naive Bayes

Naive Bayes makes several assumptions about the data:

1. **Feature independence**: The features are independent of each other given the class.
2. **No multicollinearity**: The independent variables are not highly correlated with each other.

## Complexity of Naive Bayes

The complexity of Naive Bayes is determined by the number of training samples and the number of features. The time complexity for training the model is O(n), where n is the number of training samples. The time complexity for making predictions is O(m), where m is the number of features. The space complexity is O(n), the space required to store the training data and the probabilities.

## Advantages of Naive Bayes

- Simple and easy to understand
- Can handle complex relationships between features and classes
- Widely used in various applications like text classification, spam filtering, and sentiment analysis

## Limitations of Naive Bayes

- Limited by the quality and representativeness of the labeled data
- The results can be difficult to interpret and validate
- Assumes feature independence which may not hold in real-world data

## Practical Example of Naive Bayes

Consider a dataset of customer purchase history with features like purchase date and purchase amount. Naive Bayes can be used to train a model to predict the class of a new data point based on the probabilities of the features given the class.

## Python Implementation of Naive Bayes

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose a suitable Naive Bayes algorithm
model = GaussianNB()

# Train the model on the training set
model.fit(X_train, y_train)

# Evaluate the model on the testing set
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred, average='weighted')
recall = recall_score(y_test, y_pred, average='weighted')
f1 = f1_score(y_test, y_pred, average='weighted')
print(f'Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}, F1 Score: {f1}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Scikit-Learn Example of Naive Bayes

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose a suitable Naive Bayes algorithm
model = GaussianNB()

# Train the model on the training set
model.fit(X_train, y_train)

# Evaluate the model on the testing set
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred, average='weighted')
recall = recall_score(y_test, y_pred, average='weighted')
f1 = f1_score(y_test, y_pred, average='weighted')
print(f'Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}, F1 Score: {f1}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Introduction to Support Vector Machines (SVM)

Support Vector Machines (SVM) is a supervised learning algorithm that finds the optimal hyperplane that separates the classes in the feature space. Key aspects of SVM include:

- **Intuition**: Finding the optimal hyperplane that separates the classes in the feature space
- **Problem Solved**: Predicting the class of a new data point based on the side of the hyperplane it falls on
- **Step-by-Step Working**: Collect and prepare labeled data, choose a suitable kernel function, train the model on the labeled data, evaluate the model's performance, and use the trained model to make predictions on new data
- **Pseudocode**: Import necessary libraries, load and prepare data, choose a suitable kernel function, train the model on the labeled data, evaluate the model's performance, and make predictions on new data
- **Example**: Predicting the class of a new data point based on the side of the hyperplane it falls on in a dataset of customer purchase history
- **Time Complexity**: O(n^2), where n is the number of training samples
- **Space Complexity**: O(n), the space required to store the training data and model
- **Completeness**: SVM is complete for predicting the class of a new data point based on the side of the hyperplane it falls on
- **Optimality**: SVM is optimal for predicting the class of a new data point based on the side of the hyperplane it falls on
- **Advantages**: Can handle complex relationships between features and classes, widely used in various applications like classification, regression, and outlier detection
- **Limitations**: Limited by the quality and representativeness of the labeled data, the results can be difficult to interpret and validate, can be computationally expensive for large datasets

## Mathematical Foundation of SVM

SVM finds the optimal hyperplane that separates the classes in the feature space. The optimal hyperplane is the one that maximizes the margin between the classes. The margin is the distance between the hyperplane and the nearest data points of each class, known as support vectors.

## Training SVM

Training SVM involves finding the optimal hyperplane that separates the classes in the feature space. This is typically done using the method of quadratic programming, which involves solving the optimization problem:

$$ \min_{w, b} \frac{1}{2} \|w\|^2 $$

subject to:

$$ y_i (w^T x_i + b) \geq 1, \quad i = 1, \ldots, n $$

where:

- w is the weight vector
- b is the bias term
- y_i is the class label of the i-th data point
- x_i is the feature vector of the i-th data point

The solution to the optimization problem is given by:

$$ w = \sum_{i=1}^{n} \alpha_i y_i x_i $$

$$ b = y_i - w^T x_i $$

where:

- α_i is the Lagrange multiplier for the i-th data point

## Prediction with SVM

Prediction with SVM involves calculating the side of the hyperplane the new data point falls on. The predicted class y_pred is given by:

$$ y_{pred} = \text{sign}(w^T x + b) $$

where:

- x is the feature vector of the new data point
- w is the weight vector
- b is the bias term

## Hyperparameters of SVM

SVM has several hyperparameters that need to be tuned:

- **Kernel**: The kernel function to use (linear, polynomial, or radial basis function)
- **C**: The regularization parameter
- **Gamma**: The kernel coefficient for the radial basis function

## Assumptions of SVM

SVM makes several assumptions about the data:

1. **Linearity**: The classes are linearly separable in the feature space.
2. **No multicollinearity**: The independent variables are not highly correlated with each other.

## Complexity of SVM

The complexity of SVM is determined by the number of training samples and the number of features. The time complexity for training the model is O(n^2), where n is the number of training samples. The time complexity for making predictions is O(m), where m is the number of features. The space complexity is O(n), the space required to store the training data and the model.

## Advantages of SVM

- Can handle complex relationships between features and classes
- Widely used in various applications like classification, regression, and outlier detection

## Limitations of SVM

- Limited by the quality and representativeness of the labeled data
- The results can be difficult to interpret and validate
- Can be computationally expensive for large datasets

## Practical Example of SVM

Consider a dataset of customer purchase history with features like purchase date and purchase amount. SVM can be used to train a model to predict the class of a new data point based on the side of the hyperplane it falls on.

## Python Implementation of SVM

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose a suitable kernel function
kernel = 'linear'

# Train the model on the training set
model = SVC(kernel=kernel, C=1.0, gamma='scale')
model.fit(X_train, y_train)

# Evaluate the model on the testing set
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred, average='weighted')
recall = recall_score(y_test, y_pred, average='weighted')
f1 = f1_score(y_test, y_pred, average='weighted')
print(f'Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}, F1 Score: {f1}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Scikit-Learn Example of SVM

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose a suitable kernel function
kernel = 'linear'

# Train the model on the training set
model = SVC(kernel=kernel, C=1.0, gamma='scale')
model.fit(X_train, y_train)

# Evaluate the model on the testing set
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred, average='weighted')
recall = recall_score(y_test, y_pred, average='weighted')
f1 = f1_score(y_test, y_pred, average='weighted')
print(f'Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}, F1 Score: {f1}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Conclusion

K-Nearest Neighbors (KNN), Naive Bayes, and Support Vector Machines (SVM) are powerful supervised learning algorithms that enable computers to learn from labeled data and make predictions. By understanding the mathematical foundation, training process, prediction process, hyperparameters, assumptions, complexity, advantages, and limitations of KNN, Naive Bayes, and SVM, we can develop and deploy effective ML systems that can solve complex problems and make data-driven decisions.