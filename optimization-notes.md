# Multi-Layer Perceptrons, Stochastic Gradient Descent, and Optimization

## Outline

- [Multi-Layer Perceptrons, Stochastic Gradient Descent, and Optimization](#multi-layer-perceptrons-stochastic-gradient-descent-and-optimization)
  - [Outline](#outline)
  - [Multi-Layer Perceptrons](#multi-layer-perceptrons)
    - [Motivation](#motivation)
    - [Forward Pass](#forward-pass)
    - [Backpropagation](#backpropagation)
  - [Gradient Descent](#gradient-descent)
    - [Problems](#problems)
  - [SGD](#sgd)

## Multi-Layer Perceptrons

### Motivation

Last lecture, we learned about pereptrons, a type of neural network which given some input features, can make a binary decision. Perceptrons work well when the data is linearly separable, meaning that a straight line (hyperplane) can cleanly divide the classes. However, perceptrons fail when the decision boundary is not linearly separable; for example, in the classic XOR problem. So how can we create non-linear decision boundaries?

The answer is to combine multiple perceptrons in hidden layers. By combining multiple perceptrons together, we can create models called multi-layer perceptrons (MLPs). MLPs consist of an input layer, one or more hidden layers with neurons, and an output layer. Each neuron in a hidden layer computes a **weighted** sum of inputs from the previous layer, and then applies a **non-linear** activation function. Stacking these layers together allows the model to form complex decision boundaries and overcome the linearity limitation.

Let's look at an example of this in action!

### Forward Pass

### Backpropagation

## Gradient Descent

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
