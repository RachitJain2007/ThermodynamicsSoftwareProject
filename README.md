# ThermoCubic EOS Studio

> **Interactive Real Gas PVT Behavior, Pure-Component Fugacity, and Thermodynamic Departure (H & S) Calculation Engine**

## Quick Links

* **Live Web Application:** https://sites.google.com/view/thermostudio/
* **Source Code Repository:** https://github.com/RachitJain2007/ThermodynamicsSoftwareProject/

---

## Project Overview

ThermoCubic EOS Studio is a browser-based computational tool for predicting the PVT behavior of real gases, determining pure-component fugacity ($f, \phi$), and computing enthalpy ($H$) and entropy ($S$) departure properties using cubic equations of state. Powered by an analytical Cardano cubic solver, it delivers real-time phase identification, stable root selection, and interactive thermodynamic isotherms with zero installations or dependencies.

---

## Key Features

* **4 Standard Cubic Equations of State (EOS):**
  * **Peng-Robinson (PR, 1976)**: Industry standard for natural gas and vapor-liquid equilibria.
  * **Soave-Redlich-Kwong (SRK, 1972)**: Widely used in gas processing and hydrocarbon applications.
  * **Redlich-Kwong (RK, 1949)**: Classic two-parameter model with temperature-dependent attraction.
  * **Van der Waals (vdW, 1873)**: Fundamental model accounting for molecular volume and intermolecular attraction.

* **Pure-Component Fugacity & Phase Identification:**
  * Calculates analytical fugacity coefficient $\phi = \exp(\ln \phi)$ and fugacity $f = \phi \cdot P$.
  * Automatically identifies Vapor, Liquid, or Supercritical states.
  * Resolves subcritical 2-phase regimes using minimum Gibbs energy ($\min f_i$) and enables direct inspection of the mechanically unstable middle spinodal root.

* **Thermodynamic Departure Functions (Enthalpy H & Entropy S):**
  * Evaluates residual enthalpy ($H^R$) and residual entropy ($S^R$) departure functions.
  * Computes ideal gas sensible changes ($\Delta H^{\text{ig}}, \Delta S^{\text{ig}}$) using 4-parameter polynomial heat capacity models ($C_p(T) = A + B T + C T^2 + D T^3$) relative to a customizable reference state ($T_{\text{ref}}, P_{\text{ref}}$).
  * Synthesizes total thermodynamic state properties:
    $$H(T, P) = \Delta H^{\text{ig}}(T_{\text{ref}} \to T) + H^R(T, P)$$
    $$S(T, P) = \Delta S^{\text{ig}}(T_{\text{ref}}, P_{\text{ref}} \to T, P) + S^R(T, P)$$

* **Built-in Pure Fluid Database:**
  * Calibrated critical parameters and $C_p(T)$ coefficients for:
    * Methane ($\text{CH}_4$), Ethane ($\text{C}_2\text{H}_6$), Propane ($\text{C}_3\text{H}_8$), n-Butane ($\text{C}_4\text{H}_{10}$)
    * Carbon Dioxide ($\text{CO}_2$), Nitrogen ($\text{N}_2$), Oxygen ($\text{O}_2$), Hydrogen ($\text{H}_2$)
    * Water ($\text{H}_2\text{O}$), Ammonia ($\text{NH}_3$), Hydrogen Sulfide ($\text{H}_2\text{S}$)
    * Custom user-defined fluid mode.

* **Essential Thermodynamic Plots:**
  * **Compressibility Factor Isotherm ($Z \text{ vs. } P$)**: Shows real gas deviations from ideal behavior ($Z = 1$) with interactive inspection and click-to-set pressure.
  * **Pressure–Volume Isotherm ($P \text{ vs. } V$)**: Visualizes cubic isotherm loops on a logarithmic molar volume scale.

* **Unit Basis Switching:** Instant toggle between Molar Basis ($\text{mol}$) and Specific Mass Basis ($\text{kg}$).

---

## Theoretical Background

The general cubic equation of state is expressed as:

$$P = \frac{RT}{v - b} - \frac{a(T)}{(v + \delta_1 b)(v + \delta_2 b)}$$

Expressed in terms of the compressibility factor $Z = \frac{Pv}{RT}$:

$$Z^3 + c_2 Z^2 + c_1 Z + c_0 = 0$$

Where dimensionless parameters $A$ and $B$ are defined by:

$$A = \frac{a(T) P}{(RT)^2}, \quad B = \frac{b P}{RT}$$

### Fugacity Coefficient ($\phi$)

From classical thermodynamics:

$$\ln \phi = \int_0^P \left( \frac{Z - 1}{P} \right) dP$$

Integrating analytically yields:

$$\ln \phi = (Z - 1) - \ln(Z - B) - \frac{A}{(\delta_1 - \delta_2) B} \ln \left[ \frac{Z + \delta_1 B}{Z + \delta_2 B} \right]$$

---

## How to Run the Application

This software is packaged as a standalone, single-file application (`index.html`) requiring no compilers, build pipelines, or server configurations.

### Option 1: Live in Browser

Access the hosted web app directly:
* **Link:** https://sites.google.com/view/thermostudio/

### Option 2: Running Locally (Offline)

1. **Clone the repository:**
   
```bash
   git clone [https://github.com/RachitJain2007/ThermodynamicsSoftwareProject.git](https://github.com/RachitJain2007/ThermodynamicsSoftwareProject.git)
   cd ThermodynamicsSoftwareProject
