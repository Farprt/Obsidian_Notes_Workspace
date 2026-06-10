---
title: "The $d^4$ Power Law"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
This law is often justified by computing the received power for the case that only a direct (LOS) wave, plus a ground-reflected wave, exists.
![[d4-power-law.png]]
The power behaves as $P_{RX}(d)\approx P_{TX}G_{TX}G_{RX}\left( \frac{h_{TX}h_{RX}}{d^2} \right)^2$
For distance greater than $d_{break}\geq \frac{4h_{TX}h_{RX}}{\lambda}$

For distances $d<d_{break}$, [[Friis' Law]] remains approximately valid, though significant variations occur even for small changes of $d$, due to the constructive or destructive interference of the two waves.
![[two-ray-ground-reflection-path-loss.png]]

$P_{\mathrm{RX|dBm}}(d)=P_{\mathrm{RX|dBm}}(1\mathrm{m})-20\log{(d_{\mathrm{break}}|_{\mathrm{m}})}-\alpha_\mathrm{LBP}{10}\log{(d/d_{\mathrm{break}})}.$
However, 
- $\alpha_\mathrm{LBP}=4$ is not a universal decay exponent, values between $1.5<\alpha_{LBP}<5.5$
- Theoretical model is not fulfilled in practice  
- Breakpoint is rarely where theoretically predicted  
- Second breakpoint at the radio horizon