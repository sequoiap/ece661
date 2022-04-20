# Lens Performance

We want to calculate the intensity distribution at the image for an arbitrary
object and optical system.

In linear system theory we have the concept of the impulse response of the
system.

```{figure} ../../images/part3/linearsystem.png
---
name: linearsystem-fig
---
A linear system's impulse response.
```

$h(t)$ is the impulse response of the system. It is calculated by determining
the output if the input is a $\delta$ function.

We want to extend this to 2 dimensional optical systems.

## Point Spread Function

```{figure} ../../images/part3/psf.png
---
name: psf-fig
---
2-dimensional response of an optical system.
```

In {numref}`psf-fig`, 

* $f(x,y)$ is an arbitrary object.
* $g(x,y)$ is the image of the object at the image plane.

Point Spread Function (PSF)
: The 2D impulse respone of the optical system.

The PSF is used to characterize an optical system.

The object is a delta function:

$$
    E_{obj} = \delta (x) \delta (y) \delta (z + d_0)
$$

```{figure} ../../images/part3/psfdelta.png
---
name: psfdelta-fig
---
Optical delta object.
```

First, we'll calculate the field of the object right before the lens.

$$
    E_1(x,y) &= \frac{e^{j k d_0}}{j \lambda d_0} \int \int _{-\infty} ^\infty \delta (x') \delta (y') \exp \left[ -\frac{j k}{2 d_0} \left( (x-x')^2 + (y-y')^2 \right) \right] dx' dy' \\
    &= \frac{e^{j k d_0}}{j \lambda d_0} \exp \left[ -\frac{j k}{2 d_0} (x^2 + y^2) \right]
$$

Now we'll calculate the field immediately after the lens. Apply the quadratic
phase shift:

$$
    E_2(x,y) &= E_1(x, y) \exp \left[ \frac{j k}{2 f} (x^2 + y^2) \right] \\
    &= \frac{e^{j k d_0}}{j \lambda d_0} \exp \left[ -\frac{j k}{2 d_0} (x^2 + y^2) + \frac{j k}{2 f} (x^2 + y^2) \right] \\
    &= \frac{e^{j k d_0}}{j \lambda d_0} \exp \left[ \frac{j k}{2} \left(\frac{1}{f} - \frac{1}{d_0} \right) (x^2 + y^2) \right]
$$

Use a Fresnel diffraction integral to calculate the field at the image plane
($z = d_i$).

Since in the end we only care about relative magnitude, we'll drop the common
phase and amplitude terms.

$$
    E_f(x,y) = \int \int _\sum \exp \left[ \frac{j k}{2} \left( \frac{1}{f} - \frac{1}{d_o} \right) (x'^2 + y'^2) \right] \exp \left[ - \frac{j k}{2 d_i} \left( (x-x')^2 + (y-y')^2 \right) \right] dx' dy'
$$

Using the conjugate equation {eq}`object_image_equation` from geometrical 
optics,

$$
    \frac{1}{f} - \frac{1}{d_o} = \frac{1}{d_i}
$$

$$
    E_f(x,y) &= \int \int _\sum \exp \left[ \frac{j k}{2 d_i} (x'^2 + y'^2) \right] \exp \left[ - \frac{j k}{2 d_i} \left( x'^2 + y'^2 \right) \right] \exp \left[ - \frac{j k}{2 d_i} (x^2 + y^2) \right] \exp \left[ \frac{j k}{d_i} (x x' + y y') \right] dx' dy' \\
    &= \exp \left[ - \frac{j k}{2 d_i} (x^2 y^2) \right] \int \int _\sum \exp \left[ \frac{j k}{2} (x'^2 + y'^2) \left( \frac{1}{d_i} - \frac{1}{d_i} \right) \right] \exp \left[ \frac{j k}{d_i} (x x' + y y') \right] dx' dy' \\
    &= \mathrm{PSF}(x,y) = \int \int _\sum \exp \left[ \frac{j k}{d_i} (x x' + y y') \right] dx' dy'
$$

If the lens is perfect,

$$
    \mathrm{PSF}(x,y) = \mathfrak{F} \left. \left\{ \textrm{Aperture} \right\} \right|_{f_x = x / \lambda d_i, f_y = y / \lambda d_i}
$$ (psf_perfect_lens)

$$
    \mathrm{PSF}(x,y) = \mathfrak{F} \left. \left\{ \textrm{Aperture} \left( \text{difference from spherical wave} \right) \right\} \right|_{f_x = x / \lambda d_i, f_y = y / \lambda d_i}
$$

Huygen's principle:

$$
    E_i(x,y) = E_0(x, y) \otimes \mathrm{PSF}(x, y)
$$ (huygens_principle)

## Modulation Transfer Function

Often what we want with an optical system is to determine the contrast of an
imaging system.

```{figure} ../../images/part3/mtfcontrast.png
---
name: mtfcontrast-fig
---
Contrast.
```

See www.normankoren.com/Tutorials/MTF.html.

The contrast is

$$
    \gamma = \frac{E_{max} - E_{min}}{E_{max}+E_{min}}
$$ (contrast)

It is more practical to use areance,

$$
    a = \frac{E_{max} - E_{min}}{2} + E_{min}
$$ (areance)

and variance of areance,

$$
    b = E_{max} - a
$$

The ratio is the modulation $M = \frac{b}{a}$.

The modulation transfer function is 

$$
    T = \frac{M_{image}}{M_{object}}
$$ (mtf)

$T$, as a function of spatial frequency, is

$$
    \mathrm{Modulation} \mathrm{Transfer} \mathrm{Function} \quad \mathrm{MTF} = T(f)
$$

Spatial frequency of an image
: The number of lines or other detail within a given length, usually written in
  units of inverse mm.

