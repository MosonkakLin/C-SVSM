# Convex C-OPF Test System

## Platform
- MATLAB

## Solver
- IPOPT (Interior Point OPTimizer)

## Overview

This project implements three modified test systems for convex optimal power flow (C-OPF) studies. Each system includes four types of power generators characterized by different carbon emission factors.

## Generator Classification

| Index | Generator Type | Carbon Emission Factor (lbs/kWh) |
|------|--------------|----------------------------------|
| 1    | Coal-fired   | 2.26                             |
| 2    | Natural Gas  | 0.97                             |
| 3    | Wind Power   | 1e-6                             |
| 4    | Solar Power  | 1e-6                             |

## Notes
- Wind and solar are treated as near-zero emission sources.
- The test systems are designed for comparative studies of emission-aware OPF.
