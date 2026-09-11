<div align="center">

# 🤖 PARMA

**An Inference-Time, Pose-Aware Safety Layer for Vision-Language-Action Policies**

*Code is coming soon.*

</div>

## Overview

PARMA is an inference-time, pose-aware safety layer for vision-language-action
(VLA) robot policies. It receives nominal action chunks from a policy server,
constructs local geometric safety constraints, filters the selected action,
and executes the result in a LIBERO-compatible simulator.

The framework connects policy prediction with geometric action correction.
A frozen VLA policy proposes actions, while PARMA uses local scene geometry
and pose-aware constraints to adjust the selected action before execution.

<p align="center">
  <img src="Pictures/fig1.png" alt="PARMA framework: a frozen VLA policy produces nominal action chunks, which pass through scene modeling, proxy-point constraints, QP filtering, and adaptive execution." width="100%">
</p>

*Figure 1. Overview of PARMA, from nominal VLA actions to pose-aware geometric
constraints, risk-adaptive correction, and execution.*

## Method Highlights

- **Pose-aware geometry.** Local proxy points represent the gripper's spatial
  extent and orientation for six-degree-of-freedom (6-DoF) action filtering.
- **Geometric action filtering.** A control barrier function quadratic program
  (CBF-QP) filters nominal actions using local safety constraints.
- **Risk-adaptive correction.** Constraint selection, clipping, and blending
  regulate the intervention applied to the nominal action.

Comparisons cover nominal policy execution, center-point QP, artificial
potential fields (APF), ellipsoid CBF-QP, and proxy-APF methods.
Object-aware, arm-aware, and feedback-triggered replanning extensions remain
experimental.

## Pose-Aware Local Proxy Points

A center-distance constraint measures clearance from a single reference point
and can miss local collision risks at the fingertips. PARMA represents the
gripper with local proxy points covering the **base**, **fingertips**,
**lateral regions**, and **approach direction**, allowing constraints to
reflect the gripper's geometry and pose.

<p align="center">
  <img src="Pictures/fig2_local_proxy_points.png" alt="Comparison of a center-distance constraint and PARMA local proxy points at the gripper base, fingertips, lateral regions, and approach direction." width="100%">
</p>

*Figure 2. Center-distance constraints (left) and PARMA's pose-aware local
proxy points (right).*

## 🌱 Code Availability

**Code is coming soon.**

This repository currently presents the research overview and method
illustrations. The implementation, installation guide, and usage instructions
will be added in a future update.

## Research Scope

PARMA is intended for simulation-oriented research and does not provide a
formal system-level safety guarantee.
