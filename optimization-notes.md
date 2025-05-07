# Multi-Layer Perceptrons, Stochastic Gradient Descent, and Optimization

## Outline

- [Multi-Layer Perceptrons, Stochastic Gradient Descent, and Optimization](#multi-layer-perceptrons-stochastic-gradient-descent-and-optimization)
  - [Outline](#outline)
  - [Multi-Layer Perceptrons](#multi-layer-perceptrons)
    - [Motivation](#motivation)
    - [Architecture](#architecture)
    - [Forward Pass](#forward-pass)
    - [Backpropagation](#backpropagation)
  - [Optimization](#optimization)
    - [Motivation](#motivation-1)
    - [Problems](#problems)
  - [SGD](#sgd)

## Multi-Layer Perceptrons

### Motivation

Last lecture, we learned about perceptrons, a type of neural network that takes input features and makes a binary decision. Perceptrons work well when the data is linearly separable, meaning that a straight line (hyperplane) can cleanly divide the classes. However, perceptrons fail when the decision boundary is not linearly separable; for example, in the classic XOR problem. So how can we create non-linear decision boundaries?

The answer is surprisingly elegant. If a single perceptron doesn't work, we can combine **multiple** together to create non-linear decision boundaries. This layered structure of stacking multiple perceptrons with non-linear activations is what defines a multi-layer perceptron (MLP). Just as we can approximate curves with small straight-line segments in calculus, we can approximate non-linear decision boundaries with linear perceptrons.

### Architecture

An MLP consists of an input layer, one or more hidden layers with neurons, and an output layer. Each neuron in a hidden layer computes a **weighted** sum of inputs from the previous layer, adds a bias, and then applies a  **non-linear** activation function.

Let's see an example of this in action!
<img src=https://raw.githubusercontent.com/William-Leung/cs4782-optimization-notes/main/sample_neural_network.png>
Figure 1: Example structure of a simple MLP with two input features $x_1, x_2$, two hidden neurons $u$ and $v$ in a hidden layer, and an output neuron $z$.

Now, how do we use an MLP? During training, the input is passed

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
