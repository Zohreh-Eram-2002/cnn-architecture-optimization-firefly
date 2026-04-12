# CNN Architecture Optimization using Firefly Algorithm

## Overview

This project explores the intersection of **Deep Learning** and **Bio-inspired Optimization** by applying the Firefly Algorithm to automatically design and optimize Convolutional Neural Network (CNN) architectures.

Instead of manually tuning hyperparameters and network structures, this approach treats architecture design as an optimization problem. Each candidate CNN architecture is represented as a "firefly," and the population evolves over time toward better-performing configurations.

The framework is evaluated on the CIFAR-10 dataset, demonstrating how metaheuristic algorithms can be effectively used for **Neural Architecture Search (NAS)**.

---

## Objective

The main goals of this project are:

* **Automated Architecture Search**
  Eliminate manual trial-and-error in CNN design by using an intelligent optimization strategy.

* **Hybrid Intelligence**
  Combine deep learning with swarm intelligence (Firefly Algorithm) to create adaptive systems.

* **Efficient Exploration of Search Space**
  Explore multiple CNN configurations in parallel and iteratively improve them.

* **Performance Optimization**
  Identify architectures that achieve higher classification accuracy with minimal manual intervention.

---

## Key Concepts

### Convolutional Neural Networks (CNN)

CNNs are widely used for image classification tasks. In this project, the architecture (number of layers, filters, etc.) is dynamically generated instead of being fixed.

### Firefly Algorithm

A nature-inspired optimization algorithm based on the flashing behavior of fireflies:

* Each firefly represents a candidate solution (CNN architecture)
* Brighter fireflies (higher accuracy) attract others
* Movement is based on relative performance

### Neural Architecture Search (NAS)

This project is a simplified form of NAS, where:

* The search space includes:

  * Number of convolutional layers
  * Number of filters
  * Fully connected layer size
* The objective is to maximize classification accuracy

---

## Dataset

* **Dataset:** CIFAR-10
* **Classes:** 10 object categories (airplane, car, bird, cat, etc.)
* **Image Size:** 32×32 RGB images
* **Loading:** Automatically downloaded using PyTorch

The dataset is preprocessed using normalization to stabilize training.

---

## Methodology

The optimization process follows these steps:

1. **Initialization**

   * Generate a population of random CNN architectures
   * Each architecture varies in:

     * Number of convolutional layers
     * Number of filters
     * Fully connected layer size

2. **Model Construction**

   * Dynamically build CNN models based on each firefly's configuration

3. **Training Phase**

   * Each model is trained briefly (lightweight training for efficiency)
   * Uses stochastic gradient descent (SGD)

4. **Evaluation**

   * Accuracy is measured on the test dataset
   * This serves as the "brightness" of each firefly

5. **Optimization (Firefly Movement)**

   * Poorer-performing architectures move toward better ones
   * Partial parameter sharing between architectures

6. **Iteration**

   * The process repeats for multiple generations
   * The population gradually converges toward optimal architectures

---

## Output

After running the optimization process, the system provides:

* Best CNN architecture found (layer configuration)
* Corresponding classification accuracy
* Evolution of model performance across iterations

Example output:

```text
Best architecture found: {
  'conv_layers': [(32, 3), (64, 3), (64, 3)],
  'fc_units': 256,
  'accuracy': 0.78
}
```

---

## Insights & Observations

* Metaheuristic methods can effectively explore architectural design spaces
* Even with short training cycles, meaningful performance differences emerge
* Diminishing returns may occur after several iterations (convergence behavior)

---

## Limitations

* Computationally expensive (training multiple models)
* Uses short training cycles (may not reflect full performance)
* Limited search space (simple CNN structures only)

---

## Future Work

* Implement advanced NAS methods:

  * Reinforcement Learning-based search
  * Evolutionary Algorithms
* Expand search space:

  * Different activation functions
  * Skip connections (ResNet-style)
* Parallel training using multi-GPU setups
* Apply to larger datasets (e.g., ImageNet)
* Integrate early stopping and smarter evaluation strategies

---

## Author

Zohreh Eram

---

## Support

If you found this project useful or interesting, consider giving it a ⭐ on GitHub!
