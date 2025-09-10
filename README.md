# makemore

Karpathy's tutorial

## Maximum Likelihood Estimation (MLE)

Maximum Likelihood Estimation is a fundamental statistical method used in this project for parameter estimation. Below is a comprehensive overview based on the [Wikipedia article on MLE](https://en.wikipedia.org/wiki/Maximum_likelihood_estimation).

### What is MLE?

Maximum Likelihood Estimation (MLE) is a method of estimating the parameters of an assumed probability distribution, given some observed data. This is achieved by maximizing a likelihood function so that, under the assumed statistical model, the observed data is most probable.

### Key Principles

1. **Objective**: Find parameter values that maximize the probability of observing the given data
2. **Likelihood Function**: A function that measures how likely it is to observe the data given specific parameter values
3. **Log-Likelihood**: Often used in practice as it's computationally more convenient (logarithm is monotonic)

### Mathematical Foundation

Given:

- A set of observations modeled as a random sample
- An unknown joint probability distribution with parameters θ
- A parametric family of distributions {f(·;θ) | θ ∈ Θ}

The goal is to find:

```text
θ̂ = argmax L_n(θ; y)
     θ∈Θ
```

Where L_n is the likelihood function evaluated at the observed data.

### Properties of MLE

1. **Consistency**: Under regularity conditions, MLE converges to the true parameter value as sample size increases
2. **Functional Invariance**: If θ̂ is the MLE of θ, then g(θ̂) is the MLE of g(θ) for any function g
3. **Efficiency**: MLE achieves the Cramér-Rao lower bound asymptotically
4. **Asymptotic Normality**: Under regularity conditions, MLE is approximately normally distributed for large samples

### Practical Considerations

#### When to Use MLE

- When you have a parametric model for your data
- When you need efficient parameter estimates
- When working with large samples

#### Computational Methods

- **Analytical Solutions**: Sometimes likelihood equations can be solved explicitly
- **Numerical Optimization**: Often required when closed-form solutions don't exist
  - Gradient descent
  - Newton-Raphson method
  - Quasi-Newton methods (BFGS, L-BFGS)

### Relation to Other Concepts

1. **Bayesian Inference**: MLE is equivalent to Maximum A Posteriori (MAP) estimation with a uniform prior
2. **Cross-Entropy**: Maximizing likelihood is equivalent to minimizing cross-entropy between the empirical distribution and the model
3. **Kullback-Leibler Divergence**: MLE minimizes KL divergence from the true distribution to the model

### Application in Neural Language Models

In the context of character-level language models like makemore:

1. **Model Parameters**: The neural network weights are the parameters θ to be estimated
2. **Likelihood**: The probability of generating the observed character sequences
3. **Training**: Gradient-based optimization to maximize log-likelihood (or minimize negative log-likelihood)
4. **Practical Implementation**: Often uses stochastic gradient descent on mini-batches

### Example in Language Modeling

For a character-level model predicting the next character:

- **Data**: Sequences of characters from training names
- **Parameters**: Neural network weights
- **Likelihood**: Product of probabilities of correct next-character predictions
- **Optimization**: Minimize negative log-likelihood (cross-entropy loss)

### References

- [Maximum Likelihood Estimation - Wikipedia](https://en.wikipedia.org/wiki/Maximum_likelihood_estimation)
- Original article provides extensive mathematical details and additional examples
