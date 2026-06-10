---
title: "Large-Scale Fading"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
[[Small-Scale Fading]], created by the superposition of different MPCs, changes rapidly over the spatial scale of a few wavelengths. If the field strength is averaged over a small area (e.g., ten by ten wavelengths), we obtain the Small Scale Averaged (SSA) field strength. In the previous sections, we treated the SSA field strength as a constant.

However, as explained in the introduction, it varies when considered on **a larger spatial scale**, due to **shadowing** of the MPCs by IOs.

Many experimental investigations have shown that the SSA field strength $F$, plotted on a logarithmic scale, shows a [[Gaussian Distribution]] around a mean $\mu$. Such a distribution is known as lognormal, and its pdf is given by:
$$
pdf_{F}(F)=\frac{{\frac{20}{\ln(10)}}}{F\sigma_{F}\sqrt{ 2\pi }}\exp \left[ -{\frac{(20\log_{10}(F)-\mu_{{F,dB}})^2}{2\sigma_{F}^2}} \right] 
$$
where $\sigma_{F}$ is the standard deviation of F, and $\mu_{F,dB}$ is the mean of the values of F expressed in dB.

Also, power is distributed lognormally. However, there is an important fine point: when fitting the logarithm of SSA power to a normal distribution, we find that the median value of this distribution,$\mu_{P,dB}$, is related to the median of the field strength distribution $\mu_{F,dB}$ as $\mu_{P,dB}=\mu_{P,dB}+10\log_{10}\left( \frac{4}{\pi} \right)$ if the small-scale fading is Rayleigh. The pdf for the power thus reads
$$
pdf_{P}(P)=\frac{{\frac{10}{\ln(10)}}}{P\sigma_{P}\sqrt{ 2\pi }}\exp \left[ -{\frac{(10\log_{10}(P)-\mu_{{P,dB}})^2}{2\sigma_{P}^2}} \right] 
$$where $\sigma_{P}=\sigma_{F}$. Typical values of σF are $4-10dB$.
$$
P_{SSA}=\frac{1}{N+1}\sum_{x=i-\frac{N}{2}}^{i+\frac{N}{2}}|RxSignal_{amp}|^2
$$
$$
P|_{LSF, dB}=P_{SSA}-\bar{P}(d)
$$
Where $\bar{P}(d)$ is the pass loss $\bar{P(d)}=P(d_{0})-10n\log_{10}\left( \frac{d}{d_{9}} \right)$

The lognormal variations of $F$ have commonly been attributed to shadowing effects.
![[building-shadowing.png]]