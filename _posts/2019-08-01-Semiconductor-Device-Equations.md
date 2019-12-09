---
layout: post
title:  "Semiconductor Equations Cheat Sheet"
date:   2019-09-11
categories: devicenotes
tags: notes
---

#### Some useful semiconductor device equations.

| Equation | Comments |
| $$ E = -\nabla V $$ <br> $$ V = \int_C E.dl $$ .. (for any arbitrary curve C)| Definition of Electric Field|
| $$ \nabla . E = \frac{\rho}{\epsilon} $$ <br> $$ \nabla^2V = -\frac{\rho}{\epsilon}$$  | Poisson's Equation |
| $$ \frac{d^2 V}{dx^2} = - \frac{dE}{dx} = -\frac{q}{\epsilon_{Si}}[p(x) - n(x) + N_d^+(x) - N_a^-(x)]$$| Poisson's Equation|
| $$ f_D(E) = \frac{1}{1+ e^{(E-E_C)/kT}} $$ | Fermi Dirac Distribution |
| $$ N_C = \sqrt{m_l m_t^2}\Big(\frac{8\pi m k T}{h^2}\Big)^{3/2}$$ = 2.9E19 $$cm^{-3}$$  at 300 K| Density of states in the conduction band | 
| $$ \frac{D}{\mu} = \frac{kT}{q} $$ | Einstein Relation, because drift and diffusion currents should balance each other |
| $$ L_D = \sqrt{\frac{\epsilon_{Si} k T}{q^2 N_d}} $$ | Debye Length: Distance required for the bands to respond to sudden change in concentration |
|$$J_n = q n \mu_n E+ q D_n \frac{dn}{dx} = -q n \mu_n \frac{d\phi_n}{dx}$$  <br> $$J_p = q p \mu_p E - q D_p \frac{dp}{dx}$$ |Current Density Equations|
| $$ V_{bi} = \frac{kT}{q} ln\Big(\frac{N_a N_d}{n_i^2}\Big) $$ | Built-in potential of a p-n junction | 
| $$ W_d = \sqrt{\frac{2\epsilon_{Si} V_{bi} (N_a+N_d) }{q N_a N_d}} $$ <br> $$ W_d = \sqrt{\frac{2\epsilon_{Si} kT (N_a+N_d) }{q^2 N_a N_d}ln\Big(\frac{N_a N_d}{n_i^2}\Big) } $$ | Depletion width in a p-n juntion | 
| $$ J_{b-b} = \infty exp(-E_g^{3/2})$$ | | 
| $$ I_{ds} = \mu_{eff} C_{ox} \frac{W}{L} (V_{gs} - V_{t}) V_{ds} \\ I_{ds} =  \mu_{eff} C_{ox} \frac{W}{L} \big((V_{gs} - V_{t}) V_{ds}) - m \frac{V_{ds}^2}{2}\big)$$ | MOSFET I-V|
| $$ V_{t} = V_{fb} + 2 \psi_{B} + \frac{\sqrt{2 \epsilon_{Si} q N_{a} (2*\psi_{B} - V_{bs})}}{C_{ox}} $$| Threshold Voltage Formula|	
{:.mbtablestyle}