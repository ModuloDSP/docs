---
bibliography:
- ref.bib
- render_with_liquid: false
---

# Introduction

Complex numbers arise in various areas of science and engineering.
Examples include Fourier analysis, a fundamental tool in signal
processing, phasors for analyzing electrical circuits, and solving
special types of differential equations. The purpose of this article is
to present an overview of the theory behind complex numbers and discuss
their usefulness in a selected applications. By the end of the article,
we shall have an understanding of why, for instance, the following
integration is valid, and how it can be interpreted:

$$\int_{a}^{b} e^{ixt}dt = \frac{e^{ixt}}{ix} \Big|_{a}^b = \frac{1}{ix}(e^{ibt} - e^{iat})$$

The article is structured as follow: First, an overview of complex
numbers is presented. Subsequently, Fourier series, as a method for
decomposing a periodic function into the summation of sines and cosines
is discussed, and lastly the application of complex numbers in Fourier
series is explored.

## Complex numbers

A *complex number* is a number that consists of a real and an imaginary
part, and has the general form of:

$$a + bi$$

Where $a$ and $b$ are two Real numbers and $i$ is the imaginary number
$\sqrt{-1}$. Example of such numbers are $1+i$ and $4+3i$.

## Euler's formula

Euler's formula is a famous relation that states:

$$e^{ix} = \cos{x} + i\sin{x}$$

Where $x$ is a Real number.

An important remark about Euler's formula is that the relation is
sensible considering we have a proper definition for eix, i.e., *complex
exponentiation*. In other words, *what does it mean to raise a number to
a complex number?* There are a number of equivalent ways to define
complex exponentiation. One way is as follows:

$$e^z = 1 + z + \frac{{z}^2}{2!} +  \frac{{z}^3}{3!} +  \frac{{z}^4}{4!} + ...$$

Where $z$ is a complex number of the form $a + ib$. This definition is
based on the Taylor series expansion, and by choosing $z$ to be real,
the definition reduces to the real exponential function. With this
definition, replacing $z$ with $ix$ makes it straightforward to verify
Euler's formula. Specifically:

$$\begin{aligned}
    e^{ix} &= 1 + ix + \frac{{(ix)}^2}{2!} +  \frac{{(ix)}^3}{3!} +  \frac{{(ix)}^4}{4!} + \dots \\
    &= 1 + ix - \frac{{x}^2}{2!} - \frac{{ix}^3}{3!} + \frac{{x}^4}{4!} + \dots \\
    &= \left(1 - \frac{{x}^2}{2!} + \frac{{x}^4}{4!} - \frac{{x}^6}{6!} + \dots \right) + i \left(x - \frac{{x}^3}{3!} + \frac{{x}^5}{5!} - \frac{{x}^7}{7!} + \dots \right) \\
    &= \cos{x} + i\sin{x}
\end{aligned}$$

### Complex-valued real variable functions

A function is said to be a *complex-valued real-variable function* if
its domain is the set of real numbers and its range is the set of
complex numbers. Such a function has the form:

$$f(t) = u(t) + iv(t)$$

Example of such functions are $f(t) = t^3 + it$ and $f(t) = 1 + it^2$.

The derivative of a complex-valued real variable function, by
definition, is:

$$f'(t) = u'(t) + iv'(t) \label{eq:1}$$

For instance, the derivative of the function $f(t) = t^2 + it$ evaluates
to:

$$f'(t) = 2t + i$$

With these definitions, it can be proven that many rules that apply to
real-valued real-variable functions apply to these types of functions as
well. For instance, for a constant complex number $z_0 = x_0  + iy_0$,
we have:

$$(z_0f(t))' = z_0f'(t) \label{eq:2}$$

