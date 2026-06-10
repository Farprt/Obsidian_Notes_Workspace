---
title: "Snell's Law"
type: concept
area: communications
subarea: wireless-channel
status: draft
---
![[reflection-and-transmission.png]]The angle of incidence is the same as the reflected angle:$\Theta_{r}=\Theta_{e}$
The angle of the transmitted wave is given by:
$$\frac{\sin\Theta_{\mathrm{t}}}{\sin\Theta_{\mathrm{e}}}=\frac{\sqrt{\delta_{1}}}{\sqrt{\delta_{2}}},$$
where subscripts 1 and 2 index the considered medium
The complex dielectric constant $\delta$: 
$$\delta=\varepsilon_0\delta_\mathrm{r}=\varepsilon-j\frac{\sigma_\mathrm{e}}{2\pi f_\mathrm{c}}.$$
dielectric constant $\varepsilon$: $\varepsilon=\varepsilon_{0}\varepsilon_{\mathrm{r}}$ (where $\varepsilon_{0}$ is the vacuum dielectric constant 8.854 × 10−12 Farad/m, and $\varepsilon_{\mathrm{r}}$ is the relative dielectric constant of the material)
conductivity $\sigma_{e}$

The reflection and transmission coefficients are different for TE and for TM waves. 
For TM polarization:
$$\rho_{\mathrm{TM}}=\frac{\sqrt{\delta_2}\cos\Theta_\mathrm{e}-\sqrt{\delta_1}\cos\left(\Theta_\mathrm{t}\right)}{\sqrt{\delta_2}\cos\Theta_\mathrm{e}+\sqrt{\delta_1}\cos\left(\Theta_\mathrm{t}\right)}$$$$T_{\mathrm{TM}}=\frac{2\sqrt{\delta_1}\cos\left(\Theta_\mathrm{e}\right)}{\sqrt{\delta_2}\cos\Theta_\mathrm{e}+\sqrt{\delta_1}\cos\left(\Theta_\mathrm{t}\right)}$$
 For TE polarization:
 $$\rho_{\mathrm{TE}}=\frac{\sqrt{\delta_1}\cos\left(\Theta_\mathrm{e}\right)-\sqrt{\delta_2}\cos\left(\Theta_\mathrm{t}\right)}{\sqrt{\delta_1}\cos\left(\Theta_\mathrm{e}\right)+\sqrt{\delta_2}\cos\left(\Theta_\mathrm{t}\right)}$$
 $$T_{\mathrm{TE}}=\frac{2\sqrt{\delta_1}\cos\left(\Theta_\mathrm{e}\right)}{\sqrt{\delta_1}\cos\left(\Theta_\mathrm{e}\right)+\sqrt{\delta_2}\cos\left(\Theta_\mathrm{t}\right)}$$
$$
\sqrt{ T^2+\rho^2 }=1
$$
Transmission through layered structures

Total transmission coefficient
$$
T=\frac{{T_{1}T_{2}e^{-j\alpha}}}{1+R_{1}R_{2}e^{-2j\alpha}}
$$
Total reflectrion coefficient
$$
\rho=\frac{{\rho_{1}\rho_{2}e^{-j2\alpha}}}{1+\rho_{1}\rho_{2}e^{-2j\alpha}}
$$
with the electrical length in the wall
$$
\alpha=\frac{{2\pi}}{\lambda}\sqrt{ \epsilon_{1} }d\cos(\Phi_{t})
$$
Wall with thickness d and two dielectrics
$$
T=\frac{E_{through}}{E_{i}}
$$
$$
\rho=\frac{E_{reflect}}{E_{i}}
$$