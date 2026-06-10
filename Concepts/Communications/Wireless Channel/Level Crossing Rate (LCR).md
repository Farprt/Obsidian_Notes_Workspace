---
title: "Level Crossing Rate (LCR)"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
The Doppler spectrum is a complete characterization of the temporal statistics of fading. 

However, it is often desirable to have a different formulation that allows more direct insights into system behavior. A quantity that allows immediate interpretation is the occurrence rate of fading dips – this occurrence rate is known as the [[Level Crossing Rate (LCR)]].

Obviously, it depends on which level we are considering (i.e., how a fading dip is defined): falling below a level that is 30 dB below the mean happens more rarely than falling 3 dB below this mean. As the admissible depth of fading dips depends on the mean-field strength, as well as on the considered system, we want to derive the LCR for arbitrary levels (i.e., depth of fading dips).

Providing a mathematical formulation, the LCR is defined as the expected value of the rate at which the received field strength crosses a certain level r in the positive direction. This can also be written as:
$$
N_{R}(r)=\sqrt{ \frac{{\Omega_{2}}}{\pi\Omega_{0}}} \frac{{r}}{\sqrt{ 2\Omega_{0} }}e^{(-{r^2}/2\Omega_{0})}
$$
Note that $2\Omega_{0}$ is the root-mean-square value of amplitude.