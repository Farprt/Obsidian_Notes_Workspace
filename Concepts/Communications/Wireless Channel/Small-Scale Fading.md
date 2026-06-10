---
title: "Small-Scale Fading"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
1. The Time-Invariant Two-Path Model:
we consider the simplest possible case – two MPCs whose properties do not change with time.
If the runlength between TX and RX is $d$, the received signal can be described as:
$$
E(t)=E_{0}\cos(2\pi f_{c}t-k_{0}d)
$$
where $k_{0}$ is the wavenumber $\frac{2\pi}{\lambda}$, and $E_{0}$ is the amplitude at the RX. Using complex baseband notation($s_{BP}(t)=\mathrm{Re}\left\{ s_{LP}(t)e^{j2\pi f_{c}t} \right\}$)
$$
E=E_{0}e^{-jk_{0}d}
$$
Now consider the case that the transmit signal gets to the RX via two different propagation paths, created by two different Interacting Objects (IOs)
$$
E(\vec{r})=E_{1}e^{-j \vec{k_{1}}\vec{r}}+E_{2}e^{-j \vec{k_{2}}\vec{r}}
$$
where $\vec{k_{1}}$ is the wave vector (i.e., has the absolute magnitude $k_{0}$, and is pointing into the direction of propagation) of wave 1. Note that due to our assumptions, the location vector $\vec{r}$ impacts the phase, but not the amplitude, of each of the two MPCs.
2. The Time-Variant Two-Path Model
In general, the runtime (path length) difference between the different propagation paths changes with time. This change can be due to movements of the TX, the RX, the IOs, or any combination thereof; to simplify discussion, we henceforth assume only movement of the RX.

The movement of the RX also leads to a shift of the received frequency, called the Doppler shift. If the RX moves away from the TX with speed v, then the distance d between TX and RX increases with that speed.
$$
E(t)=E_{0}\cos(2\pi f_{c}t-k_{0}[d_{0}+vt])=E_{0}\cos\left( 2\pi t\left[ f_{c}-\frac{v}{\lambda}-k_{0}d_{0} \right] \right)
$$
the Doppler shift is given by:
$$
\upsilon =-\frac{v}{\lambda}\cos(\gamma)=-\frac{f_{c}v}{c_{0}}\cos(\gamma)
$$
Different MPCs have different Doppler shifts. This leads to a **Doppler spreading**, i.e., **frequency dispersion**.

The superposition of several Doppler-shifted waves creates the sequence of fading dips. Again, this can be demonstrated using the two-path model. As the RX moves, it receives two waves that are each Doppler shifted, but by different amounts.

Summarizing, we can obtain the fading rate in the two-path model by two equivalent considerations:
1. We superimpose two incident waves, plot the resulting interference pattern (field strength “mountains and valleys”), and count the number of fading dips per second that an RX sees when moving through that pattern.
2. Alternatively, we can think of superimposing two signals with different Doppler shifts at the receive antenna, and determine the fading rate from the beat frequency – i.e., the difference of the Doppler shifts of the two waves.
### 2.1.1 Small-Scale Fading Without a Dominant Component
we now investigate a more general case of multipath propagation. We consider a radio channel with many IOs and a moving RX.
![[rayleigh-fading-field-strength.png]]![[rayleigh-fading-amplitude-pdf.png]]
Properties of the [[Rayleigh Distribution]]
$$
\begin{align}
 & \text{Mean value} & \bar{r}=\sigma \sqrt{ \frac{\pi}{2} } \\
 & \text{Mean square value} & \bar{r^2}=r^2_{{rms}}=2\sigma^2 \\ \\
 & \text{Variance} & \bar{r^2}-(\bar{r}^2 )=2\sigma^2-\frac{\pi}{2}\sigma \\
 & \text{Median value} & r_{50}=1.18\sigma \\
 & \text{Variance} & \sigma^2
\end{align}
$$
$$
pdf(r)=\frac{1}{\sqrt{ 2\pi }\sigma}e^{(-r^2/2\sigma^2)}
$$
$$
cdf(r)=1-e^{(-r^2/2\sigma^2)}=1-e^{(P_{min}/\bar{P})}
$$
Fading Margin: $M=\frac{r_{rms}^2}{r_{min}^2}$

