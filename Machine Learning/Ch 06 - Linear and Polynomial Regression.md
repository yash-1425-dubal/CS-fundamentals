# Chapter 6: Linear and Polynomial Regression

## Introduction to Linear Regression

Linear regression is a supervised learning algorithm that models the relationship between a dependent variable and one or more independent variables using a linear equation. Key aspects of linear regression include:

- **Intuition**: Modeling the relationship between variables using a linear equation
- **Problem Solved**: Predicting continuous output values based on input features
- **Step-by-Step Working**: Collect and prepare labeled data, choose a suitable regression algorithm, train the model on the labeled data, evaluate the model's performance, and use the trained model to make predictions on new data
- **Pseudocode**: Import necessary libraries, load and prepare data, split data into training and testing sets, choose and train a model, evaluate the model, and make predictions on new data
- **Example**: Predicting house prices based on features like size, number of bedrooms, and location
- **Time Complexity**: O(n), where n is the number of training samples
- **Space Complexity**: O(n), the space required to store the training data and model
- **Completeness**: Linear regression is complete for predicting continuous output values based on input features
- **Optimality**: Linear regression is optimal for predicting continuous output values based on input features
- **Advantages**: Can handle complex relationships between features and continuous output values, widely used in various applications like predicting house prices, stock prices, and sales forecasts
- **Limitations**: Limited by the quality and representativeness of the labeled data, the results can be difficult to interpret and validate

## Mathematical Foundation of Linear Regression

Linear regression models the relationship between a dependent variable y and one or more independent variables x using the linear equation:

$$ y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n + \epsilon $$

where:

- y is the dependent variable
- x1, x2, ..., xn are the independent variables
- β0, β1, β2, ..., βn are the coefficients
- ε is the error term

The goal of linear regression is to find the coefficients β0, β1, β2, ..., βn that minimize the sum of squared errors between the predicted and actual values.

## Training Linear Regression

Training linear regression involves finding the coefficients β0, β1, β2, ..., βn that minimize the sum of squared errors between the predicted and actual values. This is typically done using the method of least squares, which involves solving the normal equations:

$$ (X^T X) \beta = X^T y $$

where:

- X is the matrix of independent variables
- y is the vector of dependent variables
- β is the vector of coefficients

The solution to the normal equations is given by:

$$ \beta = (X^T X)^{-1} X^T y $$

## Prediction with Linear Regression

Prediction with linear regression involves using the trained model to make predictions on new data. The predicted value y_pred is given by:

$$ y_{pred} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n $$

where:

- x1, x2, ..., xn are the input features
- β0, β1, β2, ..., βn are the coefficients

## Hyperparameters of Linear Regression

Linear regression does not have any hyperparameters that need to be tuned. The model is trained using the method of least squares, which does not require any hyperparameters.

## Assumptions of Linear Regression

Linear regression makes several assumptions about the data:

1. **Linearity**: The relationship between the dependent variable and the independent variables is linear.
2. **Independence**: The residuals (errors) are independent of each other.
3. **Homoscedasticity**: The residuals have constant variance at every level of the independent variables.
4. **Normality**: The residuals are normally distributed.
5. **No multicollinearity**: The independent variables are not highly correlated with each other.

## Complexity of Linear Regression

The complexity of linear regression is determined by the number of independent variables in the model. The time complexity for training the model is O(nm^2), where n is the number of training samples and m is the number of independent variables. The space complexity is O(m), the space required to store the coefficients.

## Advantages of Linear Regression

- Simple and easy to understand
- Can handle complex relationships between features and continuous output values
- Widely used in various applications like predicting house prices, stock prices, and sales forecasts

## Limitations of Linear Regression

- Limited by the quality and representativeness of the labeled data
- The results can be difficult to interpret and validate
- Assumes a linear relationship between the dependent variable and the independent variables

## Practical Example of Linear Regression

Consider a dataset of house prices with features like size, number of bedrooms, and location. Linear regression can be used to train a model to predict the price of a new house based on these features.

## Python Implementation of Linear Regression

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose and train a model
model = LinearRegression()
model.fit(X_train, y_train)

# Evaluate the model
y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Scikit-Learn Example of Linear Regression

```python
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1', 'feature2']]
y = data['target']

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose and train a model
model = LinearRegression()
model.fit(X_train, y_train)

# Evaluate the model
y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2], 'feature2': [3, 4]})
predictions = model.predict(new_data)
print(predictions)
```

## Introduction to Polynomial Regression

Polynomial regression is a supervised learning algorithm that models the relationship between a dependent variable and one or more independent variables using a polynomial equation. Key aspects of polynomial regression include:

