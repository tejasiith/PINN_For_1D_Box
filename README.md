# Solving 1D Particle-in-a-Box using Physics-Informed Neural Network (PINN)

This repository implements a Physics-Informed Neural Network (PINN) to solve the time-independent Schrödinger equation for a particle confined in a one-dimensional infinite potential well — commonly known as the "particle-in-a-box" problem.

## Objective

To train a PINN to approximate the wavefunctions of a quantum particle in a 1D infinite potential well (box), using physical laws embedded in the loss function instead of relying solely on data.

## Background

The time-independent Schrödinger equation for a 1D box of length \( L \) is:

\[
- \frac{1}{2} \frac{d^2\psi(x)}{dx^2} = E \psi(x), \quad x \in (0, L)
\]

With boundary conditions:  
\[
\psi(0) = \psi(L) = 0
\]

Analytical solutions exist, but this PINN approach allows for generalization and extension to more complex quantum systems.

## Model Details

- **Input**: Position `x`
- **Output**: Wavefunction value `ψ(x)`
- **Network**: 
  - 3–4 fully connected hidden layers
  - Each with 64–128 neurons
  - Activation: `tanh`
- **Loss Function**:
  - Physics loss (residual of Schrödinger equation)
  - Boundary condition loss
  - Normalization loss
- **Optimizer**: Adam
- **Framework**: PyTorch

## Training

- Domain: `x ∈ [0, 1]`
- Uses automatic differentiation (PyTorch) for computing second derivatives
- Trained to approximate solutions for ground and excited states

## Results

- Model successfully learns the sine-shaped wavefunctions corresponding to quantum states.
- Matches well with analytical solutions.
- Generalizes to excited states by training with corresponding eigenenergies.
