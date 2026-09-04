# Chapter 6: Descriptive Statistics

## Descriptive Statistics

Descriptive statistics is the process of summarizing and describing the main features of a dataset. It includes measures of central tendency, measures of dispersion, and measures of shape.

### Measures of Central Tendency

Measures of central tendency describe the center or middle of the data distribution. They include the mean, median, and mode.

#### Mean

The mean is the average of the data points. It is calculated by summing all the data points and dividing by the number of data points.

```python
mean = sum(data) / len(data)
```

#### Median

The median is the middle value of the data points when they are arranged in order. It is calculated by finding the middle value of the ordered data points.

```python
median = sorted(data)[len(data) // 2]
```

#### Mode

The mode is the most frequently occurring value in the data. It is calculated by finding the value that appears most frequently in the data.

```python
from collections import Counter
mode = Counter(data).most_common(1)[0][0]
```

### Measures of Dispersion

Measures of dispersion describe the spread or variability of the data. They include the variance, standard deviation, range, and interquartile range.

#### Variance

The variance is the average of the squared differences from the mean. It is calculated by summing the squared differences from the mean and dividing by the number of data points.

```python
variance = sum((x - mean) ** 2 for x in data) / len(data)
```

#### Standard Deviation

The standard deviation is the square root of the variance. It is calculated by taking the square root of the variance.

```python
import math
std_dev = math.sqrt(variance)
```

#### Range

The range is the difference between the maximum and minimum values in the data. It is calculated by finding the difference between the maximum and minimum values.

```python
range = max(data) - min(data)
```

#### Interquartile Range

The interquartile range (IQR) is the difference between the third quartile and the first quartile. It is calculated by finding the difference between the third quartile and the first quartile.

```python
q1 = sorted(data)[len(data) // 4]
q3 = sorted(data)[3 * len(data) // 4]
iqr = q3 - q1
```

### Measures of Shape

Measures of shape describe the shape of the data distribution. They include skewness and kurtosis.

#### Skewness

Skewness measures the asymmetry of the data distribution. A positive skewness indicates that the data is skewed to the right, while a negative skewness indicates that the data is skewed to the left.

```python
skewness = (sum((x - mean) ** 3 for x in data) / len(data)) / std_dev ** 3
```

#### Kurtosis

Kurtosis measures the tailedness of the data distribution. A high kurtosis indicates that the data has heavy tails, while a low kurtosis indicates that the data has light tails.

```python
kurtosis = (sum((x - mean) ** 4 for x in data) / len(data)) / std_dev ** 4
```

## Conclusion

Descriptive statistics is a crucial step in the data science lifecycle. By summarizing and describing the main features of the data, we can understand its characteristics, identify patterns, and detect anomalies. This ensures the accuracy and reliability of our analysis and insights.