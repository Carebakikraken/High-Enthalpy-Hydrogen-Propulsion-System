# High Enthalpy Hydrogen Propulsion System

<p align="center">
Finite Element Analysis (FEA), CFD validation, thermal investigation, fatigue assessment, and analytical propulsion modelling using ANSYS Fluent, ANSYS Mechanical, and MATLAB.
</p>

<p align="center">
CFD Analysis • Hydrogen Propulsion • Thermal Simulation • Fatigue Investigation • Aerospace Engineering
</p>

---

# Overview

This project presents a simulation-driven investigation of a high-enthalpy hydrogen propulsion system designed for advanced aerospace propulsion applications.

The work combines:

- CFD validation
- thermal contour analysis
- structural stress investigation
- fatigue performance assessment
- analytical propulsion calculations
- mesh independence validation
- MATLAB propulsion modelling

The objective was to evaluate propulsion system performance under extreme thermal and structural operating conditions while validating engineering feasibility through simulation-driven workflows.

---

# Technical Details

## Software Used

- ANSYS Fluent
- ANSYS Mechanical
- SolidWorks
- MATLAB

---

## Engineering Methodology

- CFD simulation workflow
- compressible flow analysis
- thermal distribution validation
- structural deformation assessment
- equivalent stress analysis
- fatigue life investigation
- propulsion parameter optimisation

---

# Simulation Workflow & Results

---

## 1. Initial Blade Geometry

<p align="center">
<img src="Image/1.png" width="450"/>
</p>

<p align="center">
<em>Initial propulsion geometry used for CFD and thermal investigation workflow.</em>
</p>

---

## 2. Mesh Generation Study

<p align="center">
<img src="Image/2.png" width="450"/>
</p>

<p align="center">
<em>Finite element mesh generated for CFD validation and numerical convergence investigation.</em>
</p>

---

## 3. Comparative Engineering Results

<p align="center">
<img src="Image/3.png" width="650"/>
</p>

<p align="center">
<em>Comparison of deformation and stress behaviour under multiple loading conditions.</em>
</p>

---

## 4. Structural Deformation Investigation

<p align="center">
<img src="Image/4.png" width="450"/>
</p>

<p align="center">
<em>Total deformation contour illustrating displacement behaviour under operational thermal loading.</em>
</p>

---

## 5. Equivalent Stress Analysis

<p align="center">
<img src="Image/5.png" width="450"/>
</p>

<p align="center">
<em>Von-Mises equivalent stress distribution used for structural integrity validation.</em>
</p>

---

## 6. Thermal Distribution Investigation

<p align="center">
<img src="Image/6.png" width="450"/>
</p>

<p align="center">
<em>Thermal contour illustrating temperature distribution throughout propulsion geometry.</em>
</p>

---

## 7. Maximum Principal Stress Study

<p align="center">
<img src="Image/7.png" width="450"/>
</p>

<p align="center">
<em>Maximum principal stress contour highlighting critical stress concentration regions.</em>
</p>

---

## 8. Modal Frequency Analysis

<p align="center">
<img src="Image/8.png" width="700"/>
</p>

<p align="center">
<em>Modal analysis performed to investigate vibration behaviour and resonance characteristics.</em>
</p>

---

## 9. Temperature Field Validation

<p align="center">
<img src="Image/9.png" width="500"/>
</p>

<p align="center">
<em>Temperature field simulation demonstrating thermal loading behaviour during propulsion operation.</em>
</p>

---

# MATLAB Propulsion Modelling

The propulsion system analytical calculations were validated using MATLAB numerical modelling.

