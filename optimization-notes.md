# MLP, SGD, and Optimization

Last lecture, we saw how to represent data with models like linear classifiers. But the base model is only so good; we need to

## MLP

### Forward Pass

### Backpropagation



## Gradient Descent

### Problems

* **Convexity:**
* **Time Complexity**:

## SGD

**Critical Thinking:** We said that momentum **almost** always converges faster than standard SGD, but why did we say almost? In what scenarios could standard SGD converge to the minimum faster than momentum?
<!-- markdownlint-disable MD033 -->
[//]: # (The line above disables the flagging for inline HTML)

<details>
  <summary>Answer</summary>
  
* **High Momentum Coefficient:** If the momentum coefficient $\mu$ is too high, it can cause the optimizer to overshoot minima or oscillate in narrow valleys. In these cases, standard SGD, despite being slower,may descend towards the minimum more directly and thus faster.
* **Noisy Gradients:** If gradient estimates have a lot of noise that is uncorrelated, momentum can actually hinder progress by following the noise. On the other hand, vanilla SGD ignores the previous noisy gradients.
* **Sharp Curvature:** In regions with flat gradients followed by steep drops (plateaus into ravines), momentum may take longer to adjust to the new gradient, while SGD adapts immediately.
  
</details> <!-- markdownlint-enable MD033 -->