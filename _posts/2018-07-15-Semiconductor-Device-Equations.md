---
layout: post
title:  "Semiconductor Equations Cheat Sheet"
date:   2018-01-11
categories: devicenotes
tags: notes
---

#### Some useful semiconductor device equations.

| Equation | Comments |
| $$ f_D(E) = \frac{1}{1+ e^{(E-E_C)/kT}} $$ | Fermi Dirac Distribution |
| $$ N_C = \sqrt{m_l m_t^2}\Big(\frac{8\pi m k T}{h^2}\Big)^{3/2} $$ | Density of states in the conduction band | 
| $$ \frac{D}{\mu} = \frac{kT}{q} $$ | Einstein Relation, because drift and diffusion currents should balance each other |
| $$ \frac{d^2 \psi}{dx^2} = - \frac{dE}{dx} = -\frac{q}{\epsilon_{Si}}[p(x) - n(x) + N_d^+(x) - N_a^-(x)]$$| Poisson's Equation|
| $$ L_D = \sqrt{\frac{\epsilon_{Si} k T}{q^2 N_d}} $$ | Debye Length: Distance required for the bands to respond to sudden change in concentration |
| $$ V_{bi} = \frac{kT}{q} ln\Big(\frac{N_a N_d}{n_i^2}\Big) $$ | Built-in potential of a p-n junction | 
| $$ W_d = \sqrt{\frac{2\epsilon_{Si} V_{bi} (N_a+N_d) }{q N_a N_d}} $$ | Depletion width in a p-n juntion | 
| $$ J_{b-b} = \infty exp(-E_g^{3/2})$$ | | 
| $$ I_{ds} = \mu_{eff} C_{ox} \frac{W}{L} (V_{gs} - V_{t}) V_{ds}$$ | MOSFET I-V in Linear Region|
| $$ V_{t} = V_{fb} + 2 \psi_{B} + \frac{\sqrt{4\epsilon_{Si} q N_{a} \psi_{B}}}{C_{ox}} $$| Threshold Voltage Formula|	
{:.mbtablestyle}