# Recursive Adaptive Dynamics (RAD) — Formalism

## 1. Purpose

This document defines the mathematical objects and causal relationships used by Recursive Adaptive Dynamics (RAD).

RAD studies systems where mechanisms responsible for producing future change can themselves become objects of change.

The central object is:

\[
\boxed{
\text{evolution of reachable spaces of future adaptive mechanisms}
}
\]

---

# 2. Primitive Objects

## 2.1 System State

\[
X_t
\]

The configuration of the system at time \(t\).

State evolution:

\[
X_{t+1}=F_t(X_t)
\]

where:

- \(X_t\) = system state
- \(F_t\) = transformation mechanism

---

## 2.2 Transformation Mechanism

\[
F_t
\]

A mapping that determines how the current state changes.

\[
F_t:X_t\rightarrow X_{t+1}
\]

The transformation mechanism is the immediate cause of state evolution.

---

## 2.3 Transformation-Selection Mechanism

\[
G_t
\]

A mechanism that modifies future transformation mechanisms.

\[
F_{t+1}=G_t(F_t)
\]

The distinction:

\[
\boxed{
G_t \neq F_t
}
\]

\(F_t\) changes states.

\(G_t\) changes the mechanisms that change states.

---

## 2.4 Adaptive Mechanism Space

\[
\mathcal{G}_t
\]

The reachable space of possible transformation-selection mechanisms.

Membership:

\[
G_t\in\mathcal{G}_t
\]

The critical distinction:

\[
\boxed{
G_t\neq\mathcal{G}_t
}
\]

A system can modify its current mechanism without modifying the space of mechanisms available to it.

---

## 2.5 Internal Model Layer

\[
M_t
\]

The internal representation, memory, or model used to process consequences.

\[
M_{t+1}=U(M_t,\Omega_t)
\]

---

## 2.6 Constraint Information

\[
\Omega_t
\]

Information generated through consequences, environmental interaction, or viability feedback.

\(\Omega_t\) is not assumed to be perfect.

It may be:

- complete
- incomplete
- delayed
- noisy
- misrepresented

---

# 3. Causal Hierarchy

RAD separates four levels of recursive change.

---

## Level 0 — State Dynamics

\[
X_{t+1}=F_t(X_t)
\]

The system changes.

---

## Level 1 — Transformation Dynamics

\[
F_{t+1}=G_t(F_t)
\]

The mechanism producing change changes.

---

## Level 2 — Transformation-Selection Dynamics

\[
G_{t+1}=H_t(G_t,\Omega_t)
\]

The mechanism selecting future transformations changes.

---

## Level 3 — Adaptive Mechanism-Space Dynamics

\[
\mathcal{G}_{t+1}=J_t(\mathcal{G}_t,\Omega_t)
\]

The reachable space of future transformation-selection mechanisms changes.

---

# 4. Core Dependency Structure

The minimal recursive chain:

\[
\boxed{
X\rightarrow F\rightarrow G\rightarrow\mathcal{G}
}
\]

represents increasing levels of recursive abstraction.

Expanded causal pathway:

\[
\boxed{
\Omega
\rightarrow
M
\rightarrow
G
\rightarrow
F
\rightarrow
X
}
\]

The empirical question concerns the link:

\[
\boxed{
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
}
\]

---

# 5. Hypothesis Boundary

RAD separates definitions from claims.

## Defined objects

\[
X,F,G,\mathcal{G},M,\Omega
\]

These define the framework.

---

## Empirical hypothesis

\[
\boxed{
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
}
\]

This is not assumed.

It is tested.

---

# 6. Task-Bounded Adaptive Space

The complete space of all possible mechanisms is not required.

Instead define:

\[
\mathcal{G}^{(task)}_t
\]

The reachable mechanism space within a controlled domain.

A finite mechanism library:

\[
\mathcal{L}
=
\{G_1,G_2,...,G_n\}
\]

defines the possible operators.

Then:

\[
\mathcal{G}^{(task)}_t
\subseteq
\mathcal{L}
\]

---

# 7. Accessibility and Viability

RAD separates two properties.

## Accessibility

\[
q_i(t)
\]

Probability that mechanism \(G_i\) remains reachable.

\[
q_i(t)=P(G_i\in\mathcal{G}^{(task)}_t)
\]

---

## Viability

\[
v_i(t)
\]

Probability that mechanism \(G_i\) remains useful under future perturbations.

\[
v_i(t)=P(G_i\text{ remains adaptive})
\]

---

## Reachable Space

\[
\mathcal{G}^{(task)}_t
=
\{G_i:q_i(t)>\theta_q\}
\]

---

## Viable Space

\[
\mathcal{G}^{*}_t
=
\{G_i:q_i(t)>\theta_q
\land
v_i(t)>\theta_v
\}
\]

---

# 8. Openness Metric

Adaptive-space openness:

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

Among currently reachable mechanisms, how much future adaptive value remains?

---

# 9. Policy Layer

Available mechanisms and selected mechanisms are separate.

Policy:

\[
\pi_t(\mathcal{G}^{(task)}_t)
\rightarrow
G_t
\]

The system contains:

\[
S_t=
(X_t,F_t,\pi_t,G_t,M_t,q_t,v_t)
\]

---

# 10. Experimental Intervention

The simulator compares two update rules.

## Grounded recursion

\[
(q,v)_{t+1}
=
J(q_t,v_t,\Omega_t)
\]

Consequences influence adaptive-space evolution.

---

## Decoupled recursion

\[
(q,v)_{t+1}
=
J(q_t,v_t)
\]

Adaptive-space evolution occurs without consequence coupling.

---

# 11. Primary Prediction

RAD predicts possible divergence between present competence and future adaptability.

Performance:

\[
P(t)\uparrow
\]

while:

\[
O(t)\downarrow
\]

A system can become more effective within a narrowing region of adaptive possibility.

---

# 12. Falsification

The hypothesis is weakened if:

\[
\Omega_t\nrightarrow\Delta\mathcal{G}_{t+1}
\]

yet systems maintain:

\[
R,E,O
\]

under:

- long horizons
- repeated novelty
- adversarial perturbations
- changing constraints

---

# 13. Core Invariant

The central formal relationship:

\[
\boxed{
X\rightarrow F\rightarrow G\rightarrow\mathcal{G}
}
\]

The central empirical question:

\[
\boxed{
\Omega_t\rightarrow\Delta\mathcal{G}_{t+1}
}
\]

RAD asks whether consequence-shaped evolution of adaptive mechanism spaces is a measurable causal factor in long-horizon recursive adaptation.
