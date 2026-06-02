# Carbon Aware Static Voltage Stability Margin Test System

## Overview

This repository provides three modified IEEE 39 bus test cases for carbon aware static voltage stability margin (VSM) studies. The cases are used to examine how different source side generation mixes affect the carbon constrained VSM and the related sensitivity results.

The three cases keep the same network topology, load distribution, branch parameters, generator limits, and nodal carbon intensity (NCI) caps. They differ in the generator type composition and the corresponding carbon emission factors.

## Platform and Solver

- Platform: MATLAB
- Case format: MATPOWER
- Solver: IPOPT through CasADi

## Scenario Description

| Scenario | Case file | Description |
|---|---|---|
| S1 | `case39_high_base.m` | High carbon base case |
| S2 | `case39_g2_g8_to_gas.m` | Gas transition case |
| S3 | `case39_g2_g8_to_renewable.m` | Renewable transition case |

Scenario S1 is the high carbon base case. Scenario S2 replaces part of the coal fired generation with natural gas generation. Scenario S3 further increases the share of near zero emission renewable generation. These scenarios are designed to isolate the effect of source side carbon profiles on the carbon constrained VSM.

## Generator Carbon Emission Factors

| Type index | Generator type | Carbon emission factor (lb/kWh) |
|---:|---|---:|
| 1 | Coal fired | 2.26 |
| 2 | Natural gas | 0.97 |
| 3 | Wind power | 1e-6 |
| 4 | Solar power | 1e-6 |

Wind and solar units are treated as near zero emission sources.

## Carbon Data

Each case file contains carbon related data for the VSM model. The field `mpc.carbon` stores the baseline NCI cap of each bus, and `mpc.carbon_wg` stores the generator carbon emission factors when provided.

The same NCI caps are used in all three scenarios, so that the comparison focuses on the influence of generator type composition rather than changes in nodal carbon limits. The NCI caps are constructed from the unconstrained VSM solution and adjusted at selected load buses to activate carbon constraints.

## Load Setting

In the numerical studies, the active and reactive loads are scaled to 80% of the original IEEE 39 bus case. This load level is used consistently across all three scenarios.

## Usage

Add the case files to the MATLAB path and load a scenario using MATPOWER:

```matlab
mpc = loadcase('case39_high_base');
```

Other scenarios can be loaded by replacing the case name:

```matlab
mpc = loadcase('case39_g2_g8_to_gas');
mpc = loadcase('case39_g2_g8_to_renewable');
```

## Notes

- These cases are intended for carbon aware static VSM evaluation, sensitivity validation, and scenario comparison.
- The cases are modified from the IEEE 39 bus system in MATPOWER format.
- The provided carbon profiles are designed for comparative studies and do not represent a real power system carbon inventory.
- The term "renewable" refers to near zero emission generator modeling in this test system.
