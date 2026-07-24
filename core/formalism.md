# Recursive Adaptive Dynamics (RAD)
# Formalism

## Purpose

This document defines the mathematical objects and relations used by Recursive Adaptive Dynamics (RAD).

RAD formalizes systems where mechanisms responsible for producing change can themselves become objects of change.

The primary object of study is:

\[
\text{the evolution of reachable spaces of future adaptive mechanisms}
\]

---

# 1. System State

A RAD system at time \(t\) is represented as:

\[
S_t=(X_t,F_t,\pi_t,G_t,M_t,q_t,v_t)
\]

where:

| Symbol | Meaning |
|---|---|
| \(X_t\) | system state |
| \(F_t\) | transformation mechanism |
| \(\pi_t\) | transformation-selection policy |
| \(G_t\) | selected transformation-selection mechanism |
| \(M_t\) | internal model / representation |
| \(q_t\) | accessibility distribution |
| \(v_t\) | viability distribution |

---

# 2. State Dynamics

The lowest level of change is state transition:

\[
X_{t+1}=F_t(X_t)
\]

where:

- \(X_t\) is the current system configuration
- \(F_t\) determines how the system changes

This represents ordinary dynamical evolution.

---

# 3. Transformation Dynamics

The transformation mechanism itself can change:

\[
F_{t+1}=G_t(F_t)
\]

where:

- \(F_t\) is the current transformation process
- \(G_t\) modifies future transformation processes

This introduces recursive adaptation.

---

# 4. Transformation-Selection Policy

The system selects among available adaptive mechanisms through:

\[
\pi_t(\mathcal{G}^{(task)}_t)\rightarrow G_t
\]

where:

- \(\pi_t\) is the selection policy
- \(\mathcal{G}^{(task)}_t\) is the reachable mechanism space
- \(G_t\) is the selected mechanism

This separates:

\[
\text{available mechanisms}
\neq
\text{selected mechanism}
\]

---

# 5. Mechanism Library

A bounded adaptive mechanism library is defined as:

\[
\mathcal{L}=\{G_1,G_2,...,G_n\}
\]

Each mechanism:

\[
G_i=(a_i,m_i,c_i,h_i)
\]

where:

| Symbol | Meaning |
|---|---|
| \(a_i\) | action behavior |
| \(m_i\) | modification operator |
| \(c_i\) | resource cost |
| \(h_i\) | historical statistics |

The simulator operates over a finite approximation of adaptive possibility space.

---

# 6. Accessibility Distribution

Accessibility describes whether a mechanism remains reachable:

\[
q_i(t)=P(G_i\text{ reachable at }t)
\]

The reachable mechanism space is:

\[
\boxed{
\mathcal{G}^{(task)}_t
=
\{G_i\in\mathcal{L}\mid q_i(t)>\theta_q\}
}
\]

Accessibility answers:

> Can this mechanism still be reached?

---

# 7. Viability Distribution

Viability describes future usefulness:

\[
v_i(t)=P(G_i\text{ remains adaptive under future perturbations})
\]

The viable adaptive space is:

\[
\boxed{
\mathcal{G}^{*}_t
=
\{G_i\in\mathcal{L}
\mid
q_i(t)>\theta_q
\land
v_i(t)>\theta_v
\}
}
\]

Viability answers:

> Would this mechanism remain useful under future conditions?

---

# 8. Constraint Information

The environment generates consequence information:

\[
\Omega_t
\]

where:

\[
\Omega_t=f(X_t,E_t)
\]

and:

- \(E_t\) is environmental state
- \(\Omega_t\) contains information produced by consequences

---

# 9. Internal Representation

Constraint information influences internal representation:

\[
M_{t+1}=U(M_t,\Omega_t)
\]

The model layer mediates how consequences affect future adaptive dynamics.

---

# 10. Adaptive-Space Evolution

The central RAD object is the evolution of accessibility and viability:

\[
(q,v)_{t+1}
=
J(q_t,v_t,\Omega_t)
\]

The hypothesis tested by RAD is whether the \(\Omega_t\) dependency is causally important.

---

# 11. Grounded and Decoupled Dynamics

## Grounded recursion

Constraint information affects adaptive-space evolution:

\[
\boxed{
(q,v)_{t+1}
=
J(q_t,v_t,\Omega_t)
}
\]

---

## Decoupled recursion

Adaptive-space evolution occurs without current constraint information:

\[
\boxed{
(q,v)_{t+1}
=
J(q_t,v_t)
}
\]

The intervention removes only:

\[
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
\]

---

# 12. Adaptive Openness

Adaptive openness measures future-compatible accessibility:

\[
\boxed{
O_t=
\frac{
\sum_i q_i(t)v_i(t)
}{
\sum_i q_i(t)
}
}
\]

Interpretation:

Among currently reachable mechanisms, what fraction retain future adaptive value?

---

# 13. Performance Separation

RAD distinguishes current performance from future adaptability.

Performance:

\[
P(t)
\]

Future adaptive capacity:

\[
A_{future}(t)
\]

No equivalence is assumed:

\[
\boxed{
P(t)\neq A_{future}(t)
}
\]

A system may optimize current performance while reducing future adaptive capacity.

---

# 14. Core Dependency Structure

The complete RAD dependency graph:

\[
\boxed{
\Omega_t
\rightarrow
M_t
\rightarrow
(q_t,v_t)
\rightarrow
\mathcal{G}^{*}_t
\rightarrow
\pi_t
\rightarrow
G_t
\rightarrow
F_t
\rightarrow
X_t
\rightarrow
\Omega_{t+1}
}
\]

---

# 15. Formal Research Object

RAD investigates:

\[
\boxed{
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
}
\]

where:

- \(\Omega_t\) = consequence-bearing constraint information
- \(\Delta\mathcal{G}_{t+1}\) = change in reachable future adaptive mechanisms

This relation is an empirical hypothesis, not a definition.
