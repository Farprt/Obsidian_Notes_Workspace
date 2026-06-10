---
title: "Wide-Sense Stationary (WSS)"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
> [!NOTE] [[Wide-Sense Stationary (WSS)]]
> The mathematical definition of wide-sense stationarity is that the ACF depends not on the two variables $t$, $t'$ separately, but only on their difference $t-t'$ . Consequently, second-order amplitude statistics do not change with time.
   $$R_{h}(t,t',\tau,\tau')=R_{h}(t,t+\Delta t,\tau,\tau')=R_{h}(\Delta t,\tau,\tau')$$
   Physically speaking, WSS means that the statistical properties of the channel do not change with time.
   
This must not be confused with *a static channel*, where fading realizations do not change with time. For the simple case of a flat Rayleigh-fading channel, WSS means that the mean power and the ACF do not change with time, while the instantaneous amplitude can change.

In practice, this is not possible: as the UE moves over larger distances, the mean received power changes because of shadowing and variations in path loss. Rather, WSS is typically fulfilled over an area of about 10λ diameter (compare also Figure). We can thus define quasi-stationarity over a stationarity time, i.e., a finite time interval (associated with a movement distance of the UE) over which statistics do not change noticeably.
  ![[received-power-variation-types.png]]


WSS also implies that components with different Doppler shifts undergo uncorrelated fading. This can be shown by considering the Doppler-variant impulse response $s(\upsilon,t)$.
$$
R_{s}(\upsilon,\upsilon',\tau,\tau')=\hat{\hat{P_{s}}}(\upsilon,\tau,\tau')\delta(\upsilon-\upsilon')
$$
This implies that contributions undergo uncorrelated fading if they have different Doppler shifts.

Analogously, we can write RB as:
$$
R_{B}(\upsilon,\upsilon',f,f')=P_{B}(\upsilon,f,f')\delta(\upsilon-\upsilon)
$$