Equation [\[eq:2\]](#eq:2){reference-type="eqref" reference="eq:2"} can
be proven as:

$$\begin{aligned}
    (z_0 f(t))' 
    &= [(x_0 + i y_0)(u(t) + i v(t))]' \\
    &= \left[(x_0 u(t) - y_0 v(t)) + i(y_0 u(t) + x_0 v(t))\right]' \\
    &= (x_0 u(t) - y_0 v(t))' + i(y_0 u(t) + x_0 v(t))' \\
    &= (x_0 + i y_0)(u'(t) + i v'(t)) \\
    &= z_0 w'(t)
\end{aligned}$$

Another consequence of the way we define the differentiation of
complex-valued real-variable functions is the following:

$$(e^{z_0t})' = z_0e^{z_0t} \label{eq:3}$$

This relation can be proven in a similar manner to equation
[\[eq:2\]](#eq:2){reference-type="ref" reference="eq:2"} and also by
using Euler's relation i.e. $e^{ix} = \cos{x} + i\sin{x}$.

So far, we have discussed the definition of complex-valued real-variable
functions. As for their integration, the following definition is used:

$$\int_{a}^{b} f(t) dt = \int_{a}^{b}u(t) dt + i\int_{a}^{b} v(t) dt$$

An immediate consequence of defining the integral for such functions is
that the *Fundamental Theorem of Calculus*, which holds for real-valued
real-variable functions, also holds for these types of functions. Assume
we have $f$ as before, i.e. $f(t) = u(t) + iv(t)$ and also
$F(t) = U(t) + iV(t)$ where $U(t)$ and $V(t)$ are anti-derivative of
$u(t)$ and $V(t)$. Consequently:

$$\begin{aligned}
    \int_{a}^{b} f(t)\,dt 
    &= \left. U(x) \right|_a^b + \left. V(t) \right|_a^b \\
    &= [U(b) - iV(b)] - [U(a) + iV(b)] \\
    &= F(b) - F(a) \\
    &= \left. F(t) \right|_a^b
\end{aligned}$$

**Example:**

$$\begin{aligned}
    \int_{1}^{2} (1+it)\,dt = \int_{1}^{2} 1dt + i\int_{1}^{2} (t)dt = 1 + 1.5i
\end{aligned}$$

As with the case of derivative, it is also easy to show that the
integral of a generic complex exponential function $e^{zt}$, where
$z = a + ib$ follows the similar rule as with the real exponential
function:

$$\begin{aligned}
    \int_{a}^{b} e^{zt}\,dt = \frac{e^zt}{z} + C \quad\quad z \neq 0
\end{aligned}$$

## Fourier series

### Fourier series with real-valued coefficients

The Fourier series is a powerful tool that allows the decomposition of a
periodic function into a sum of sines and cosines. A periodic function
with the period of $T$ can be expressed using Fourier series via:

$$f(x) = \frac{a_0}{2} + \sum_{1}^{\infty}(a_n\cos{k \omega_0 t} + 
b_n\sin{k \omega_0 t}
)$$

Where $\omega_0 = \frac{2\pi}{T}$ is referred to as the *fundamental
frequency*. In this equation, $a_0$, $a_n$ and $b_n$ are referred to as
the Fourier series *coefficients* and are determined by:

$$\frac{a_0}{2} = \frac{1}{L} \int_{-L}^{L} f(x) dx$$

$$a_n = \frac{2}{L} \int_{-L}^{L} f(x) \cos{k \omega_0 t}  dx$$

$$b_n = \frac{2}{L} \int_{-L}^{L} f(x) \sin{k \omega_0 t}  dx$$

As an example, the square wave function over period is defined as:

$$f(t) = 
\begin{cases}
    1, & |t| < 0.5 \\
    0, & 0.5 < |t| < 1
\end{cases}$$

This is a square-wave with the duty cycle of $\% 50$, meaning that the
signal is *on* half of the times and *off* in the other half.

The Fourier series coefficients are computed as:

$$\begin{aligned}
    \frac{a_0}{2} &= \frac{1}{2} \int_{0}^{2} f(t)\,dt = \frac{1}{2} \int_{0}^{0.5}1dt + \frac{1}{2} \int_{1.5}^{2}1 dt = 0.5 \\
    a_n &= \frac{2}{2} \int_{0}^{2} f(t)\cos(k\omega_0 t)\,dt =
    \int_{0}^{0.5} \cos(k\omega_0 t) +  \int_{1.5}^{2} \cos(k\omega_0 t) dt = 
     \frac{2}{k\pi} \sin\left(k \frac{\pi}{2}\right) \\
    b_n &= \int_{0}^{2} f(t)\sin(k\omega_0 t)\,dt = 0
\end{aligned}$$

The example showed how the Fourier series coefficients can be computed
for a function, and comparing the resulting Fourier series confirms that
the series converges to the function at all points except at the
discontinuities. An important question that may now arise is regarding
the *convergence of Fourier series*. Specifically, we may ask: *Is there
a guarantee that the resulting coefficients lead to a series that
converges to the function?*

This question turns out to be difficult to answer for several reasons.
First, we must be precise about what we mean by the Fourier series
converging to the function. One interpretation is through the definition
of pointwise convergence, where the series converges to the function *at
each individual point*. By another definition, the series may not
converge at every point, but instead approaches the function in an
\"average\" sense over an interval. A comprehensive study of Fourier
series convergence is presented in [@brown2009complex]. Despite the
plethora of theorems regarding Fourier series and its convergence, it
can be shown that if a function satisfies the following three
properties:

1.  Over a period, the integral of the function must be finite, i.e.,
    the function must be *absolutely integrable*.

2.  Over a single period, the function has a finite number of maxima and
    minima.

3.  For any finite interval of the function, there are a finite number
    of discontinuities, and the values of the function at these
    discontinuities are finite.

Then the Fourier series converges to the function at all points except
at discontinuities. For the majority of practical problems, *this is a
perfectly reasonable assumption*.

### Fourier series with complex-valued coefficients

In the previous section, we discussed the Fourier series where the
coefficients were real variables. There, we observed that we had to
compute three sets of coefficients: one for $a_0$, one for $a_n$, and
lastly one for $b_n$. In special cases where the functions are odd or
even, either $a_n$ or $b_n$ is eliminated and results in 0. However, in
the general case, all three coefficients must be computed. Now, we shall
explore what happens if we calculate one set of coefficients, calling it
$c_n$, by multiplying the function by $e^{-ik\omega_0 t}$ and taking the
integral:

$$c_n = \frac{1}{2T} \int_{0}^{T}f(t) e^{-ik\omega_0t}dt$$

Specifically, we shall see how it relates to the real Fourier
coefficients computed earlier:

$$\begin{aligned}
c_n = \frac{1}{T} \int_{0}^{T}f(t) e^{-ik\omega_0t}dt = \frac{1}{T} \int_{0}^{T}f(t)(\cos{n\omega_0 t - i\sin{n\omega_0 t}})dt = \frac{a_n-ib_n}{2}
\end{aligned}$$

Moreover, it is now easy to see that for $c_{-n}$ is computed as:

$$\begin{aligned}
    c_{-n} = \frac{1}{T} \int_{0}^{T}f(t) e^{ik\omega_0t}dt = \frac{a_n+ib_n}{2}
\end{aligned}$$

And lastly:

$$\begin{aligned}
c_0 = \frac{a_0}{2}
\end{aligned}$$

Alternative, to compute $a_n$, $b_n$ and $a_0$ from $c_n$, the following
relations can be used:

$$\begin{aligned}
    a_0 &= c_0 \\
    a_n &= c_n + c_{-n} \quad\quad n > 0 \\
    b_n &= i(c_n - c_{-n})  \quad\quad n > 0
\end{aligned}$$

The consequence of computing $c_n$ instead of three individual sets of
coefficients for Fourier series, namely, $a_n$, $b_n$ and $a_0$ allows
us to get all three coefficients in *simultaneously*. We shall see that
in the example below.

**Example:** Compute the complex Fourier series for the periodic square
wave functions.

$$\begin{aligned}
    c_{n} &= \frac{1}{T} \int_{-T/2}^{T/2} f(t)e^{-ik\omega_0 t} \, dt 
    = \frac{1}{2} \int_{-0.5}^{0.5} e^{-ik\pi t} \, dt 
    = \frac{1}{2} \left[ \frac{e^{-ik\pi t}}{-ik\pi} \right]_{-0.5}^{0.5} \notag \\
    &= \frac{1}{-2ik\pi} \left( e^{-ik\pi/2} - e^{ik\pi/2} \right) 
    = \frac{1}{-2ik\pi} \left( -2i \sin\left(\frac{k\pi}{2}\right) \right) 
    = \frac{\sin\left(\frac{k\pi}{2}\right)}{k\pi} \quad k \neq 0
\end{aligned}$$

And moreover:

$$\begin{aligned}
c_0 = \frac{1}{2}
\end{aligned}$$

Therefore, the real Fourier coefficients can be computed from the
relations discussed earlier, which show the values we calculated
previously for the square wave function.

We have seen how the complex Fourier series coefficients are computed.
To complete the discussion of this form of Fourier series, we may now
investigate whether we can also rewrite the following formula:

$$f(t) = \frac{a_0}{2} + \sum_{1}^{\infty}(a_n\cos{k \omega_0 t} + 
b_n\sin{k \omega_0 t}
)$$

And replace not only the coefficients in terms of complex numbers, but
also all terms that are multiplied by the coefficients with complex
exponentials as well. This can be done by recognizing that the
trigonometric functions are related to complex exponentials via:

$$\begin{aligned}
\cos{x} = \frac{e^{ix} + e^{-ix}}{2} \quad,\quad
\sin{x} = \frac{e^{ix} - e^{-ix}}{2i}
\end{aligned}$$

Hence:

$$f(t) = \frac{a_0}{2} + \sum_{1}^{\infty}( \frac{a_n - ib_n}{2} \cos{k \omega_0 t} + 
\frac{a_n + ib_n}{2}\sin{k \omega_0 t}
)$$

Lastly:

$$f(t) = \sum_{-\infty}^{+\infty}c_n e^{-in\omega_0t}$$

This is the complex form of the Fourier transform where $c_n$ are
complex coefficients.

## Conclusion

This article presents an introduction to complex numbers as well as the
calculus involving complex-valued real variable functions. As discussed,
complex numbers and the exponential function provide convenient rules
for the evaluation of integrals for Fourier series in a compact way.
More advanced operations involving complex numbers, such as integration
and differentiation of complex-valued complex-variable functions, also
exist. The application of these types of calculus includes the Laplace
transform, which has found numerous applications in engineering. In the
subsequent article, these types of more advanced concepts involving
complex numbers are discussed.
