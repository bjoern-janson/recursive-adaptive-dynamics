# Recursive Adaptive Dynamics (RAD)
# Mechanism Library

## Purpose

This document defines the bounded mechanism library used by the simulator.

RAD does not attempt to represent the complete space of possible adaptive mechanisms.

Instead, the simulator operates over:

\[
\boxed{
\mathcal{L}=\{G_1,G_2,...,G_n\}
}
\]

a finite approximation of a local adaptive mechanism space.

The experimental question is how accessibility and viability distributions evolve over this shared library.

---

# 1. Mechanism Definition

Each mechanism is represented as:

\[
\boxed{
G_i=(a_i,m_i,c_i,h_i)
}
\]

where:

| Symbol | Meaning |
|-|-|
| \(a_i\) | action behavior |
| \(m_i\) | modification operator |
| \(c_i\) | resource cost |
| \(h_i\) | historical statistics |

---

# 2. Mechanism Components

## 2.1 Action Behavior

\[
a_i
\]

Defines how the mechanism acts on the current task.

Examples:

- exploit current solution
- search alternative solution
- reuse historical pattern
- test unknown strategy

---

## 2.2 Modification Operator

\[
m_i
\]

Defines how the mechanism changes future transformations.

Formally:

\[
F_{t+1}=m_i(F_t)
\]

The modification operator determines how a selected mechanism influences future behavior.

---

## 2.3 Resource Cost

\[
c_i
\]

Represents computational or environmental cost.

Example:

\[
c_i \in \mathbb{R}^{+}
\]

Lower cost mechanisms may remain accessible longer.

---

## 2.4 Historical Statistics

\[
h_i(t)
\]

Stores mechanism history:

\[
h_i(t)=
(success,failures,usage,context)
\]

Historical information may influence:

- accessibility updates
- viability estimation
- policy selection

---

# 3. Example Initial Library

A minimal experiment may use:

\[
\mathcal{L}
=
\{G_1,G_2,G_3,G_4\}
\]

---

## \(G_1\) — Exploit

Purpose:

Use the currently successful transformation.

Properties:

\[
a_1=\text{exploit}
\]

\[
m_1=\text{local optimization}
\]

Strength:

High short-term performance.

Weakness:

Low adaptation under regime change.

---

## \(G_2\) — Explore

Purpose:

Search for alternative transformations.

Properties:

\[
a_2=\text{explore}
\]

\[
m_2=\text{generate variation}
\]

Strength:

Maintains discovery capability.

Weakness:

Higher immediate cost.

---

## \(G_3\) — Reuse

Purpose:

Restore previously successful mechanisms.

Properties:

\[
a_3=\text{retrieve history}
\]

\[
m_3=\text{reactivate previous }F
\]

Strength:

Fast recovery.

Weakness:

Depends on historical relevance.

---

## \(G_4\) — Abstract

Purpose:

Compress discovered patterns into reusable structures.

Properties:

\[
a_4=\text{model structure}
\]

\[
m_4=\text{modify representation}
\]

Strength:

Potentially enables transfer.

Weakness:

Higher complexity cost.

---

# 4. Mechanism Selection

The policy selects from reachable mechanisms:

\[
\pi_t(\mathcal{G}^{(task)}_t)
\rightarrow G_t
\]

Only mechanisms satisfying:

\[
q_i(t)>\theta_q
\]

are selectable.

---

# 5. Mechanism Accessibility

Each mechanism has:

\[
q_i(t)
\]

Accessibility represents:

\[
P(G_i\text{ reachable})
\]

The mechanism library itself remains fixed.

Only accessibility changes.

---

# 6. Mechanism Viability

Each mechanism has:

\[
v_i(t)
\]

Viability represents:

\[
P(G_i\text{ remains useful under future perturbation})
\]

A mechanism can have:

## High accessibility

\[
q_i\approx1
\]

but:

## Low viability

\[
v_i\approx0
\]

Meaning:

The system can still use the mechanism, but the mechanism is no longer future-compatible.

---

# 7. Mechanism Space

The simulator distinguishes:

## Library

\[
\mathcal{L}
\]

All possible mechanisms defined in the experiment.

---

## Reachable space

\[
\mathcal{G}^{(task)}_t
\subseteq
\mathcal{L}
\]

Mechanisms currently available.

---

## Viable space

\[
\mathcal{G}^{*}_t
\subseteq
\mathcal{G}^{(task)}_t
\]

Mechanisms currently available and future-compatible.

---

# 8. Mechanism Evolution

Mechanisms themselves do not need to be created or destroyed.

The first RAD experiments focus on distributional evolution:

\[
q_i(t),v_i(t)
\]

over a fixed library.

Future extensions may allow:

\[
\mathcal{L}_{t+1}\neq\mathcal{L}_t
\]

but this is outside v0.1.

---

# 9. Design Constraints

The mechanism library should:

- contain mechanisms with different adaptation profiles
- allow performance optimization without guaranteed future adaptability
- include mechanisms that become valuable after regime changes
- be simple enough that causal differences remain interpretable

---

# 10. Core Experimental Principle

The mechanism library is shared.

Both experimental conditions use:

\[
\boxed{
\mathcal{L}_A=\mathcal{L}_B
}
\]

The only manipulated variable is:

\[
\boxed{
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
}
\]

The experiment tests whether different adaptive-space update rules create different future trajectories.

---

# Summary

The mechanism library provides the controlled universe:

\[
\boxed{
\mathcal{L}
}
\]

The adaptive state evolves over it:

\[
\boxed{
(q_t,v_t)
}
\]

The observable object is:

\[
\boxed{
\mathcal{G}^{*}_t
}
\]

The experimental question:

\[
\boxed{
\text{Does consequence-shaped evolution of mechanism accessibility and viability preserve future adaptive capacity?}
}
\]
