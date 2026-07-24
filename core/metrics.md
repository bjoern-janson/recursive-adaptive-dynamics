# Recursive Adaptive Dynamics (RAD)
# Metrics

## Purpose

This document defines measurable quantities used to evaluate RAD simulations.

The primary measurement target is not intelligence or performance.

The primary target is:

\[
\Delta\mathcal{G}^{(task)}
\]

the change in reachable adaptive mechanism space.

---

# 1. Performance

Performance measures current task competence.

\[
P(t)
\]

Example:

\[
P(t)=\frac{\text{successful outcomes}}{\text{total outcomes}}
\]

Performance is a local measure.

It does not directly measure future adaptive capacity.

---

# 2. Accessibility Metrics

## 2.1 Mechanism Accessibility

Each mechanism has accessibility:

\[
q_i(t)\in[0,1]
\]

where:

\[
q_i(t)=P(G_i\text{ reachable at }t)
\]

---

## 2.2 Accessible Mechanism Count

Number of reachable mechanisms:

\[
N_q(t)=
|\{G_i:q_i(t)>\theta_q\}|
\]

Measures:

> How many adaptive mechanisms remain available?

---

## 2.3 Accessibility Entropy

Distributional diversity of reachable mechanisms:

\[
H_q(t)=
-\sum_i q_i(t)\log(q_i(t))
\]

Higher values indicate broader accessibility distribution.

---

## 2.4 Accessibility Drift

Difference between two systems:

\[
D_q(t)=D(q_A(t),q_B(t))
\]

where \(D\) is a distribution distance.

Example:

\[
D_{KL}(q_A||q_B)
\]

---

# 3. Viability Metrics

## 3.1 Mechanism Viability

Each mechanism has:

\[
v_i(t)\in[0,1]
\]

where:

\[
v_i(t)=P(G_i\text{ remains adaptive under future perturbations})
\]

---

## 3.2 Viable Mechanism Count

\[
N_v(t)=
|\{G_i:q_i(t)>\theta_q\land v_i(t)>\theta_v\}|
\]

Measures:

> How many reachable mechanisms remain future-compatible?

---

## 3.3 Viability Drift

Difference between systems:

\[
D_v(t)=D(v_A(t),v_B(t))
\]

---

# 4. Adaptive Mechanism Space

## 4.1 Reachable Space

\[
\mathcal{G}^{(task)}_t
=
\{G_i:q_i(t)>\theta_q\}
\]

---

## 4.2 Viable Space

\[
\mathcal{G}^{*}_t
=
\{G_i:q_i(t)>\theta_q
\land
v_i(t)>\theta_v
\}
\]

---

## 4.3 Space Divergence

Difference between two trajectories:

\[
D_{\mathcal{G}}(t)
=
D(
\mathcal{G}_A(t),
\mathcal{G}_B(t)
)
\]

Possible implementations:

- Jaccard distance
- distribution distance
- embedding distance

---

# 5. Adaptive Openness

The primary RAD metric:

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

Expected future viability of reachable mechanisms.

---

Properties:

## High accessibility, low viability

\[
q_i\uparrow,\quad v_i\downarrow
\]

The system retains options but they are brittle.

---

## Low accessibility, high viability

\[
q_i\downarrow,\quad v_i\uparrow
\]

The system has good mechanisms but poor access.

---

## High openness

\[
q_i\uparrow,\quad v_i\uparrow
\]

The system maintains adaptable possibility.

---

# 6. Recovery Metrics

Recovery measures adaptation after environmental disruption.

Define:

\[
E_t\rightarrow E_{t+\Delta}
\]

as a regime change.

Recovery:

\[
R=
\frac{
P(t+\Delta)-P_{min}
}{
P_{pre}-P_{min}
}
\]

where:

- \(P_{pre}\) = performance before disruption
- \(P_{min}\) = minimum performance after disruption

---

# 7. Exploration Metrics

Exploration measures discovery of new mechanisms.

## Mechanism discovery rate

\[
E_m=
\frac{
|\text{newly activated }G_i|
}{
T
}
\]

---

## Mechanism diversity

\[
E_d=
H_q(t)
\]

---

# 8. Composite Adaptive Vector

RAD evaluation uses:

\[
\boxed{
\mathbf{A}=(P,R,E,O)
}
\]

where:

| Variable | Meaning |
|-|-|
| \(P\) | current performance |
| \(R\) | recovery after disruption |
| \(E\) | exploration/discovery |
| \(O\) | adaptive openness |

---

# 9. Expected RAD Signature

The predicted pattern is not immediate performance superiority.

Expected:

Early:

\[
P_A\approx P_B
\]

\[
O_A\approx O_B
\]

Later:

\[
O_A>O_B
\]

After novelty:

\[
R_A>R_B
\]

---

# 10. Adaptive Closure

A system exhibits adaptive closure when:

\[
P(t)\uparrow
\]

while:

\[
O(t)\downarrow
\]

Meaning:

Current optimization improves while future adaptive openness decreases.

---

# 11. Primary Experimental Outcome

The key comparison:

Grounded:

\[
J(q,v,\Omega)
\]

versus:

Decoupled:

\[
J(q,v)
\]

The question is whether removing:

\[
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
\]

produces measurable divergence in:

\[
(P,R,E,O)
\]

---

# 12. Metric Requirements

A valid RAD metric should:

- distinguish availability from usefulness
- distinguish present performance from future adaptability
- measure trajectory change, not only endpoint values
- remain defined within a bounded mechanism library

---

# Summary

RAD measures:

\[
\boxed{
\text{how adaptive mechanism distributions evolve over time}
}
\]

not:

\[
\boxed{
\text{how intelligent a system is}
}
\]
