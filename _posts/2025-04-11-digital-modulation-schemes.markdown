---
layout: post
title:  "Part I: M-ary Digital Modulation Schemes"
date:   2025-04-11 14:41:00 +0100
categories: wireless communication
---
By definition, in an $$M$$-ary digital modulation scheme, we send any one of $$M$$ possible signals, $$s_1(t),s_2(t),\cdots,s_M(t)$$ during each signalling (symbol) interval of duration $$T$$. In almost all applications, $$M = 2^m$$, where $$m$$ is a positive integer which represent the number of bits per symbol. Thus, the symbol duration becomes $$T = m\cdot T_b$$, where $$T_b$$ is the bit duration.

The $$M$$-ary modulation schemes preferred over binary modulation schemes for transmitting digital data over bandpass channels when the requirement is to conserve bandwidth *at the expense of both increased power and increased system complexity*.

### Bandwidth Conservation Capability of M-ary Modulation Schemes
Let's consider the transmission of information consisting of a binary sequence with a bit duration $$T_b$$.
- If we were to transmit information using binary phase shift keying (BPSK), the required channel bandwidth becomes proportional with $$1/T_b$$.

- If we take blocks of $$m$$ bits to produce a symbol e.g. $$M$$-PSK with $$M=2^m$$ and symbol duration $$T = m\cdot T_b$$, then required channel bandwidth becomes proportional with $$1/(m\cdot T_b)$$, which shows that the $$M$$-PSK reduces the required channel bandwidth by the factor of $$m = \log_2(M)$$ over BPSK.

### Mapping of Digitally Modulated Waveforms Onto Constellations of Signal Points
Let's start with $$M$$-ary PSK due to it's simplicity, the available phase $$2\pi$$ radians are portioned equally and a discrete way among $$M$$ transmitted signals as follows:

$$s_i(t) = \sqrt{\frac{2E}{T}}\cos(2\pi f_c t + \frac{2\pi}{M}i)$$

where $$i=0,1,\cdots,M-1$$ and $$ 0 \leq t \leq T $$. The parameters $$E$$ is the signal energy per symbol and $$f_c$$ is the carrier frequency.

The idea of signal-space diagrams has a profound importance in statistical information theory since it provides mathematical basis for the *geometrical representation of energy signals*, exemplified by digitally modulated waveforms. For a specific method of digital modulation, the geometric representation is pictured in the form of a constellation points in the signal space diagram, which is unique to that method. For instance, BPSK show the way in which two waveforms $$s_1(t)$$ and $$s_2(t)$$ representing the binary symbols $$1$$ and $$0$$ respectively, are mapped onto the *transmitted signal points* as follows:

$$\begin{aligned} s_1(t) &= \sqrt{\frac{2E_b}{T_b}}\cos(2\pi f_c t), \quad \text{symbol 1} \\
                s_2(t) &= \sqrt{\frac{2E_b}{T_b}}\cos(2\pi f_c t + \pi), \quad \text{symbol 0} \end{aligned}$$

<div style="text-align: center;">
    <img src="/blog/assets/images/BPSK_waves.png" alt="BPSK waveforms" style="width: 100%;">
</div>

#### How is the mapping accomplished?
The answer lies within the concept of *the correlator*. The definition of the modulated waves for the BPSK modulation is given above. Similarly, the signal-space representation of the BPSK modulation involves a single basis function,

$$\phi_1(t) \sqrt{\frac{2}{T_b}}\cos(2\pi f_c t)$$

More specifically, two signalling waveforms $$s_1(t)$$ and $$s_2(t)$$ are correlated with the basis function $$\phi_1(t)$$, over the time interval $$0\leq t \leq T_b$$

- We get the point $$\mathbf{s}_1$$ by using, $$\mathbf{s}_1 = \int_{0}^{T_b}\phi_1(t)s_1(t)\text{d}t$$.

- Similarly, we can get the point $$\mathbf{s}_2$$, $$\mathbf{s}_2 = \int_{0}^{T_b}\phi_1(t)s_2(t)\text{d}t$$.

