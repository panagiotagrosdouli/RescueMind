# Research Vision

## Breaking the Wall of Rescue Uncertainty

RescueMind investigates a fundamental limitation in post-disaster response: emergency teams often receive large quantities of incomplete sensor data but lack a unified, uncertainty-aware operational picture that helps them decide where to intervene first.

The central hypothesis is that a heterogeneous robotic team can do more than map debris or detect isolated signals. By combining multimodal observations, collaborative perception, dynamic mapping, and transparent prioritization, robotic systems may help rescuers allocate limited resources more effectively during the earliest and most critical phase of an emergency.

## Research Proposition

The proposed research proposition is:

> A distributed team of aerial robots, ground robots, and sensor nodes can construct and continuously update a probabilistic disaster representation that ranks candidate rescue locations according to evidence of human presence, potential survivability, accessibility, intervention time, operational risk, and uncertainty.

This proposition contains several distinct scientific questions. It therefore should not be treated as a single engineering implementation task, but as a staged research programme.

## Intended Contribution

RescueMind does not claim novelty from the individual use of drones, ground robots, thermal imaging, SLAM, or artificial intelligence. Each of these technologies already has a substantial research literature.

The intended contribution lies in their integration around a different objective:

- not merely **detecting** possible survivors;
- not merely **mapping** a damaged structure;
- not merely **coordinating** a robotic swarm;
- but producing an **interpretable, dynamically updated rescue-priority model** for human decision-makers.

The project therefore shifts the emphasis from autonomous observation to human-centred, uncertainty-aware disaster triage.

## Research Pillars

### 1. Heterogeneous Collaborative Perception

Different robotic platforms possess complementary strengths. Aerial vehicles offer speed and broad visibility, while ground robots can approach confined areas and carry heavier sensors. Fixed beacons can provide persistent observations and communication support.

Research is needed to determine which information should be shared, at what level of abstraction, and under what communication constraints.

### 2. Multimodal Evidence Fusion

No single sensing modality is sufficiently reliable in a collapsed structure. Thermal anomalies can be caused by machinery or heated surfaces. Acoustic signals can be masked by rescue operations. Carbon dioxide measurements are affected by ventilation. Radar measurements may be ambiguous.

RescueMind should combine evidence while accounting for dependence, contradiction, sensor quality, spatial uncertainty, and time.

### 3. Dynamic Disaster Representation

A disaster environment is not static. Rubble may shift, fires may spread, aftershocks may alter access routes, and communication coverage may change.

The Living Disaster Twin should therefore preserve both the current estimate and the history of how that estimate evolved.

### 4. Explainable Rescue Prioritization

A ranking is useful only when its reasoning can be inspected. Emergency coordinators need to know whether a high-priority recommendation is supported by thermal evidence, repeated acoustic observations, accessibility estimates, or a combination of signals.

The system should communicate uncertainty and alternative explanations instead of presenting predictions as facts.

### 5. Human–Robot Teaming

The purpose of RescueMind is not to remove people from decision-making. It is to improve the information available to trained professionals.

Research should examine how rescuers interact with recommendations, how they challenge or correct the system, and how interface design affects trust, workload, and decision quality.

## Preliminary Research Objectives

1. Develop a simulation environment for heterogeneous robotic disaster response.
2. Establish baseline methods for distributed exploration and mapping.
3. Model multimodal survivor evidence probabilistically.
4. Construct a dynamic representation of hazards, access routes, and survivor hypotheses.
5. Define and compare alternative Rescue Priority Index formulations.
6. Design an interface that exposes evidence, uncertainty, and recommendation provenance.
7. Evaluate performance under communication loss, sensor faults, false detections, and environmental change.
8. Progress toward controlled hardware experiments only after simulation results justify the transition.

## Validation Philosophy

A system intended for disaster response must be evaluated conservatively. High average accuracy in a clean dataset is insufficient.

Validation should include:

- realistic environmental noise;
- incomplete and corrupted observations;
- sensor disagreement;
- communication failures;
- agent loss;
- changing geometry;
- domain shift between simulation and reality;
- explicit measurement of confidence calibration;
- comparison with simpler baselines;
- human-in-the-loop evaluation.

Negative results, failure cases, and uncertainty should be documented openly.

## Ethical Position

RescueMind concerns decisions that may affect human survival. Consequently:

- algorithmic recommendations must remain advisory;
- final authority must remain with qualified response personnel;
- the system must support abstention when evidence is inadequate;
- performance claims must be limited to tested conditions;
- personal and biometric data must be protected;
- field testing must not endanger victims, responders, or bystanders;
- future deployment would require professional, legal, regulatory, and ethical review.

## Falling Walls Lab Narrative

The public-facing narrative can be expressed in four steps:

1. **The problem:** after an earthquake, rescuers make critical decisions with incomplete and fragmented information.
2. **The limitation:** current robotic systems can observe the scene, but observations do not automatically reveal where intervention is most urgent and feasible.
3. **The idea:** RescueMind fuses evidence from heterogeneous robots into a Living Disaster Twin and produces transparent rescue-priority recommendations.
4. **The impact:** emergency teams could spend less time interpreting disconnected data and more time acting on the locations where a life is most likely to be saved.

A concise project statement is:

> RescueMind turns distributed robotic perception into transparent disaster triage, helping rescue teams decide where to act first when every minute matters.

## Long-Term Vision

The long-term vision is a validated, interoperable framework that can connect multiple robotic platforms and sensing systems without depending on a single manufacturer or hardware configuration.

Its success should not be measured by autonomy alone. It should be measured by whether it provides reliable, understandable, and operationally useful support to the people responsible for saving lives.
