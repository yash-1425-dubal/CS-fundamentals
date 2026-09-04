# Chapter 2: Requirements Estimation and Capacity Planning

## Requirement Gathering

Requirement gathering is the process of identifying and documenting the needs and expectations of stakeholders for a system. It involves understanding the functional and non-functional requirements, constraints, and trade-offs.

### Functional Requirements

Functional requirements are the specific behaviors or functions that a system must perform. They describe what the system should do and how it should respond to particular inputs.

### Non-Functional Requirements

Non-functional requirements are the quality attributes that a system must possess. They describe how well the system should perform its functions, rather than what the system should do.

## Capacity Estimation

Capacity estimation is the process of determining the resources required to support a system's expected load. It involves estimating the number of users, requests, data storage, and bandwidth required.

### Back-of-the-Envelope Estimation

Back-of-the-envelope estimation is a quick and rough calculation used to estimate the capacity requirements of a system. It involves making reasonable assumptions and simplifications to arrive at a rough estimate.

## Calculations and Examples

### Requests per Second

Requests per second (RPS) is the number of requests a system can handle per second. It is a measure of the system's throughput and performance.

```python
# Example: Estimating RPS for a web application
# Assume 1 million daily active users (DAU) and 10 requests per user per day
rps = (1_000_000 * 10) / (24 * 60 * 60)  # 10 requests per user per day, 24 hours, 60 minutes, 60 seconds
```

### Queries per Second

Queries per second (QPS) is the number of database queries a system can handle per second. It is a measure of the system's database performance.

```python
# Example: Estimating QPS for a database
# Assume 100 RPS and 5 queries per request
qps = 100 * 5  # 5 queries per request
```

### Storage Requirements

Storage requirements are the amount of data storage needed to support a system's expected load. It involves estimating the amount of data generated, stored, and processed.

```python
# Example: Estimating storage requirements for a web application
# Assume 1 million daily active users (DAU) and 100 bytes of data per user per day
storage = 1_000_000 * 100  # 100 bytes per user per day
```

### Bandwidth

Bandwidth is the amount of data that can be transmitted over a network in a given time. It is a measure of the network's capacity and performance.

```python
# Example: Estimating bandwidth for a web application
# Assume 100 RPS and 1 KB of data per request
bandwidth = 100 * 1_000  # 1 KB per request
```

### Network Throughput

Network throughput is the amount of data that can be transmitted over a network in a given time. It is a measure of the network's capacity and performance.

```python
# Example: Estimating network throughput for a web application
# Assume 100 RPS and 1 KB of data per request
throughput = 100 * 1_000  # 1 KB per request
```

### Memory Requirements

Memory requirements are the amount of memory needed to support a system's expected load. It involves estimating the amount of memory required for data storage, processing, and caching.

```python
# Example: Estimating memory requirements for a web application
# Assume 1 million daily active users (DAU) and 100 bytes of data per user per day
memory = 1_000_000 * 100  # 100 bytes per user per day
```

### Cache Requirements

Cache requirements are the amount of cache needed to support a system's expected load. It involves estimating the amount of data that can be cached to improve performance.

```python
# Example: Estimating cache requirements for a web application
# Assume 100 RPS and 1 KB of data per request
cache = 100 * 1_000  # 1 KB per request
```

### Daily Active Users

Daily active users (DAU) is the number of unique users who interact with a system in a given day. It is a measure of the system's user engagement and growth.

```python
# Example: Estimating DAU for a web application
# Assume 1 million daily active users (DAU)
dau = 1_000_000  # 1 million daily active users
```

### Monthly Active Users

Monthly active users (MAU) is the number of unique users who interact with a system in a given month. It is a measure of the system's user engagement and growth.

```python
# Example: Estimating MAU for a web application
# Assume 1 million monthly active users (MAU)
mau = 1_000_000  # 1 million monthly active users
```

### Peak Traffic

Peak traffic is the highest amount of traffic a system experiences during a given period. It is a measure of the system's capacity and performance under peak load.

```python
# Example: Estimating peak traffic for a web application
# Assume 100 RPS and a peak multiplier of 2
peak_traffic = 100 * 2  # 200 RPS during peak traffic
```

### Average Traffic

Average traffic is the average amount of traffic a system experiences during a given period. It is a measure of the system's capacity and performance under normal load.

```python
# Example: Estimating average traffic for a web application
# Assume 100 RPS and a peak multiplier of 2
average_traffic = 100  # 100 RPS during average traffic
```

## Read/Write Ratio

Read/write ratio is the ratio of read operations to write operations in a system. It is a measure of the system's data access patterns and performance.

```python
# Example: Estimating read/write ratio for a web application
# Assume 100 RPS and 10 write operations per second
read_ratio = 100 / 10  # 10:1 read/write ratio
```

## Peak-to-Average Traffic

Peak-to-average traffic is the ratio of peak traffic to average traffic in a system. It is a measure of the system's capacity and performance under peak load.

```python
# Example: Estimating peak-to-average traffic for a web application
# Assume 100 RPS during average traffic and 200 RPS during peak traffic
peak_to_average = 200 / 100  # 2:1 peak-to-average traffic ratio
```

## Growth Estimation

Growth estimation is the process of predicting the future growth of a system. It involves estimating the number of users, requests, data storage, and bandwidth required over time.

```python
# Example: Estimating growth for a web application
# Assume 1 million daily active users (DAU) and a growth rate of 10% per year
growth = 1_000_000 * (1 + 0.10) ** 1  # 1 million DAU with 10% growth per year
```

## Storage Growth

Storage growth is the process of estimating the future storage requirements of a system. It involves estimating the amount of data generated, stored, and processed over time.

```python
# Example: Estimating storage growth for a web application
# Assume 1 million daily active users (DAU) and 100 bytes of data per user per day
storage_growth = 1_000_000 * 100 * (1 + 0.10) ** 1  # 1 million DAU with 10% growth per year
```

## Traffic Growth

Traffic growth is the process of estimating the future traffic requirements of a system. It involves estimating the number of requests, data storage, and bandwidth required over time.

```python
# Example: Estimating traffic growth for a web application
# Assume 100 RPS and a growth rate of 10% per year
traffic_growth = 100 * (1 + 0.10) ** 1  # 100 RPS with 10% growth per year
```

## Conclusion

Requirements estimation and capacity planning are critical steps in the System Design process. By understanding the functional and non-functional requirements, constraints, and trade-offs, and estimating the capacity requirements of a system, we can ensure that the system meets its goals and provides value to users.