1.Let's calculate the integral $$\mathbf{s}_1 = \int_{0}^{T_b}\phi_1(t)s_1(t)\text{d}t$$,

$$\begin{aligned} \mathbf{s}_1 &= \int_{0}^{T_b} \left( \sqrt{\frac{2}{T_b}}\cos(2\pi f_c t) \right) \left( \sqrt\frac{2E_b}{T_b}\cos(2\pi f_c t) \right) \text{d}t \\ 
                                &= \int_{0}^{T_b}\frac{2\sqrt{E_b}}{T_b}\cos^2(2\pi f_c t) \end{aligned}$$

If we use the well known trigonometric expression:

$$\cos^2(\theta) = \frac{1 + \cos(2\theta)}{2}$$

The above integral could be evaluated as follows:

$$\begin{aligned} \int_{0}^{T_b}\frac{2\sqrt{E_b}}{T_b}\cos^2(2\pi f_c t) &=  \int_{0}^{T_b}\frac{2\sqrt{E_b}}{T_b}\left( \frac{1 + \cos(4\pi f_c t)}{2} \right)\text{d}t \\
                    &= \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b} \text{d}t + \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b}\cos(4\pi f_c t) \text{d}t\end{aligned}$$

Since $$\int_{0}^{T_b}\cos(4\pi f_c t) \text{d}t = 0$$, which is equvalent to find the area under the coside curve for a full period, we know that it is zero as cosine function could be represented as two odd function between 0 and 0.5 and 0.5 to 1 (please refer to the figure above).

Therefore,

$$\mathbf{s}_1 = \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b} \text{d}t = \frac{\sqrt{E_b}}{T_b}\cdot T_b = \sqrt{E_b}.$$

Similarly, we can show the same thing for the point $$\mathbf{s}_2$$ as follows:

$$\begin{aligned} \mathbf{s}_2 &= \left( \sqrt{\frac{2}{T_b}}\cos(2\pi f_c t) \right) \left( \sqrt{\frac{2E_b}{T_b}}\cos(2\pi f_c t + \pi) \right)\text{d}t \\ 
                                &= \int_{0}^{T_b} \frac{2\sqrt{E_b}}{T_b}\cos(2\pi f_c t) \cos(2\pi f_c t + \pi) \text{d}t \end{aligned}$$

Another well known trigonometric expression is a follows:

$$\begin{aligned} \cos(\theta + \gamma) &= \cos(\theta) \cos(\gamma) - \sin(\theta)\sin(\gamma) \\
                    \cos(\theta - \gamma) &= \cos(\theta) \cos(\gamma) + \sin(\theta)\sin(\gamma) \end{aligned}$$.

Consequently,

$$ \cos(\theta)\cos(\gamma) = \frac{\cos(\theta+\gamma)+\cos(\theta-\gamma)}{2} $$

We can use the above expression to evaluate the integral,

$$\begin{aligned} \mathbf{s}_2 = \int_{0}^{T_b} \frac{2\sqrt{E_b}}{T_b}\cos(2\pi f_c t) \cos(2\pi f_c t + \pi) \text{d}t  &= \int_{0}^{T_b} \frac{2\sqrt{E_b}}{T_b} \left( \frac{\cos(4\pi f_c t + \pi) + \cos(-\pi)}{2}\right) \text{d}t \\
&= \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b}\cos(4\pi f_c t + \pi) \text{d}t - \frac{\sqrt{E_b}}{T_b}\int_{0}^{T_b} \text{d}t \\
&= -\sqrt{E_b} \end{aligned}$$

Note from above expression that the area under a cosine function is phase shift invariant since the integral is taken for the whole period of the curve. The points $$\mathbf{s}_1$$ and $$\mathbf{s}_2$$ therefore could be represented in a simple plot like that,

<div style="text-align: center;">
    <img src="/blog/assets/images/BPSK_points.png" alt="BPSK points" style="width: 40%;">
</div>

# References
[1] An Introduction to Digital and Analog Communications, Simon Haykin, 2nd Edition, 2001.

[2] Wireless Communications, Andrea Goldsmith, 2005.