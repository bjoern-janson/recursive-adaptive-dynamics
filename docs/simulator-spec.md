# Minimal Recursive Adaptive Dynamics Simulator Specification v0.1

## Metadata

**Project:**  
Recursive Adaptive Dynamics (RAD)

**Artifact Type:**  
Simulator specification

**Purpose:**  
Define a minimal computational environment for testing whether constraint-shaped evolution of adaptive mechanism spaces produces measurable differences in long-horizon adaptation.

**Status:**  
Specification defined; implementation pending


---

# 1. Objective

The simulator tests the hypothesis:

\[
\boxed{
\Omega_t\rightarrow\Delta\mathcal{G}^{(task)}_{t+1}
}
\]

against the counterfactual:

\[
\boxed{
\Omega_t\nrightarrow\Delta\mathcal{G}^{(task)}_{t+1}
}
\]

while controlling:

- initial capability
- compute budget
- mechanism library
- self-modification capacity
- environment exposure


The simulator does not test whether feedback improves performance.

It tests whether consequence-shaped evolution of adaptive mechanism spaces changes future adaptive trajectories.


---

# 2. Core Principle

RAD separates:

\[
\boxed{
\text{available mechanisms}
\neq
\text{selected mechanism}
\neq
\text{current performance}
\neq
\text{future adaptive capacity}
}
\]

The simulator therefore models:

- accessibility
- viability
- selection
- execution


---

# 3. Agent State

The complete system state is:

\[
\boxed{
S_t=(X_t,F_t,\pi_t,G_t,M_t,q_t,v_t)
}
\]


## X — System State

\[
X_t
\]

Current configuration of the agent/environment interaction.


---

## F — Transformation Mechanism

\[
F_t
\]

The process producing state transitions.

\[
X_{t+1}=F_t(X_t)
\]


---

## π — Selection Policy

\[
\pi_t
\]

Maps accessible adaptive mechanisms to a selected mechanism.

\[
\pi_t(\mathcal{G}^{(task)}_t)\rightarrow G_t
\]


---

## G — Transformation-Selection Mechanism

\[
G_t
\]

Modifies future transformation processes.

\[
F_{t+1}=G_t(F_t)
\]


---

## M — Internal Model

\[
M_t
\]

Representation of consequences, history, and environmental structure.


---

## q — Accessibility Distribution

\[
q_i(t)
\]

Probability that mechanism:

\[
G_i
\]

remains reachable.

\[
q_i(t)\in[0,1]
\]


---

## v — Viability Distribution

\[
v_i(t)
\]

Probability that mechanism:

\[
G_i
\]

remains adaptive under future perturbations.

\[
v_i(t)\in[0,1]
\]


---

# 4. Mechanism Library

The simulator uses a bounded mechanism universe:

\[
\mathcal{L}
=
\{G_1,G_2,...,G_n\}
\]


Each mechanism contains:

\[
G_i=(a_i,m_i,c_i,h_i)
\]

where:

| Variable | Meaning |
|---|---|
| \(a_i\) | action rule |
| \(m_i\) | modification operator |
| \(c_i\) | resource cost |
| \(h_i\) | historical statistics |


RAD does not attempt to estimate the complete space of possible mechanisms.

It studies trajectories through a controlled local mechanism space.


---

# 5. Adaptive Spaces

## Reachable Mechanism Space

\[
\boxed{
\mathcal{G}^{(task)}_t
=
\{G_i:q_i(t)>\theta_q\}
}
\]


Represents mechanisms currently accessible to the system.


---

## Viable Mechanism Space

\[
\boxed{
\mathcal{G}^{*}_t
=
\{G_i:q_i(t)>\theta_q\land v_i(t)>\theta_v\}
}
\]


Represents mechanisms that are both accessible and future-compatible.


---

# 6. Causal Architecture

Full simulator loop:

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

# 7. Experimental Intervention

The only difference between experimental agents is the adaptive-space update rule.


## Agent A — Grounded Evolution

Constraint-coupled:

\[
\boxed{
(q,v)_{t+1}
=
J(q_t,v_t,\Omega_t)
}
\]


Environmental consequences influence future mechanism accessibility and viability.


---

## Agent B — Decoupled Evolution

Constraint-independent:

\[
\boxed{
(q,v)_{t+1}
=
J(q_t,v_t)
}
\]


The system can still self-modify but adaptive-space evolution is disconnected from current consequences.


---

# 8. Initial Conditions

The comparison is valid only if both agents begin equivalent.

Require:

\[
P_A(0)\approx P_B(0)
\]

\[
q_A(0)=q_B(0)
\]

\[
v_A(0)=v_B(0)
\]


Equal:

- mechanism library
- compute budget
- environment exposure
- modification capacity


Only the causal pathway differs.


---

# 9. Environment

The environment contains:

\[
E_t=(R_t,C_t)
\]

where:

- \(R_t\) = hidden environmental rule
- \(C_t\) = current constraints


The agent observes:

\[
\Omega_t
\]

but does not directly observe:

\[
R_t
\]


---

# 10. Novelty Generator

The environment contains regime changes:

\[
E_1\rightarrow E_2\rightarrow E_3
\]

with increasing novelty:

\[
d(E_t,E_{t+1})
\]


The purpose is not to test problem-solving ability.

The purpose is to test preservation of future adaptive mechanisms.


---

# 11. Metrics

The simulator records:

\[
\mathbf{A}=(P,R,E,O)
\]


## Performance

\[
P(t)
\]

Current task competence.


---

## Recovery

\[
R
\]

Performance recovery after environmental disruption.


---

## Exploration

\[
E
\]

Discovery of previously unused successful mechanisms.


---

## Adaptive Openness

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


Measures future viability among reachable mechanisms.


---

# 12. Divergence Metrics

Accessibility divergence:

\[
D_q(t)=D(q_A(t),q_B(t))
\]


Viability divergence:

\[
D_v(t)=D(v_A(t),v_B(t))
\]


Openness divergence:

\[
D_O(t)=|O_A(t)-O_B(t)|
\]


---

# 13. Expected Signature

The simulator should not produce immediate failure.

Expected:

Early:

\[
P_A\approx P_B
\]

\[
O_A\approx O_B
\]


After novelty:

\[
O_A>O_B
\]

\[
R_A>R_B
\]


The predicted phenomenon:

\[
\boxed{
\text{adaptive closure}
}
\]


A system may improve present performance while reducing future adaptive openness.


---

# 14. Falsification

RAD is weakened if systems without:

\[
\Omega_t\rightarrow\Delta\mathcal{G}^{(task)}_{t+1}
\]

maintain equivalent:

- recovery
- exploration
- adaptive openness

under:

- long horizons
- repeated novelty
- adversarial perturbations


---

# 15. Implementation Goal

The first implementation should answer one question:

\[
\boxed{
\text{Can two systems with identical present capability diverge solely because their adaptive spaces evolve differently?}
}
\]


If yes:

RAD identifies a measurable causal phenomenon.

If no:

RAD remains a useful descriptive decomposition but the central hypothesis is weakened.
