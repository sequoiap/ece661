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

```{figure} ../../images/part1/psfdelta.png
---
name: psfdelta-fig
---
Optical delta object.
```

First, we'll calculate the field of the object right before the lens.

$$
    E_1(x,y)
$$

Now we'll calculate the field immediately after the lens. Apply the quadratic
phase shift:

$$
    E_2(x,y)
$$

Use a Fresnel diffraction integral to calculate the field at the image plane
($z = d_i$).

Since in the end we only care about relative magnitude, we'll drop the common
phase and amplitude terms.

$$
    E_f(x,y)
$$

## Modulation Transfer Function

Often what we want with an optical system is to determine the contrast of an
imaging system.

```{figure} ../../images/part1/mtfcontrast.png
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

