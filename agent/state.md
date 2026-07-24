# Recursive Adaptive Dynamics (RAD)

## Metadata

**Framework:** Recursive Adaptive Dynamics (RAD)

**Type:**  
Causal decomposition + empirical hypothesis

**Status:**  
Ontology defined; hypothesis unverified

**Primary object:**  
Evolution of reachable spaces of future adaptive mechanisms

**Core unresolved question:**

Does constraint-bearing information influence the evolution of future adaptive mechanism spaces?

Formal:

\[
\Omega_t \rightarrow \Delta\mathcal{G}_{t+1}
\]

Status:

\[
\text{Hypothesis, not established fact}
\]

---

# Scope Boundary

RAD is not a theory of:

- intelligence
- learning
- optimization
- alignment
- agency
- consciousness

RAD is a causal framework for studying systems where mechanisms of change can themselves become objects of change.

The focus is:

\[
\text{evolution of reachable spaces of adaptive mechanisms}
\]

---

# Definition

Recursive Adaptive Dynamics (RAD) studies systems in which the mechanisms responsible for producing future change can themselves change.

The central distinction:

\[
\boxed{
\text{change within a mechanism space}
\neq
\text{change of the mechanism space itself}
}
\]

A system may improve existing strategies without increasing its ability to generate future strategies.

---

# Core Ontology

## System State

\[
X_t
\]

The current configuration of the system.

---

## Transformation Mechanism

\[
F_t
\]

The mechanism producing state changes.

\[
X_{t+1}=F_t(X_t)
\]

---

## Transformation-Selection Mechanism

\[
G_t
\]

The mechanism that modifies future transformation mechanisms.

\[
F_{t+1}=G_t(F_t)
\]

---

## Reachable Adaptive Mechanism Space

\[
\mathcal{G}_t
\]

The reachable space of possible transformation-selection mechanisms.

\[
G_t \in \mathcal{G}_t
\]

---

## Internal Model Layer

\[
M_t
\]

Internal representations, memory, or models of consequences.

---

## Constraint-Bearing Information

\[
\Omega_t
\]

Information generated through consequences and environmental interaction.

---

# Causal Hierarchy

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

The reachable space of future adaptive mechanisms changes.

---

# Causal Structure

Main recursive chain:

\[
\boxed{
X \rightarrow F \rightarrow G \rightarrow \mathcal{G}
}
\]

Constraint pathway:

\[
\boxed{
\Omega \rightarrow M \rightarrow G \rightarrow F \rightarrow X
}
\]

---

# Central Hypothesis

RAD hypothesizes:

\[
\boxed{
\Omega_t \rightarrow \Delta\mathcal{G}_{t+1}
}
\]

Meaning:

Long-horizon recursive adaptation may depend on whether viability-relevant constraints continue influencing the evolution of reachable future adaptive mechanisms.

---

# Operational Model

RAD does not attempt to estimate the complete space of all possible mechanisms.

Instead, it defines a bounded task-specific mechanism space:

\[
\mathcal{G}^{(task)}_t
\]

using a finite mechanism library:

\[
\mathcal{L}=\{G_1,G_2,...,G_n\}
\]

Each mechanism has:

## Accessibility

\[
q_i(t)
\]

Probability that mechanism \(G_i\) remains reachable.

---

## Viability

\[
v_i(t)
\]

Probability that mechanism \(G_i\) remains useful under future perturbations.

---

Reachable mechanism space:

\[
\mathcal{G}^{(task)}_t
=
\{G_i:q_i(t)>\theta_q\}
\]

Viable mechanism space:

\[
\mathcal{G}^{*}_t
=
\{G_i:q_i(t)>\theta_q \land v_i(t)>\theta_v\}
\]

---

# Simulator State

\[
\boxed{
S_t=(X_t,F_t,\pi_t,G_t,M_t,q_t,v_t)
}
\]

Where:

| Symbol | Meaning |
|---|---|
| \(X_t\) | System state |
| \(F_t\) | Transformation mechanism |
| \(\pi_t\) | Mechanism selection policy |
| \(G_t\) | Selected transformation-selection mechanism |
| \(M_t\) | Internal model |
| \(q_t\) | Accessibility distribution |
| \(v_t\) | Viability distribution |

---

# Policy Separation

The simulator separates:

\[
\boxed{
\text{available mechanisms}
\neq
\text{selected mechanisms}
}
\]

Selection:

\[
\pi_t(\mathcal{G}^{(task)}_t)\rightarrow G_t
\]

A system may choose poorly while retaining adaptive openness.

A system may choose well while losing future options.

---

# Experimental Intervention

Two systems share:

- mechanism library
- compute
- initial capability
- environment
- modification capacity

Only one causal pathway changes.

---

## Grounded Recursion

Constraint-coupled:

\[
(q,v)_{t+1}=J(q_t,v_t,\Omega_t)
\]

---

## Decoupled Recursion

Constraint-independent:

\[
(q,v)_{t+1}=J(q_t,v_t)
\]

---

# Measurements

## Performance

\[
P(t)
\]

Current competence.

---

## Recovery

\[
R
\]

Ability to recover after environmental change.

---

## Exploration

\[
E
\]

Discovery of new successful mechanisms.

---

## Adaptive Openness

\[
O_t=
\frac{\sum_i q_i(t)v_i(t)}
{\sum_i q_i(t)}
\]

Measures future-compatible adaptive capacity among reachable mechanisms.

---

# Predicted Phenomenon

RAD does not predict immediate failure.

Expected:

Early:

\[
P_A \approx P_B
\]

Later:

\[
O_A > O_B
\]

After novelty:

\[
R_A > R_B
\]

Possible signature:

\[
\boxed{
P(t)\uparrow \land O(t)\downarrow
}
\]

A system becomes more capable inside a narrowing adaptive basin.

---

# Falsification

RAD is weakened if systems maintain long-horizon adaptive capacity while:

\[
\Omega_t\nrightarrow\Delta\mathcal{G}_{t+1}
\]

under:

- repeated novelty
- distribution shifts
- adversarial perturbations
- misleading proxies

Possible outcomes:

1. Adaptive-space evolution is unnecessary.
2. Another mechanism performs the same function.
3. The decomposition is descriptive rather than causal.

---

# Repository Structure
