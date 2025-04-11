---
layout: post
title:  "Part I: M-ary Digital Modulation Schemes"
date:   2025-04-11 14:41:00 +0100
categories: wireless communication
---

In an $$M$$-ary digital modulation scheme, one of $$M$$ possible signals, $$s_1(t), s_2(t), \ldots, s_M(t)$$, is transmitted during each symbol interval of duration $$T$$. Typically, $$M = 2^m$$, where $$m$$ is a positive integer representing the number of bits per symbol. Thus, the symbol duration is $$T = m \cdot T_b$$, where $$T_b$$ is the bit duration.

$$M$$-ary modulation schemes are preferred over binary schemes for digital data transmission over bandpass channels when bandwidth conservation is prioritized, even at the cost of increased power and system complexity.

### Bandwidth Conservation of M-ary Modulation Schemes

Consider transmitting a binary sequence with a bit duration of $$T_b$$.

- Using binary phase shift keying (BPSK), the required channel bandwidth is proportional to $$1/T_b$$.
  
- By grouping $$m$$ bits to form a symbol, such as with $$M$$-PSK where $$M=2^m$$, and using a symbol duration $$T = m \cdot T_b$$, the required channel bandwidth becomes proportional to $$1/(m \cdot T_b)$$. This means that $$M$$-PSK reduces the needed bandwidth by a factor of $$m = \log_2(M)$$ compared to BPSK.

### Mapping Digitally Modulated Waveforms onto Signal Constellations

Consider $$M$$-ary PSK for its simplicity. The available phase range of $$2\pi$$ radians is divided equally among $$M$$ signals:

$$s_i(t) = \sqrt{\frac{2E}{T}}\cos(2\pi f_c t + \frac{2\pi}{M}i)$$

where $$i=0, 1, \ldots, M-1$$ and $$0 \leq t \leq T$$. Here, $$E$$ is the signal energy per symbol, and $$f_c$$ is the carrier frequency.

Signal-space diagrams are crucial in statistical information theory as they provide a mathematical basis for the geometric representation of energy signals, exemplified by digitally modulated waveforms. For a particular modulation method, the geometric representation appears as a constellation of points unique to that method. For instance, in BPSK, two waveforms $$s_1(t)$$ and $$s_2(t)$$ representing binary symbols $$1$$ and $$0$$, respectively, are mapped onto transmitted signal points as follows:

$$\begin{aligned} 
s_1(t) &= \sqrt{\frac{2E_b}{T_b}}\cos(2\pi f_c t), \quad \text{symbol 1} \\
s_2(t) &= \sqrt{\frac{2E_b}{T_b}}\cos(2\pi f_c t + \pi), \quad \text{symbol 0} 
\end{aligned}$$

<div style="text-align: center;">
    <img src="/blog/assets/images/BPSK_waves.png" alt="BPSK waveforms" style="width: 100%;">
</div>

#### How is the Mapping Achieved?

The mapping is accomplished through the concept of *the correlator*. The BPSK modulation's signal-space representation involves a single basis function:

$$\phi_1(t) = \sqrt{\frac{2}{T_b}}\cos(2\pi f_c t)$$

Two signaling waveforms $$s_1(t)$$ and $$s_2(t)$$ are correlated with this basis function over the interval $$0 \leq t \leq T_b$$.

- The point $$\mathbf{s}_1$$ is obtained using $$\mathbf{s}_1 = \int_{0}^{T_b}\phi_1(t)s_1(t)\text{d}t$$.

- Similarly, the point $$\mathbf{s}_2$$ is found as $$\mathbf{s}_2 = \int_{0}^{T_b}\phi_1(t)s_2(t)\text{d}t$$.

1) Calculate the integral $$\mathbf{s}_1 = \int_{0}^{T_b}\phi_1(t)s_1(t)\text{d}t$$:

$$\begin{aligned} 
\mathbf{s}_1 &= \int_{0}^{T_b} \left( \sqrt{\frac{2}{T_b}}\cos(2\pi f_c t) \right) \left( \sqrt{\frac{2E_b}{T_b}}\cos(2\pi f_c t) \right) \text{d}t \\ 
&= \int_{0}^{T_b}\frac{2\sqrt{E_b}}{T_b}\cos^2(2\pi f_c t) \text{d}t 
\end{aligned}$$

Using the trigonometric identity:

$$\cos^2(\theta) = \frac{1 + \cos(2\theta)}{2}$$

The integral evaluates to:

$$\begin{aligned} 
\int_{0}^{T_b}\frac{2\sqrt{E_b}}{T_b}\cos^2(2\pi f_c t) &= \int_{0}^{T_b}\frac{2\sqrt{E_b}}{T_b}\left( \frac{1 + \cos(4\pi f_c t)}{2} \right)\text{d}t \\
&= \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b} \text{d}t + \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b}\cos(4\pi f_c t) \text{d}t
\end{aligned}$$

Since $$\int_{0}^{T_b}\cos(4\pi f_c t) \text{d}t = 0$$, the integral simplifies to:

$$\mathbf{s}_1 = \frac{\sqrt{E_b}}{T_b}\cdot T_b = \sqrt{E_b}$$

2) Similarly, for the point $$\mathbf{s}_2$$:

$$\begin{aligned} 
\mathbf{s}_2 &= \int_{0}^{T_b} \frac{2\sqrt{E_b}}{T_b}\cos(2\pi f_c t) \cos(2\pi f_c t + \pi) \text{d}t 
\end{aligned}$$

Using the identity:

$$\cos(\theta)\cos(\gamma) = \frac{\cos(\theta+\gamma)+\cos(\theta-\gamma)}{2}$$

The integral becomes:

$$\begin{aligned} 
\mathbf{s}_2 &= \int_{0}^{T_b} \frac{2\sqrt{E_b}}{T_b} \left( \frac{\cos(4\pi f_c t + \pi) + \cos(-\pi)}{2}\right) \text{d}t \\
&= \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b}\cos(4\pi f_c t + \pi) \text{d}t - \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b} \text{d}t
\end{aligned}$$

Note from the above expression that the area under a cosine function is phase shift invariant since the integral is taken for the whole period of the curve. 

The points $$\mathbf{s}_1$$ and $$\mathbf{s}_2$$ therefore could be represented in a simple plot as follows,

<div style="text-align: center;">
    <img src="/blog/assets/images/BPSK_points.png" alt="BPSK points" style="width: 40%;">
</div>

# References
[1] An Introduction to Digital and Analog Communications, Simon Haykin, 2nd Edition, 2001.

[2] Wireless Communications, Andrea Goldsmith, 2005.