---
jayout: "post"
title: "Deep Learning from Scratch"
date: "2020-04-22 23:14"
categories: Deep Learning
tags: [Deep Learning]
toc: true
comments: true
---


# Percepron 感知机
## AND Gate
```cpp
import  numpy as np

def AND(x1, x2):
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.75
    tmp = np.sum(w*x) + b
    if tmp <= 0:
        return 0
    elif tmp > 0:
        return 1

if __name__ == "__main__":
    print(AND(0, 0))
    print(AND(0, 1))
    print(AND(1, 0))
    print(AND(1, 1))
```

# 3.2 Active function 激活函数

# 3.4 三层神经网络的搭建
## 3.4.2 简单实现

```cpp
import numpy as np
from sigmoid import sigmoid

def identify_function(x):
    return x

# Input
print('Input data:')
X = np.array([1.0, 0.5])
W1 = np.array([[0.1, 0.3, 0.5], [0.2, 0.4, 0.6]])
B1 = np.array([0.1, 0.2, 0.3])

W2 = np.array([ [0.1, 0.4], [0.2, 0.5], [0.3,0.6] ])
B2 = np.array([0.1, 0.2])

W3 = np.array([[0.1, 0.3], [0.2, 0.4] ])
B3 = np.array([0.1, 0.2])

print('X')
print(X)

# first layer
print('First layer:')
A1 = np.dot(X, W1) + B1
Z1 = sigmoid(A1)

print('A1:')
print(A1)
print('Z1:')
print(Z1)

# Second layer
print('Second layer:')
A2 = np.dot(Z1, W2) + B2
Z2 = sigmoid(A2)

print('A2:')
print(A2)

print('Z2')
print(Z2)

# Output layer
A3 = np.dot(Z2, W3) + B3
Y = identify_function(A3)

print('A3:')
print(A3)
print('Y:')
print(Y)
```



## 3.4.3 实现总结

```cpp
import numpy as np
from sigmoid import sigmoid


def identify_function(x):
    return x


def init_network():
    network = {}
    network['W1'] = np.array([[0.1, 0.3, 0.5], [0.2, 0.4, 0.6]])
    network['b1'] = np.array([0.1, 0.2, 0.3])
    network['W2'] = np.array([[0.1, 0.4], [0.2, 0.5], [0.3, 0.6]])
    network['b2'] = np.array([0.1, 0.2])
    network['W3'] = np.array([[0.1, 0.3], [0.2, 0.4]])
    network['b3'] = np.array([0.1, 0.2])
    return network


def forward(network, x):
    W1, W2, W3 = network['W1'], network['W2'], network['W3']
    b1, b2, b3 = network['b1'], network['b2'], network['b3']
    a1 = np.dot(x, W1) + b1
    z1 = sigmoid(a1)
    a2 = np.dot(z1, W2) + b2
    z2 = sigmoid(a2)
    a3 = np.dot(z2, W3) + b3
    y = identify_function(a3)

    return y


network = init_network()
# Input
print('Input data:')
x = np.array([1.0, 0.5])
y = forward(network, x)

print('Y:')
print(y)
```
