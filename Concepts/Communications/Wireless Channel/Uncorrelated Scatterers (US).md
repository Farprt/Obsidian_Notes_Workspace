---
title: "Uncorrelated Scatterers (US)"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
The US assumption is defined as “contributions with different delays are uncorrelated,” which is written mathematically as:
$$
R_{h}(t,t',\tau,\tau')=P_{h}(t,t',\tau)\delta(\tau-\tau')
$$
For the transfer function, the US condition means that $R_{H}$ does not depend on the absolute frequency, but only on the frequency difference:
$$
R_{H}(t,t',f,f+\Delta f)=R_{H}(t,t',\Delta f)
$$
This implies that the frequency correlation function is independent of the carrier frequency, and only depends on the frequency difference $\Delta f$ between the two considered frequencies.

Again, it is obvious that this cannot hold for all frequencies – the correlation function at 100 MHz will be different from that at 100 GHz. We can thus define a stationarity bandwidth within which the US assumption is valid, while for larger changes in carrier frequency the assumption will not hold.