---
header-includes:
  - \usepackage{mathtools}
---

# Multi-Layer Perceptrons, Stochastic Gradient Descent, and Optimization

## Outline

- [Multi-Layer Perceptrons, Stochastic Gradient Descent, and Optimization](#multi-layer-perceptrons-stochastic-gradient-descent-and-optimization)
  - [Outline](#outline)
  - [Multi-Layer Perceptrons](#multi-layer-perceptrons)
    - [Motivation](#motivation)
    - [Forward Pass](#forward-pass)
    - [Forward Pass](#forward-pass-1)
    - [Backpropagation](#backpropagation)
  - [Optimization](#optimization)
    - [Motivation](#motivation-1)
    - [Problems](#problems)
  - [SGD](#sgd)

## Multi-Layer Perceptrons

### Motivation

Last lecture, we learned about perceptrons, a type of neural network that takes input features and makes a binary decision. Perceptrons work well when the data is linearly separable, meaning that a straight line (hyperplane) can cleanly divide the classes. However, perceptrons fail when the decision boundary is not linearly separable; for example, in the classic XOR problem. So how can we create non-linear decision boundaries?

The answer is surprisingly elegant. If a single perceptron doesn't work, we can combine **multiple** together to create non-linear decision boundaries. This layered structure of stacking multiple perceptrons with non-linear activations is what defines a multi-layer perceptron (MLP). Just as we can approximate curves with small straight-line segments in calculus, we can approximate non-linear decision boundaries with linear perceptrons.

### Forward Pass

An MLP consists of an input layer, one or more hidden layers with neurons, and an output layer. Each neuron in a hidden layer computes a **weighted** sum of inputs from the previous layer, adds a bias, and then applies a **non-linear** activation function.
<img src= https://raw.githubusercontent.com/William-Leung/cs4782-optimization-notes/main/images/forward_pass.png>
A forward pass through the MLP performs the following steps:

1. **Multiply the input x to a node with a weight vector associated with the node.**
   At every neuron in the network, we perform a weighted sum of the inputs and add a bias. Note that in the past, we have stored the bias term separately, but it's possible to encode the bias into our weights. By rewriting $x_i$ as $\begin{bmatrix} {x}_i \\1\end{bmatrix}$ and $w$ as $\begin{bmatrix} w \\ b \end{bmatrix}$, we have $$a_i=wx_i=\begin{bmatrix} w \\ b \end{bmatrix}^T \begin{bmatrix} x_i \\ 1 \end{bmatrix} = w^Tx_i+b$$
2. **Apply a non-linear activation function $\sigma$ to the weighted sum $a_i$.**
   Activation functions allow neurons to introduce non-linearity and complexity into the model and without them, the model could be represented as a single linear transformation. Early MLPs used the sigmoid (logistic) function, which squashes between $0$ and $1$. An alternative is the hyperbolic tangent (tanh), which squashes between $-1$ and $1$. However, the most popular choice in modern networks is the ReLU (Rectified Linear Unit) which is $0$ for negative inputs and the identity function for positive inputs.

Let's see an example of this in action!
<img src=https://raw.githubusercontent.com/William-Leung/cs4782-optimization-notes/main/images/sample_neural_network.png>
Figure 1: Example structure of a simple MLP with two input features $x_1, x_2$, two hidden neurons $u$ and $v$ in a hidden layer, and an output neuron $z$.

Now, how do we use an MLP? During training, the input is passed

1.

### Forward Pass

### Backpropagation

## Optimization

### Motivation

So far, we've seen how

### Problems

- **Convexity:**
- **Time Complexity**:

## SGD

**Critical Thinking:** We said that momentum **almost** always converges faster than standard SGD, but why did we say almost? In what scenarios could standard SGD converge to the minimum faster than momentum?

<!-- markdownlint-disable MD033 -->

[//]: # "The line above disables the flagging for inline HTML"

<details>
  <summary>Answer</summary>
  
* **High Momentum Coefficient:** If the momentum coefficient $\mu$ is too high, it can cause the optimizer to overshoot minima or oscillate in narrow valleys. In these cases, standard SGD, despite being slower,may descend towards the minimum more directly and thus faster.
* **Noisy Gradients:** If gradient estimates have a lot of noise that is uncorrelated, momentum can actually hinder progress by following the noise. On the other hand, vanilla SGD ignores the previous noisy gradients.
* **Sharp Curvature:** In regions with flat gradients followed by steep drops (plateaus into ravines), momentum may take longer to adjust to the new gradient, while SGD adapts immediately.
  
</details> <!-- markdownlint-enable MD033 -->
