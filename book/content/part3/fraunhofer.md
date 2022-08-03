# Fraunhofer Approximation

{download}`fraunhofer_examples.pdf <../../files/fraunhofer_examples.pdf>`.

{download}`LED_diffraction_example.pdf <../../files/LED_diffraction_example.pdf>`.

## Example 1: A Square Aperture

A $100 \mu m \times 1 \mathrm{mm}$ aperture illuminated by a laser $\lambda = 500 nm$.

1. Find the diffraction pattern.
2. Find the necessary distance away from the aperture.

Assume that the incident field is a plane wave

$$
    E(x, y) = \frac{e^{j k z}}{j \lambda z} e^{j \frac{k}{2z}(x^2 + y^2)} \mathfrak{F}\{ P(x, y) \} |_{f_x = x / \lambda z, f_y = y / \lambda z}
$$

$$
    P(x) = \left\{ \begin{matrix} 1 & \lvert x \rvert \leq 50 \mu m \\ 0 & \mathrm{otherwise} \end{matrix} \right.
$$

This is similar to

$$
    \mathrm{rect}(x) = \left\{ \begin{matrix} 1 & \lvert x \rvert \leq \frac{1}{2} \\ 0 & \mathrm{otherwise} \end{matrix} \right.
$$

\begin{align}
    \begin{split}
        \mathrm{rect}(a x) &= \left\{ \begin{matrix} 1 & \lvert a x \rvert \leq \frac{1}{2} \\ 0 & \mathrm{otherwise} \end{matrix} \right. \\
        &= \left\{ \begin{matrix} 1 & \lvert x \rvert \leq \frac{1}{2a} \\ 0 & \mathrm{otherwise} \end{matrix} \right. \\
   \end{split}
\end{align}

Let $a = \frac{1}{100} \mu m$.

$$
    P(x) = \mathrm{rect}(\frac{x}{100\mu m}) = \left\{ \begin{matrix} 1 & \lvert x \rvert \leq 50 \mu m \\ 0 & \mathrm{otherwise} \end{matrix} \right.
$$

Now take the Fourier transform,

$$
    \mathfrak{F}\{ \mathrm{rect}(ax) \} = \frac{1}{a} \mathrm{sinc} \left( \frac{F_x}{a} \right)
$$

$$
    P(F_x) = 100 \times 10^{-6} \mathrm{sinc} (100 \times 10^{-6} F_x)
$$

Similar for the y-direction

$$
    P(F_y) = 10^{-3} \mathrm{sinc} (10^{-3} F_y)
$$

where

$$
    F_x = \frac{x}{\lambda z}, F_y = \frac{y}{\lambda z}
$$

Hence,

$$
    E(x, y) = \frac{e^{j k z}}{j \lambda z} e^{j \frac{k}{2z} (x^2 + y^2)} (100 \times 10^{-6}) (10^{-3}) \mathrm{sinc} \left( \frac{100 \times 10^{-6} x}{\lambda z} \right) \mathrm{sinc} \left( \frac{10^{-3} y}{\lambda z} \right)
$$

Zeros are at

$$
    \frac{100 \times 10^{-6} x}{\lambda z} = \pm 1
$$

$$
    \theta_x = \frac{x}{z} = \frac{\lambda}{100 \times 10^{-6}} = \frac{0.5 \times 10^{-6}}{100 \times 10^{-6}}
$$

$$ 
    \theta_x = 5 \mathrm{mrad} = 0.29^\circ
$$