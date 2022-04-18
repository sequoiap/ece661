# Lenses

## Conjugate Equation

Let's start by looking at a single spherical surface. We will use Snell's Law.

Here is our sign convention:

* Light travels from left to right
* Distances up are positive
* Distances to the right are positive
* Counterclockwise (CCW) angles are positive
* For light travelling right to left, use n as negative.

```{figure} ../../images/part1/lenses1.png
---
name: lenses1-fig
---
Single spherical surface interface.
```

Apply Snell's Law at the interface:

\begin{equation}
    n \sin (i) = n' \sin (i')
\end{equation}

Using the paraxial approximation,

$$
    n i = n' i'
$$ (paraxial_snell)

We need to relate u to i and u' to i'.

$$
    u + \phi + q = 180 \\
    q = 180 - u - \phi \\
    q + i = 180 \\
    i = 180 - 180 + u + \phi \\
    |i| = |u| + | \phi | \\
$$

From our sign convention, $u \gt 0$, $\phi \lt 0$, and $i \gt 0$. Hence,

$$
    i = u - \phi
$$

Next, we'll relate u' to i':

$$
    |i'| + |u'| + 180  - |\phi| = 180 \\
    |i'| = - |u'| + |\phi|
$$

Again, noting that $i' \gt 0$, $\phi \lt 0$, and $u' \lt 0$,

$$
    i' = u' - \phi
$$

Substituting into {eq}`paraxial_snell`, we get:

$$
    n (u - \phi) = n' (u' - \phi)
$$

Now, we need to relate the angle equation to position.

```{figure} ../../images/part1/lenses2.png
---
name: lenses2-fig
---
Relating angle to position.
```

Again, using the paraxial approximation,

$$
    \tan u \approx u = \frac{h}{S_o} \\
    \sin \phi \approx \phi = \frac{h}{R} \\
    \tan u' \approx u' = \frac{h}{S_i} 
$$

$$
    n (u - \phi) = n' (u' - \phi) \\
    n \left( \frac{h}{S_o} - \frac{h}{R} \right) = n' \left( \frac{h}{S_i} - \frac{h}{R} \right) \\
    \frac{n}{S_o} - \frac{n}{R} = \frac{n'}{S_i} - \frac{n'}{R} \\
    \frac{n}{S_o} - \frac{n'}{S_i} = (n - n') \frac{1}{R} \\
$$

Or, 

$$
    \frac{n'}{S_i} - \frac{n}{S_o} = (n' - n) \frac{1}{R} \\
$$ (conjugate_equation)

where $1 / R \equiv C$ is the curvature. {eq}`conjugate_equation` is known as
the **conjugate equation**.

## Thin Lens

We'll use the conjugate equation for a single surface to get the conjugate
equation for a thin lens.

```{figure} ../../images/part1/conjugatesurface.png
---
name: conjugatesurface-fig
---
A single surface.
```

The conjugate equation for the picture in {numref}`conjugatesurface-fig` is:

$$
    \frac{n'}{S_i} - \frac{n}{S_o} = \frac{(n' - n)}{R} \\
$$

```{figure} ../../images/part1/conjugatethinlens.png
---
name: conjugatethinlens-fig
---
A thin lens.
```

The thin lens is simply the single surface, replicated; once for entry, and 
once for exit. The entry and exit of the material have the same index, with
a different index in the middle. We assume zero separation between lens 
surfaces.

```{figure} ../../images/part1/conjugatethinlensmodel.png
---
name: conjugatethinlensmodel-fig
---
A thin lens. a) The first encountered surface. b) The second encountered 
surface.
```

The following are true for the first surface:

$$
    S = S_o \\
    S' = S_1 \\
    n = n_1 \\
    n' = n_2 \\
    R = R_1 
$$

The conjugate equation for the first surface is

$$
    \frac{n_2}{S_1} - \frac{n_1}{S_o} = \frac{(n_2 - n_1)}{R_1} \\
    \frac{n_2}{S_1} = \frac{n_1}{S_o} + \frac{(n_2 - n_1)}{R_1}
$$

The following are true for the second surface:

$$
    S = -S_1 \\
    S' = S_i \\
    n = n_2 \\
    n' = n_1 \\
    R = R_2 
$$

Hence,

$$
    \frac{n_1}{S_i} - \frac{n_2}{S_1} = \frac{(n_1 - n_2)}{R_2} \\
$$

Substituting $n_2 / S_i$ from before, 

$$
    \frac{n_1}{S_i} - \frac{n_1}{S_o} - \frac{n_2 - n_1}{R_1} = \frac{(n_1 - n_2)}{R_2} \\
    \frac{1}{S_i} - \frac{1}{S_o} = \left(\frac{1}{n_1}\right) \left( \frac{n_1 - n_2}{R_2} + \frac{n_2 - n_1}{R_1} \right)
$$

$$
    \frac{1}{S_i} - \frac{1}{S_o} = \left(\frac{n_2 - n_1}{n_1}\right) \left(\frac{1}{R_1} - \frac{1}{R_2}\right) = \frac{1}{f}
$$ (thin_lens_conjugate_equation)

Remember that distances to the left are negative and distances to the right are positive.

If we define $S_o$ being left of the lens as "positive", we get

$$
    \frac{1}{S_i} + \frac{1}{S_o} = \frac{1}{f}
$$ (object_image_equation)

## Imaging

Now, let's look at producing an image from an object using a single thin lens.

We will analyze the lens and image using the following properties:

1. A ray passing through the focal point is bent parallel to the axis of symmetry.
2. An incident ray parallel to the lens axis is bent to pass through the back focal point.
3. A ray passing through the center of the lens is unchanged in direction.
4. A point in the object space is imaged to a point in the image space.
5. Parallel rays image to a point (a lens converts from incident angle to a point).

## Magnification