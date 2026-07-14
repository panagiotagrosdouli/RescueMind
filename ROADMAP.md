# RescueMind Roadmap

This roadmap translates the RescueMind vision into a sequence of research and engineering milestones. Dates are intentionally omitted until the technical scope, available supervision, hardware access, and team capacity are defined.

## Phase 0 — Problem Definition and Scope

### Objectives

- Define the initial disaster scenario and operational assumptions.
- Identify the intended users and decision points.
- Separate research questions from implementation goals.
- Establish ethical, safety, and regulatory constraints.

### Deliverables

- Use-case document;
- stakeholder and workflow map;
- initial system requirements;
- risk register;
- glossary of key terms;
- definition of success and failure.

### Exit criteria

A narrow prototype question can be stated precisely and evaluated quantitatively.

---

## Phase 1 — Simulation Baseline

### Objectives

- Build or configure a damaged-building simulation environment.
- Introduce at least two heterogeneous simulated agents.
- Establish baseline exploration, mapping, and communication.

### Candidate tasks

- ROS 2 workspace initialization;
- simulator selection;
- robot-model integration;
- occupancy mapping;
- simulated communication constraints;
- scenario logging and reproducibility.

### Deliverables

- reproducible simulation setup;
- baseline maps;
- exploration metrics;
- initial test scenarios.

### Exit criteria

Multiple agents can explore the environment, exchange state information, and produce a shared baseline map.

---

## Phase 2 — Multimodal Survivor Evidence

### Objectives

- Introduce simulated thermal, acoustic, and environmental observations.
- Represent detections as probabilistic evidence rather than binary truth.
- Evaluate false positives and contradictory measurements.

### Deliverables

- sensor simulation models;
- timestamped observation schema;
- baseline fusion method;
- confidence-calibration evaluation;
- documented failure cases.

### Exit criteria

The system can create, update, merge, and reject survivor hypotheses from multiple noisy observations.

---

## Phase 3 — Living Disaster Twin

### Objectives

- Combine geometry, hazards, robot states, communication coverage, and survivor hypotheses.
- Preserve observation history and freshness.
- Detect meaningful changes in the environment.

### Deliverables

- dynamic map representation;
- hazard and accessibility layers;
- survivor-hypothesis layer;
- update and conflict-resolution mechanisms;
- visualization prototype.

### Exit criteria

The digital representation remains internally consistent during controlled environmental changes and communication interruptions.

---

## Phase 4 — Rescue Priority Index

### Objectives

- Formalize the variables used in rescue prioritization.
- Compare interpretable baseline models with more advanced alternatives.
- Include uncertainty and abstention.

### Candidate methods

- weighted rule-based scoring;
- Bayesian decision models;
- constrained multi-objective optimization;
- risk-sensitive ranking;
- learning-to-rank under expert supervision.

### Deliverables

- formal RPI specification;
- baseline implementation;
- synthetic and simulated evaluation scenarios;
- sensitivity analysis;
- explanation format for each ranking.

### Exit criteria

The system ranks candidate locations consistently under predefined scenarios and clearly communicates the evidence and uncertainty behind each recommendation.

---

## Phase 5 — Multi-Agent Coordination

### Objectives

- Direct robots toward observations that reduce decision uncertainty.
- Balance information gain, urgency, robot safety, and energy.
- Support replanning after agent or communication failure.

### Deliverables

- task-allocation baseline;
- active-perception strategy;
- degraded-network experiments;
- agent-loss recovery tests;
- coordination performance report.

### Exit criteria

The robotic team improves rescue-priority confidence more efficiently than independent or purely coverage-based exploration baselines.

---

## Phase 6 — Human Command Interface

### Objectives

- Present priorities, evidence, hazards, and uncertainty clearly.
- Allow operators to reject, confirm, or request further investigation.
- Reduce automation bias and false certainty.

### Deliverables

- interactive map;
- evidence-provenance panel;
- confidence and freshness indicators;
- operator-feedback controls;
- preliminary usability study protocol.

### Exit criteria

Users can identify why a recommendation was produced and can safely override or challenge it.

---

## Phase 7 — Controlled Hardware Demonstrator

### Objectives

- Transfer a restricted subset of the pipeline to physical platforms.
- Evaluate simulation-to-reality gaps.
- Validate timing, communication, sensing, and compute assumptions.

### Possible minimum setup

- one small aerial platform;
- one compact ground platform;
- one or more deployable sensing nodes;
- controlled indoor rubble-like test environment;
- offline safety supervision.

### Deliverables

- hardware integration report;
- sensor-calibration procedures;
- controlled demonstrations;
- real-world failure analysis;
- revised architecture.

### Exit criteria

Selected system components operate reliably in a controlled environment without making claims beyond the tested conditions.

---

## Phase 8 — External Collaboration and Validation

### Objectives

- Seek feedback from robotics researchers, structural engineers, emergency-response professionals, and human-factors specialists.
- Align future experiments with operational reality.
- Identify requirements for responsible field evaluation.

### Deliverables

- expert-feedback report;
- revised use cases;
- validation protocol;
- collaboration and funding plan;
- publication or competition strategy.

## Immediate Repository Priorities

1. Create a minimal ROS 2 project structure.
2. Select the first simulator and robot models.
3. Define a machine-readable observation and survivor-hypothesis schema.
4. Design one small reproducible disaster scenario.
5. Implement a transparent baseline Rescue Priority Index.
6. Document assumptions before adding complex AI models.

## Guiding Principle

The project should advance by demonstrating one defensible capability at a time. A simple, measurable, and transparent baseline is more valuable than an impressive but unvalidated claim.
