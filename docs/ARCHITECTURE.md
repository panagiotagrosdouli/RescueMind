# RescueMind Conceptual Architecture

## 1. Purpose

This document describes a preliminary architecture for RescueMind, an uncertainty-aware decision-support framework for robotic urban search and rescue. The architecture is deliberately modular so that individual research questions can be investigated independently before attempting full-system integration.

The system is not assumed to operate as a single monolithic artificial-intelligence model. Instead, it is conceived as a distributed pipeline that separates sensing, perception, mapping, coordination, risk estimation, prioritization, and human interaction.

## 2. Design Objectives

The architecture should support:

- heterogeneous aerial, ground, and stationary robotic agents;
- operation in GPS-denied and communication-degraded environments;
- multimodal sensing with asynchronous data streams;
- explicit uncertainty representation;
- graceful degradation under platform or network failure;
- local inference at the edge;
- traceable recommendations for human decision-makers;
- simulation-first development and staged hardware validation.

## 3. System Layers

### 3.1 Robotic and Sensing Layer

This layer contains the physical or simulated agents that observe and interact with the environment.

#### Aerial agents

Potential responsibilities:

- rapid exterior reconnaissance;
- roof and façade inspection;
- thermal and visual surveying;
- relay-node deployment;
- access through elevated or partially open spaces.

Possible sensors:

- RGB or low-light cameras;
- thermal cameras;
- lightweight LiDAR or depth cameras;
- inertial measurement units;
- barometers;
- radio-signal measurements.

#### Ground agents

Potential responsibilities:

- navigation under slabs and through narrow passages;
- close-range acoustic and radar sensing;
- persistent local monitoring;
- transport or deployment of sensor beacons.

Possible sensors:

- RGB-D cameras;
- ultra-wideband radar;
- microphone arrays;
- carbon dioxide and air-quality sensors;
- vibration sensors;
- wheel odometry and inertial sensors.

#### Stationary beacons

Potential responsibilities:

- local environmental monitoring;
- mesh-network extension;
- radio ranging and localization support;
- persistent acoustic or gas sensing;
- detection of environmental changes over time.

### 3.2 Edge Processing Layer

Each agent should perform a subset of time-critical processing locally. Candidate functions include:

- visual and thermal feature extraction;
- acoustic event detection;
- sensor quality assessment;
- local obstacle detection;
- local odometry;
- data compression and event-triggered transmission;
- health monitoring and fault detection.

The objective is to avoid transmitting every raw measurement. Agents should communicate compact, task-relevant representations when bandwidth is limited.

### 3.3 Communication and Coordination Layer

The communication layer should support dynamic, infrastructure-independent networking.

Research topics include:

- ad hoc mesh formation;
- delay-tolerant messaging;
- bandwidth-aware data prioritization;
- store-carry-forward communication;
- synchronization under intermittent connectivity;
- distributed task allocation;
- recovery after agent loss.

A useful design principle is that no single communication failure should eliminate all local autonomy.

### 3.4 Collaborative Perception Layer

This layer combines observations from multiple agents.

Core functions may include:

- temporal alignment;
- spatial registration;
- cross-modal data association;
- duplicate-observation detection;
- confidence calibration;
- conflict detection;
- distributed or centralized feature fusion.

The system should distinguish between:

1. independent evidence supporting the same hypothesis;
2. duplicated evidence originating from the same underlying observation;
3. contradictory evidence;
4. missing evidence caused by sensor limitations.

### 3.5 Living Disaster Twin

The Living Disaster Twin is a continuously updated probabilistic representation of the environment.

It may include:

- geometric occupancy;
- traversability;
- structural hazards;
- fire, smoke, gas, or temperature anomalies;
- communication coverage;
- robot locations and health states;
- candidate survivor hypotheses;
- confidence and observation history;
- rescue access routes.

Unlike a static map, the twin should model change. A passage that was open five minutes ago may become obstructed. A weak acoustic signal may strengthen, disappear, or be contradicted by later measurements.

### 3.6 Survivor-Hypothesis Layer

Rather than treating every detection as a confirmed person, RescueMind should maintain explicit hypotheses.

A survivor hypothesis may contain:

- estimated position and spatial uncertainty;
- supporting sensor observations;
- time of most recent evidence;
- estimated probability of human presence;
- indicators of possible viability;
- alternative explanations;
- required follow-up observations.

Example:

```yaml
hypothesis_id: H-017
position_estimate: [12.4, 7.8, -1.2]
position_uncertainty_m: 1.6
human_presence_probability: 0.73
supporting_evidence:
  - thermal_anomaly
  - periodic_acoustic_signal
contradictory_evidence:
  - no_detectable_co2_change
recommended_action:
  - deploy_ground_robot_for_confirmation
```