The task is therefore to answer the following question: “Given a minimum receive power required for successful communications, how large does the mean power have to be in order to ensure that communication fails in no more than $x\%$ of all situations?” 
In other words, how large does the fading margin have to be?

The cdf gives by definition the probability that a certain field strength level is not exceeded. In order to achieve an x% outage probability, it follows that:
$$
x=cdf(P_{min})\approx \frac{P_{min}}{\bar{P}}
$$
$$
\bar{P}=2\sigma^2
$$
### 2.1.2 Small-Scale Fading with a Dominant Component
Fading statistics change when a dominant MPC – e.g., a LOS component or a dominant specular component – is present.

![[small-scale-fading-dominant-component.png]]It is clear that the probability of deep fades is much smaller than in the Rayleigh-fading case. The stronger the LOS component, the rarer the occurrence of deep fades.

$$
pdf_{r}(r)=\frac{r}{\sigma^2}e^{[-{r^2+A^2}/2\sigma^2]}I_{0}\left( \frac{{rA}}{\sigma^2} \right)
$$
$$
cdf(r)=1-Q_{M}\left( \frac{A}{\sigma}, {\frac{r_{min}}{\sigma}} \right)
$$
$I_{0}(x)$ is the modified Bessel function of the first kind, zero order. $A$ is the amplitude of the dominant component.
$$
\bar{r^2}=2\sigma^2+A^2
$$
The ratio of the power in the LOS component $A$ to the power in the diffuse component $2\sigma^2$, $\frac{A^2}{2\sigma^2}$, is called the Rice factor $K_{r}$

For $K_{r}\to0$, the [[Rice Distribution]] becomes a Rayleigh distribution, while for large $K_{r}$ it approximates a Gaussian distribution with mean value $A$
![[rice-distribution-k-factor-comparison.png]]

## 2.1.3 [[Doppler Spectra]] and Statistics of Temporal Channel Variations
If the UE is moving, then different directions of the MPCs arriving at the UE give rise to different frequency shifts. This leads to a broadening of the received spectrum. The goal of this section is to derive this spectrum

the Doppler effect leads to a shift of the received frequency $f$ by the amount $\upsilon$, so that the received frequency is given by:
$$
f=f_{c}+\upsilon=f_{c}\left[ 1-\frac{v}{c_{0}}\cos(\gamma) \right]
$$
Obviously, the frequency shift depends on the direction of the wave, and must lie in the range $f_{c} − \upsilon_{max}\dots f_{c} + \upsilon_{max}$, where $\upsilon_{max}= f_{c}\frac{v}{c}$.

If there are multiple MPCs, we need to know the distribution of power of the incident waves as a function of $\gamma$.  As we are interested in the statistical distribution of the received signal, we consider the pdf of the received power.
we call it the pdf of the incident waves $pdf_{\gamma}(\gamma)$.  It describes the power density coming from the angular range $[\gamma,\gamma+d\gamma]$, which depends both on the density of MPCs (how many MPCs per unit angle) and the powers of those MPCs.

A very popular model for the angular spectrum at the UE is that the waves are incident uniformly from all azimuthal directions, and all arrive in the horizontal plane, so that:
$$
pdf_{\gamma}(\gamma)=\frac{1}{2\pi} \text{ for } -\pi<\gamma\leq \pi 
$$
This situation corresponds to the case when there is no LOS connection, and a large number of IOs are distributed uniformly around the UE.
Assuming furthermore that the antenna is a vertical short dipole, with an antenna pattern $G(\gamma) = 1.5$, the Doppler spectrum becomes
$$
S_{D}(\upsilon)={\frac{1.5\bar{\Omega}}{\pi \sqrt{ \upsilon_{max}^2-\upsilon^2 }}}
$$
![[jakes-doppler-spectrum.png]]
This spectrum, known as the classical or Jakes spectrum, is depicted in Figure 5.23. It has the characteristic “bathtub” shape