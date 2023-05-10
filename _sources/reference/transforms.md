# Fourier Transforms

## Fourier transform equations

$$
    G(f_x, f_y) = F\{g\} = \int \int g(x, y) \exp \left[ -j 2 \pi (f_x x + f_y y) \right] dx dy
$$ (fourier_transform)

$$
    g(x, y) = \mathfrak{F}^{-1} \{G\} = \int \int G(f_x, f_y) \exp \left[ j 2 \pi (f_x x + f_y y) \right] dx dy
$$ (inv_fourier_transform)

## Fourier transform relations

|  | Fourier Domain |
|---|---|
| $f(x)$ | $F(f_x)$ |
| $K f(x)$ | $K F(f_x)$ |
| $f(ax)$ | $\frac{1}{a} F \left( \frac{f_x}{a} \right)$ |
| $f(x-a)$ | $\exp (-j 2 \pi f_x a) F(f_x)$ |
| $\exp(j 2 \pi f_{xo}x) f(x)$ | $F(f_x - f_{xo})$ |

## Useful functions

```{table} Useful Functions
:name: functions-table

| Function | Definition |
|---|---|
| rectangle | $\mathrm{rect}(x) = \left\{ \begin{matrix} 1 & \lvert x \rvert \lt \frac{1}{2} \\ \frac{1}{2} & \lvert x \rvert = \frac{1}{2} \\ 0 & \mathrm{otherwise} \end{matrix} \right.$ |
| sinc | $\mathrm{sinc}(x) = \frac{\sin(\pi x)}{\pi x}$ |
| signum | $\mathrm{sgn}(x) = \left\{ \begin{matrix} 1 & x \gt 0 \\ 0 & x = 0 \\ -1 & x \lt 0 \end{matrix} \right.$ |
| triangle | $\Lambda(x) = \left\{ \begin{matrix} 1 - \lvert x \rvert & \lvert x \rvert \leq 1 \\ 0 & \mathrm{otherwise} \end{matrix} \right.$ |
| comb | $\mathrm{comb}(x) = \sum_{n=-\infty}^\infty \delta(x-n)$ |
| circle | $\mathrm{circ}(\sqrt{x^2 + y^2}) = \left\{ \begin{matrix} 1 & \sqrt{x^2 + y^2} \lt 1 \\ \frac{1}{2} & \sqrt{x^2 + y^2} = \frac{1}{2} \\ 0 & \mathrm{otherwise} \end{matrix} \right.$ |
```

## Useful equivalencies

$$
    \int_{-\infty}^\infty \mathrm{sinc} (x) dx = \int_{-\infty}^{\infty} \mathrm{sinc}^2(x) dx = 1
$$ (equiv_1)

$$
    \int_{0}^{\infty} \lvert \frac{J_1(x)}{x} \rvert ^2 dx = \frac{4}{3\pi}
$$ (equiv_2)

$$
    \int_0^\infty x | \frac{J_1(x)}{x} | ^2 dx = \frac{1}{2}
$$ (equiv_3)

$$
    \lim_{x\to\infty} \left( J_1(x) \right) = \frac{x}{2}
$$ (equiv_4)

## Fourier transforms

```{table} Fourier Transforms
:name: fourier-table

| Function | Definition | Transform |
|---|---|---|
| Impulse | $\delta (x)$ | $1$ |
| Uniform | $A$ | $2 \pi A \delta (f_x)$ |
| Cosine | $\cos (\omega_{xo} x)$ | $\pi \left[ \delta (\omega_x + \omega_{xo}) + \delta (\omega_x - \omega_{xo}) \right]$ |
| Sine | $\sin (\omega_{xo})$ | $j\pi \left[ \delta (\omega_x + \omega_{xo}) - \delta (\omega_x - \omega_{xo}) \right]$ |
| Rectangular | $\mathrm{rect}(x)$ | $\mathrm{sinc}(f_x)$ |
| Triangle | $\Lambda (x)$ | $\mathrm{sinc}^2(f_x)$ |
| Circle | $\mathrm{circ} \left( \frac{r}{R} \right)$ | $\pi R^2 \left[ 2 \frac{J_1 (2 \pi R f_x)}{2 \pi R f_x} \right]$ |
| Exponential | $\exp \left( -\lvert x \rvert \right)$ | $\frac{2}{1 + (2 \pi f_x)^2}$ |
| Gaussian | $\exp \left( - \pi x^2 \right)$ | $\exp \left( - \pi f_x^2 \right)$ |
| Chirp | $\exp (j \pi x^2)$ | $\exp \left( j \frac{\pi}{4} \right) \exp (-j \pi f_x^2)$ |
| Finite sum of pulses | $\sum_{n=-s}^s \delta (x-n)$ | $\frac{\sin (M \pi f_x)}{\sin (\pi f_x)}, M=2S+1$ |
| Infinite sum of pulses | $\sum_{n=-\infty}^\infty \delta (x-n)$ | $\sum_{n=-\infty}^\infty \delta (f_x - n)$ |
```