### 3.7 Hazard and Accessibility Layer

This layer estimates whether a location can be reached and at what risk.

Potential inputs include:

- traversable-space maps;
- structural movement;
- obstacle geometry;
- temperature and gas measurements;
- robot mobility constraints;
- estimated human-rescuer access requirements;
- route length and intervention time.

This layer should never claim structural safety beyond the evidence available. Its output should be an uncertainty-qualified operational estimate, not a substitute for structural-engineering assessment.

### 3.8 Rescue Priority Index Layer

The Rescue Priority Index combines survivor evidence, urgency, accessibility, risk, and uncertainty.

A preliminary formulation might be:

\[
RPI_i = w_1 P_{human,i} + w_2 P_{viable,i} + w_3 A_i - w_4 R_i - w_5 T_i - w_6 U_i
\]

where:

- \(P_{human,i}\) is the probability of human presence;
- \(P_{viable,i}\) is the probability of viable survival indicators;
- \(A_i\) is accessibility;
- \(R_i\) is intervention risk;
- \(T_i\) is estimated time to reach and assist;
- \(U_i\) is uncertainty.

This linear expression is only a conceptual baseline. Future research should investigate:

- Bayesian decision models;
- constrained optimization;
- Pareto ranking;
- risk-sensitive planning;
- learning-to-rank approaches;
- expert-defined rules;
- calibrated confidence intervals.

The ranking must remain interpretable. A coordinator should be able to see why one location is ranked above another.

### 3.9 Human Command Interface

The interface should present:

- a 2D and 3D operational map;
- candidate survivor locations;
- confidence levels;
- evidence summaries;
- hazard regions;
- recommended routes;
- robot states;
- communication coverage;
- changes since the previous update.

The interface should avoid false precision. For example, a probability of 0.731 should not be displayed in a way that implies unrealistic certainty. Confidence categories and evidence provenance may be more appropriate in some contexts.

## 4. Information Flow

A conceptual information flow is:

```text
Sensors
  ↓
Local preprocessing and quality checks
  ↓
Compact observations or learned features
  ↓
Communication and temporal synchronization
  ↓
Collaborative perception
  ↓
Living Disaster Twin
  ↓
Survivor and hazard hypotheses
  ↓
Rescue Priority Index
  ↓
Human-readable recommendations
  ↓
Coordinator feedback and robot-task updates
```

Human feedback should be able to modify priorities, reject hypotheses, request additional evidence, or constrain robot behaviour.

## 5. Candidate Software Stack

The exact stack remains open, but an initial research prototype may use:

- **ROS 2** for robotic middleware;
- **Gazebo, Isaac Sim, or Webots** for simulation;
- **Python and C++** for rapid prototyping and real-time components;
- **PyTorch** for learned perception models;
- **OpenCV and Open3D** for image and point-cloud processing;
- **GTSAM, Ceres, or equivalent tools** for estimation and optimization;
- **DDS or ROS 2 communication profiles** for distributed messaging;
- **Foxglove, RViz, or a custom web interface** for visualization.

Technology selection should follow research requirements rather than branding preferences.

## 6. Evaluation Strategy

The architecture should be evaluated using scenario-level metrics, not only model accuracy.

Candidate metrics include:

- survivor-detection precision and recall;
- calibration error;
- localization error;
- false-priority rate;
- time to first credible survivor hypothesis;
- time to correctly rank high-priority locations;
- map completeness;
- route-feasibility accuracy;
- bandwidth consumption;
- energy consumption;
- resilience to agent loss;
- human decision time;
- human trust calibration;
- frequency of unsafe or misleading recommendations.

## 7. Safety and Failure Modes

Expected failure modes include:

- thermal false positives;
- human-like acoustic noise;
- sensor drift;
- map inconsistency;
- localization failure;
- stale observations;
- communication partitions;
- adversarial or accidental radio interference;
- structural change after mapping;
- overconfidence caused by correlated sensors;
- automation bias in human users.

Each module should expose health, confidence, and freshness metadata. The system should be able to abstain when evidence is insufficient.

## 8. Near-Term Prototype Boundary

The first prototype should not attempt to implement the complete vision. A realistic minimum research demonstrator could include:

1. two or more simulated mobile agents;
2. a damaged-building simulation environment;
3. RGB-D or LiDAR-based mapping;
4. simulated thermal and acoustic observations;
5. simple probabilistic survivor hypotheses;
6. a baseline Rescue Priority Index;
7. a visualization dashboard;
8. controlled experiments with communication loss and false detections.

This limited scope would be sufficient to test the central proposition: whether distributed robotic evidence can be converted into a useful, transparent rescue-priority map.
