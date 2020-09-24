# Linearization at a singular point

## General theory

Given an ODE $\dot x=v(x)$, a point $a$ is called a *singular point* (a.k.a. zero, a.k.a. equilibrium state, a.k.a. critical point) of this ODE if $v(a)=0$.
In order to study the behaviour of the solutions of $\dot x=v(x)$ near $x=a$, we can replace $v(x)$ with its *linear part* at $a$.
More precisely, let $J$ be the jacobian matrix of $v$ at $a$:
$$
J=\left[\frac{\partial v_i}{\partial x_j}(a)\right]
$$

Then for $x\approx a$ we have $v(x)\approx J(x-a)$, so we can study $\dot y=Jy$ instead of $\dot x=v(x)$, where $y=x-a$.
If the real parts of all eigenvalues of $J$ are nonzero, then the phase portraits of the linearized system near $y=0$ is “qualitatively the same” as the phase portrait of the original system near $x=a$.

## Example 1: pendulum

Consider a pendulum (a massive bob on a weightless rod), see a diagram on [Wikipedia](https://en.wikipedia.org/wiki/Pendulum_(mathematics)). Its motion is given by $\ddot x=-\sin x$.

### Reformulating as a first order ODE

Let us introduce $y=\dot x$, then we have
\begin{align}
\dot x&=y;\\
\dot y&=-\sin x.
\end{align}

### Singular points

* We need to solve $y=0$, $-\sin x=0$.
* The solutions are $(x, y)=(\pi k, 0)$, $k\in\mathbb Z$.
* All the solutions $(2\pi k, 0)$ correspond to the bottom point of the circle,
  and all the solutions $((2k+1)\pi, 0)$ correspond to the top point of the circle.

### Linearization at $(0, 0)$

The jacobian matrix is given by
$$
J=\left.\begin{bmatrix}
    \frac{\partial y}{\partial x} & \frac{\partial y}{\partial y}\\
    \frac{\partial (-\sin x)}{\partial x} & \frac{\partial (-\sin x)}{\partial y}
  \end{bmatrix}\right|_{x=0, y=0} =
  \left.\begin{bmatrix}
    0 & 1\\
    -\cos x & 0
  \end{bmatrix}\right|_{x=0, y=0} =
  \begin{bmatrix} 0 & 1 \\ -1 & 0 \end{bmatrix}.
$$

The eigenvalues are $\pm i$, their **real parts** are zeros, so we **can't be sure** yet that the original nonlinear system has qualitatively the same phase portrait (a center) at $(0, 0)$ as it linearization.
Later we will discuss how to deal with this (spoiler: this nonlinear system has a center at $(0, 0)$).

### Linearization at $(\pi, 0)$

The jacobian matrix is given by
$$
J=\left.\begin{bmatrix}
    \frac{\partial y}{\partial x} & \frac{\partial y}{\partial y}\\
    \frac{\partial (-\sin x)}{\partial x} & \frac{\partial (-\sin x)}{\partial y}
  \end{bmatrix}\right|_{x=\pi, y=0} =
  \left.\begin{bmatrix}
    0 & 1\\
    -\cos x & 0
  \end{bmatrix}\right|_{x=\pi, y=0} =
  \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}.
$$

The eigenvalues are $\pm 1$, their **real parts** are nonzero, so and we **know for sure** that the phase portrait of the original nonlinear system near $(\pi, 0)$ is qualitatively the same as the phase portrait of the linearization, i.e., it has a saddle point with separatrices tangent to $x-\pi=\pm y$.

### Linearizations at other points

Since $\sin$ is a $2\pi$-periodic function, the linearizations at $(2\pi k, 0)$ will be centers, and linearizations at $(2\pi k+\pi, 0)$ will be saddles.

```python
import numpy as np
import matplotlib.pyplot as plt
Y, X = np.mgrid[-3:3:1000j, -4:5:1000j]
U, V = Y, -np.sin(X)
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 4))
ax1.streamplot(X, Y, U, V)
ax2.contour(X, Y, Y ** 2 / 2 - np.cos(X), 15)
```

## Example 2: damped pendulum

Let's add some friction (damping) to our system. The new equation is $\ddot x=-\dot x-\sin x$.

### Reformulating as a first order ODE

Let us introduce $y=\dot x$, then we have
\begin{align}
\dot x&=y;\\
\dot y&=-\sin x-y.
\end{align}

### Singular points

* We need to solve $y=0$, $-\sin x-y=0$; adding equations we get $-\sin x=0$.
* The solutions are $(x, y)=(\pi k, 0)$, $k\in\mathbb Z$.
* All the solutions $(2\pi k, 0)$ correspond to the bottom point of the circle,
  and all the solutions $((2k+1)\pi, 0)$ correspond to the top point of the circle.

### Linearization at $(0, 0)$

The jacobian matrix is given by
$$
J=\left.\begin{bmatrix}
    \frac{\partial y}{\partial x} & \frac{\partial y}{\partial y}\\
    \frac{\partial (-\sin x-y)}{\partial x} & \frac{\partial (-\sin x-y)}{\partial y}
  \end{bmatrix}\right|_{x=0, y=0} =
  \left.\begin{bmatrix}
    0 & 1\\
    -\cos x & -1
  \end{bmatrix}\right|_{x=0, y=0} =
  \begin{bmatrix} 0 & 1 \\ -1 & -1 \end{bmatrix}.
$$

The eigenvalues are $-\frac{1}{2}\pm i\frac{\sqrt{3}}{2}$, their **real parts** are negative, so we **know for sure** that the original nonlinear system has qualitatively the same phase portrait (a stable focus) at $(0, 0)$ as its linearization.

### Linearization at $(\pi, 0)$

The jacobian matrix is given by
$$
J=\left.\begin{bmatrix}
    \frac{\partial y}{\partial x} & \frac{\partial y}{\partial y}\\
    \frac{\partial (-\sin x-y)}{\partial x} & \frac{\partial (-\sin x-y)}{\partial y}
  \end{bmatrix}\right|_{x=\pi, y=0} =
  \left.\begin{bmatrix}
    0 & 1\\
    -\cos x & -1
  \end{bmatrix}\right|_{x=\pi, y=0} =
  \begin{bmatrix} 0 & 1 \\ 1 & -1 \end{bmatrix}.
$$

The eigenvalues are $\frac{-1\pm\sqrt{5}}{2}$, their **real parts** are nonzero, so and we **know for sure** that the phase portrait of the original nonlinear system near $(\pi, 0)$ is qualitatively the same as the phase portrait of the linearization, i.e., it has a saddle point.

### Linearizations at other points

Since $\sin$ is a $2\pi$-periodic function, the linearization at $(2\pi k, 0)$ will be a stable focus, and the linearization at $(2\pi k+\pi, 0)$ will be a saddle.

```python
import numpy as np
import matplotlib.pyplot as plt
Y, X = np.mgrid[-3:3:1000j, -4:5:1000j]
U, V = Y, -np.sin(X)-Y
plt.streamplot(X, Y, U, V)
```