### Calculating MTF

MTF is the angular spectrum of the optical system.

Since most imaging systems use incoherent light, we use the power PSF

$$
    \mathrm{PPSF} = |\mathrm{PSF}|^2 = \mathrm{PSF}(x,y) \mathrm{PSF}^*(x,y)
$$

\begin{equation}
    \mathrm{MTF} = | \int \int_{-\infty}^\infty \mathrm{PSF}(x,y) \mathrm{PSF}^*(x,y) \exp \left[ -j 2 \pi (f_x x + f_y y) \right] |
\end{equation}

where

$$
    \mathrm{PSF}(x,y) &= \int \int_{-\infty}^\infty A(x_1, y_1) \exp \left[ j \frac{k}{f} (x_1 x + y_1 y) \right] dx_1 dy_1 \\
    \mathrm{PSF}^*(x,y) &= \int \int_{-\infty}^\infty A^*(x_2, y_2) \exp \left[ -j \frac{k}{f} (x_2 x + y_2 y) \right] dx_2 dy_2
$$

$$
    \mathrm{MTF} = | \int \int_{-\infty}^\infty A(x_1, y_1) A^*(x_2, y_2) \exp \left[ j \left( \frac{k x_1}{f} - \frac{k x_2}{f} - 2 \pi f_x \right) x + j \left( \frac{k y_1}{f} - \frac{k y_2}{f} - 2 \pi f_y \right) y \right] |
$$

To eliminate the exponential, let

$$
    \frac{k x_1}{f} &= \frac{k x_2}{f} + 2 \pi f_x \\
    x_1 &= x_2 + \frac{2 \pi f}{k} f_x \\
    x_1 &= x_2 + \lambda f f_x \\
    y_1 &= y_2 + \lambda f f_y
$$

$$
    \mathrm{MTF} = | \int \int_{-\infty}^\infty A(x_2 + \lambda f f_x, y_2 + \lambda f f_y) A^*(x_2, y_2) dx_2 dy_2 |
$$

or, more simply

$$
    \mathrm{MTF} = | \int \int_{-\infty}^\infty A(\hat{\alpha} + \alpha, \hat{\beta} + \beta) A^*(\hat{\alpha}, \hat{\beta}) d\hat{\alpha} d\hat{\beta} | _{\alpha = f_x \lambda f, \beta = f_y \lambda f}
$$

<div class="admonition note" name="html-admonition">
<p class="admonition-title">Example: MTF of a perfect lens</p>


Let's calculate the MTF of a perfect lens with a circular aperture.

$$
    A(x,y) = \left\{ \begin{matrix}
        1 & \sqrt{x^2 + y^2} \leq R \\
        0 & \mathrm{otherwise}
    \end{matrix} \right.
$$

The MTF is the overlap between two circles.

$$
    \mathrm{MTF} = | \int \int_{-\infty}^\infty A(x+\alpha, y+\beta) A^*(x, y) dx, dy |
$$

since the aperture function is purely real, $A = A^*$.

```{figure} ../../images/part3/mtfoverlap.png
---
name: mtfoverlap-fig
---
The MTF is the overlap between two circles.
```

```{figure} ../../images/part3/circlearea.png
---
name: circlearea-fig
---
The overlapping area of the circles.
```

The shaded area is the area of $A_1$ (the area of the sector of the circle) minus
the area of $A_2$, which is the area of the triangle.

Knowing that $\Delta = \alpha / 2$, $\theta = \cos^{-1} \Delta / R$, we get as 
the area of the sector

$$
    A_1 &= 2 \int_0^R \int_0^{\cos^{-1}(\Delta / R)} \rho d\rho d\phi \\
    &= \rho^2 \theta |_0^R \\
    &= R^2 \cos^{-1} \left( \frac{\Delta}{R} \right)
$$

The area of the triangle is

$$
    A_2 &= (2) \left( \frac{1}{2} \right) (\Delta) \sqrt{R^2 - \Delta ^2} \\
    &= R^2 \left[ \cos^{-1} \left( \frac{\Delta}{R} \right) - \frac{\Delta}{R} \sqrt{1 - \left( \frac{\Delta}{R} \right) ^2} \right]
$$

$$
    \mathrm{MTF} = 2A = 2 R^2 \left[ \cos^{-1} \left( \frac{\Delta}{R} \right) - \frac{\Delta}{R} \sqrt{1 - \left( \frac{\Delta}{R} \right) ^2} \right]
$$

Given that $\Delta = \alpha / 2$,

$$
    \mathrm{MTF} = 2 R^2 \left[ \cos^{-1} \left( \frac{\alpha}{2 R} \right) - \frac{\alpha}{2 R} \sqrt{1 - \left( \frac{\alpha}{2 R} \right) ^2} \right]
$$

where $\alpha = f_r \lambda f$.

Normalizing yields

$$
    \mathrm{MTF} = \left( \frac{2}{\pi} \right) \left[ \cos^{-1} \left( \frac{f_r \lambda f}{2 R} \right) - \frac{f_r \lambda f}{2 R} \sqrt{1 - \left( \frac{f_r \lambda f}{2 R}^2 \right)} \right]
$$ (mtf_perfect_lens)

for $0 \lt f_r \lt \frac{2 R}{\lambda f}$.

The maximum spatial frequency is $f_{r, max} = \frac{2R}{f} \left( \frac{1}{\lambda} \right) = \frac{1}{\lambda f_\#}$.

</div>

```{figure} ../../images/part3/apodization1.png
---
name: apodization1-fig
---
Optical transfer functions with and without a Gaussian apodization.
```

```{figure} ../../images/part3/apodization2.png
---
name: apodization2-fig
---
Pupil amplitude transmittance and the corresponding OTF with and without a 
particular "inverse" apodization.
```