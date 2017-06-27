---
layout: post
title:  "Notes: Basic Comparison of Emission Techniques for Defect Detection"
date:   2017-06-18
categories: devicenotes
tags: notes
---
<style type="text/css">
table{
    border-collapse: collapse;
    border-spacing: 10 px 20 px;
    border:1px solid #000000;
}

th{
    border:1px solid #000000;
}

td{
    border:1px solid #000000;
}
</style>

Identifying and eliminating process defects or design weak spots is an important aspect of semiconductor device / integrated circuit technology development. Emission techniques are very useful identifying the location of these defects or weak spots in the device, and guiding us towards underlying root cause for the failures. 

Emission Microscopy (EMMI) techniques broadly rely on detecting the light emitted by recombination of electron hole pairs. Hence, they are limited by various things such as the ability of equipment to detect the wavelength of light being emitted, whether the light being emitted is obstructed by other metal layers etc. 

The following table compares some of the emission techniques, their applicability and limitations. 

| Process | Principle | Defects Detected | Defects Not Detected | Comments |
| - | - | - | - | - |
| EMMI / InGaAs EMMI | Detection of light generated using Silicon or InGaAs CCD.  | Gate defects, Junction Leakage, Avalanche Leakage etc. | Resistive Metal Shorts, Defects that don't produce light.  | InGaAs EMMI is used for detecting lower energy emissions such as leakage currents |
| OBIRCH | A laser beam scan is used to generate heat in the IC, causing a resistance change locally. Defective regions behave differently from other regions.  | Resistive shorts, metal bridges etc.  | ? (TBD) |  |
| Thermal EMMI | Direct detection of thermal radiation emitted by the device during regular operation.  | Low resistance shorts (why ??) | ? (TBD) | Thermal EMMI is useful for non invasive FA, as the package does not need to be removed.  |

References:
1. [IST Website](http://www.istgroup.com/english/3_service/03_01_list.php?MID=43)