```matlab
clc;
clear;

%% 1. Input Parameters
Pc = 40e6;           % Chamber Pressure (Pa)
Tc = 5000;           % Chamber Temperature (K)
Pa = 101325;         % Ambient Pressure (Pa)
R  = 4124;           % Gas Constant for H2 (J/kg*K)
gamma = 1.3;         % Heat Capacity Ratio
Rt = 0.1;            % Throat Radius (m)
epsilon = 20.25;     % Expansion Ratio (Ae/At)
total_mass = 140000; % Total Rocket Mass (kg)
g = 9.81;            % Gravity (m/s^2)

%% 2. Geometric Calculations
At = pi * Rt^2;
Ae = epsilon * At;

%% 3. Throat Conditions
Tt = Tc * (2 / (gamma + 1));
Vt = sqrt(gamma * R * Tt);

%% 4. Mass Flow Rate
term1 = (At * Pc) / sqrt(Tc);
term2 = sqrt(gamma/R * (2/(gamma+1))^((gamma+1)/(gamma-1)));
mdot = term1 * term2;

%% 5. Exit Mach Number
area_mach_eq = @(M) (1./M) .* ((2/(gamma+1)) .* ...
    (1 + (gamma-1)/2 .* M.^2)).^((gamma+1)/(2*(gamma-1))) - epsilon;

Me = fzero(area_mach_eq, 4);

%% 6. Exit Conditions
Te = Tc / (1 + (gamma-1)/2 * Me^2);
Ve = Me * sqrt(gamma * R * Te);

%% 7. Exit Pressure
Pe = Pc * (1 + (gamma-1)/2 * Me^2)^(-gamma/(gamma-1));

%% 8. Thrust Calculations
Momentum_Thrust = mdot * Ve;
Pressure_Thrust = (Pe - Pa) * Ae;

Total_Thrust = Momentum_Thrust + Pressure_Thrust;

%% 9. Thrust-to-Weight Ratio
TWR = Total_Thrust / (total_mass * g);

%% 10. Mission Status
if TWR < 1
    status = 'Insufficient thrust for liftoff';
elseif TWR < 1.2
    status = 'Marginal liftoff';
else
    status = 'Sufficient thrust for liftoff';
end

%% 11. Display Results
fprintf('--- Hydrogen Propulsion Performance Report ---\n');
fprintf('Mass Flow Rate: %.2f kg/s\n', mdot);
fprintf('Exit Mach Number: %.3f\n', Me);
fprintf('Exit Velocity: %.2f m/s\n', Ve);
fprintf('Total Thrust: %.2f MN\n', Total_Thrust/1e6);
fprintf('TWR: %.2f\n', TWR);
fprintf('Mission Status: %s\n', status);
```

---

# Engineering Comparison Study

| Category | Final Model | Chemical Rocket | Nuclear Thermal Rocket |
|---|---|---|---|
| Propellant | Hydrogen (H₂) | RP-1 / LH2 + LOX | U235 |
| Chamber Temperature | 5000 K | 3000–3500 K | 2500–3000 K |
| Chamber Pressure | 40 MPa | 10–25 MPa | 3–10 MPa |
| Exit Velocity | ~11,400 m/s | 3,000–4,500 m/s | 8,000–9,000 m/s |
| Specific Impulse | ~1100s | 300–450s | 800–900s |
| CFD Validation | ✅ | ❌ | ❌ |
| Structural Testing | ✅ | ❌ | ❌ |

---

# Results & Findings

The investigation demonstrated the effectiveness of simulation-driven propulsion engineering workflows for evaluating high-temperature hydrogen propulsion systems.

## Key Findings

- improved thermal loading understanding
- validated CFD flow behaviour
- structural integrity assessment completed
- fatigue reliability investigated
- mesh independence verified
- propulsion performance analytically validated
- high specific impulse potential demonstrated

The combined CFD, structural, thermal, and analytical workflow provides a strong engineering foundation for future propulsion system optimisation studies.

---

# Future Improvements

Potential future developments include:

- plasma-assisted propulsion modelling
- regenerative cooling simulation
- transient combustion modelling
- AI-assisted geometry optimisation
- advanced fatigue lifecycle investigation
- coupled thermo-structural simulation

---

# Repository Structure

```bash
├── Appendix
├── CFD-Results
├── Fatigue-Analysis
├── Image
├── MATLAB
├── Reports
└── README.md
```

Because apparently humans enjoy organising folders almost as much as they enjoy overheating aerospace hardware to several thousand Kelvin and calling it innovation.

---

# Appendix

Additional engineering calculations, fatigue investigations, mesh studies, and propulsion validation data are included within the appendix documentation.

📄 Appendix File:  
`Appendix/Individual Project Appendix 1.docx`

Source document uploaded in conversation: :contentReference[oaicite:0]{index=0}

---

# Author

Varun Saini  
Aerospace Engineering Graduate  
Preston, United Kingdom

---