- **Intuition**: Modeling the relationship between variables using a polynomial equation
- **Problem Solved**: Predicting continuous output values based on input features, especially when the relationship is not linear
- **Step-by-Step Working**: Collect and prepare labeled data, choose a suitable regression algorithm, train the model on the labeled data, evaluate the model's performance, and use the trained model to make predictions on new data
- **Pseudocode**: Import necessary libraries, load and prepare data, split data into training and testing sets, choose and train a model, evaluate the model, and make predictions on new data
- **Example**: Predicting house prices based on features like size, number of bedrooms, and location, especially when the relationship is not linear
- **Time Complexity**: O(n), where n is the number of training samples
- **Space Complexity**: O(n), the space required to store the training data and model
- **Completeness**: Polynomial regression is complete for predicting continuous output values based on input features, especially when the relationship is not linear
- **Optimality**: Polynomial regression is optimal for predicting continuous output values based on input features, especially when the relationship is not linear
- **Advantages**: Can handle complex relationships between features and continuous output values, especially when the relationship is not linear, widely used in various applications like predicting house prices, stock prices, and sales forecasts
- **Limitations**: Limited by the quality and representativeness of the labeled data, the results can be difficult to interpret and validate, can lead to overfitting if the degree of the polynomial is too high

## Mathematical Foundation of Polynomial Regression

Polynomial regression models the relationship between a dependent variable y and one or more independent variables x using the polynomial equation:

$$ y = \beta_0 + \beta_1 x + \beta_2 x^2 + \ldots + \beta_n x^n + \epsilon $$

where:

- y is the dependent variable
- x is the independent variable
- β0, β1, β2, ..., βn are the coefficients
- ε is the error term

The goal of polynomial regression is to find the coefficients β0, β1, β2, ..., βn that minimize the sum of squared errors between the predicted and actual values.

## Training Polynomial Regression

Training polynomial regression involves finding the coefficients β0, β1, β2, ..., βn that minimize the sum of squared errors between the predicted and actual values. This is typically done using the method of least squares, which involves solving the normal equations:

$$ (X^T X) \beta = X^T y $$

where:

- X is the matrix of independent variables
- y is the vector of dependent variables
- β is the vector of coefficients

The solution to the normal equations is given by:

$$ \beta = (X^T X)^{-1} X^T y $$

## Prediction with Polynomial Regression

Prediction with polynomial regression involves using the trained model to make predictions on new data. The predicted value y_pred is given by:

$$ y_{pred} = \beta_0 + \beta_1 x + \beta_2 x^2 + \ldots + \beta_n x^n $$

where:

- x is the input feature
- β0, β1, β2, ..., βn are the coefficients

## Hyperparameters of Polynomial Regression

Polynomial regression has one hyperparameter that needs to be tuned: the degree of the polynomial. The degree of the polynomial determines the complexity of the model and can affect its performance.

## Assumptions of Polynomial Regression

Polynomial regression makes several assumptions about the data:

1. **Polynomial relationship**: The relationship between the dependent variable and the independent variables is polynomial.
2. **Independence**: The residuals (errors) are independent of each other.
3. **Homoscedasticity**: The residuals have constant variance at every level of the independent variables.
4. **Normality**: The residuals are normally distributed.
5. **No multicollinearity**: The independent variables are not highly correlated with each other.

## Complexity of Polynomial Regression

The complexity of polynomial regression is determined by the degree of the polynomial. The time complexity for training the model is O(nm^2), where n is the number of training samples and m is the degree of the polynomial. The space complexity is O(m), the space required to store the coefficients.

## Advantages of Polynomial Regression

- Can handle complex relationships between features and continuous output values, especially when the relationship is not linear
- Widely used in various applications like predicting house prices, stock prices, and sales forecasts

## Limitations of Polynomial Regression

- Limited by the quality and representativeness of the labeled data
- The results can be difficult to interpret and validate
- Can lead to overfitting if the degree of the polynomial is too high

## Practical Example of Polynomial Regression

Consider a dataset of house prices with features like size, number of bedrooms, and location, especially when the relationship is not linear. Polynomial regression can be used to train a model to predict the price of a new house based on these features.

## Python Implementation of Polynomial Regression

```python
# Import necessary libraries
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1']]
y = data['target']

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose and train a model
poly = PolynomialFeatures(degree=2)
X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)
model = LinearRegression()
model.fit(X_train_poly, y_train)

# Evaluate the model
y_pred = model.predict(X_test_poly)
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2]})
new_data_poly = poly.transform(new_data)
predictions = model.predict(new_data_poly)
print(predictions)
```

## Scikit-Learn Example of Polynomial Regression

```python
# Import necessary libraries
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load and prepare data
data = pd.read_csv('data.csv')
X = data[['feature1']]
y = data['target']

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Choose and train a model
poly = PolynomialFeatures(degree=2)
X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)
model = LinearRegression()
model.fit(X_train_poly, y_train)

# Evaluate the model
y_pred = model.predict(X_test_poly)
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')

# Make predictions on new data
new_data = pd.DataFrame({'feature1': [1, 2]})
new_data_poly = poly.transform(new_data)
predictions = model.predict(new_data_poly)
print(predictions)
```

## Conclusion

Linear and polynomial regression are powerful supervised learning algorithms that enable computers to learn from labeled data and make predictions. By understanding the mathematical foundation, training process, prediction process, hyperparameters, assumptions, complexity, advantages, and limitations of linear and polynomial regression, we can develop and deploy effective ML systems that can solve complex problems and make data-driven decisions.