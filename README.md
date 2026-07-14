# RescueMind

> **AI-assisted disaster triage for faster, safer, and evidence-driven urban search and rescue.**

RescueMind is a research-oriented concept for a heterogeneous autonomous robotic system designed to support emergency teams after earthquakes and other structural disasters. Rather than merely collecting images or detecting isolated signs of life, RescueMind aims to transform fragmented sensor observations into a continuously updated, interpretable map of rescue priorities.

The project explores how aerial robots, ground robots, stationary sensing nodes, multimodal perception, and edge intelligence can work together to answer the most urgent operational question in disaster response:

> **Where should rescuers intervene first to maximize the probability of saving lives without exposing teams to unnecessary risk?**

## The Wall We Aim to Break

During the first critical hours after a major earthquake, rescue teams must make high-stakes decisions under severe uncertainty. Rubble is unstable, access routes are obstructed, communication infrastructure may be degraded, and available information is incomplete or contradictory.

Existing robotic platforms can provide valuable imagery, thermal measurements, environmental readings, or partial maps. However, raw data alone does not solve the central coordination problem. Emergency teams still need to determine:

- where survivors are most likely to be located;
- which signals are credible and mutually consistent;
- which areas can be reached safely;
- how rapidly local conditions are changing;
- where limited personnel and equipment should be deployed first.

RescueMind reframes search and rescue as a problem of **dynamic, uncertainty-aware disaster triage**.

## Core Concept

RescueMind envisions a heterogeneous robotic team composed of:

- **Micro aerial vehicles** for rapid exterior inspection, overhead mapping, and access through partially open structures;
- **Compact ground robots** for navigating confined, dusty, unstable, or GPS-denied environments;
- **Deployable sensor beacons** for persistent monitoring, localization support, and ad hoc communication;
- **A human-facing decision layer** that converts robotic observations into transparent, actionable recommendations.

Each platform contributes only a partial view. RescueMind combines these observations through collaborative perception and multimodal sensor fusion to construct a continuously evolving **Living Disaster Twin**: a probabilistic representation of the affected environment, its hazards, its accessible routes, and the likelihood of human presence.

## Rescue Priority Index

A central research direction is the **Rescue Priority Index (RPI)**, a dynamic score intended to support — not replace — professional rescue judgment.

For a candidate location \(x\) at time \(t\), the index may be expressed conceptually as:

\[
RPI(x,t) = f(P_h, P_v, A, S, T, U)
\]

where:

- \(P_h\): probability of human presence;
- \(P_v\): estimated probability of viable survival signs;
- \(A\): accessibility of the location;
- \(S\): structural and environmental safety;
- \(T\): estimated intervention time;
- \(U\): model and sensor uncertainty.

The RPI is not intended to make autonomous life-or-death decisions. Its purpose is to help rescue coordinators compare locations, understand the evidence behind each recommendation, and allocate resources more effectively.

## Multimodal Perception

Potential sensing modalities include:

- RGB and low-light imaging;
- thermal imaging;
- LiDAR or depth sensing;
- ultra-wideband radar;
- microphone arrays and acoustic event detection;
- carbon dioxide and air-quality measurements;
- vibration and structural-motion sensing;
- inertial, odometric, and radio-based localization.

A key scientific challenge is not simply collecting these measurements, but combining asynchronous, noisy, incomplete, and potentially conflicting observations while preserving calibrated uncertainty.

## Scientific and Engineering Challenges

RescueMind is intended as a multidisciplinary research framework spanning robotics, embedded systems, artificial intelligence, communications, and human–machine interaction.

Major challenges include:

1. **Collaborative perception in degraded environments**  
   Sharing useful information across agents despite limited bandwidth, occlusion, dust, darkness, and intermittent connectivity.

2. **Uncertainty-aware sensor fusion**  
   Distinguishing weak but meaningful evidence from false positives and explicitly representing confidence.

3. **Multi-agent exploration and task allocation**  
   Coordinating heterogeneous robots with different mobility, sensing, endurance, and risk profiles.

4. **Dynamic mapping and digital-twin updates**  
   Maintaining a spatial model as rubble shifts, routes become blocked, and hazards evolve.

5. **Edge intelligence**  
   Performing time-critical inference locally when cloud connectivity is unavailable or unsafe.

6. **Explainable decision support**  
   Presenting recommendations in a form that emergency professionals can understand, challenge, and override.

7. **Resilient communication**  
   Supporting ad hoc networking and graceful degradation when infrastructure fails.

## Proposed System Architecture

```text
┌──────────────────────────────────────────────────────────────┐
│                 Human Command Interface                      │
│  Priority map · evidence view · risk alerts · route options  │
└──────────────────────────────┬───────────────────────────────┘
                               │
┌──────────────────────────────▼───────────────────────────────┐
│              Decision-Support and Triage Layer               │
│ Rescue Priority Index · uncertainty · task recommendations   │
└──────────────────────────────┬───────────────────────────────┘
                               │
┌──────────────────────────────▼───────────────────────────────┐
│                 Living Disaster Twin                         │
│ 3D map · survivor hypotheses · hazards · access topology     │
└──────────────────────────────┬───────────────────────────────┘
                               │
┌──────────────────────────────▼───────────────────────────────┐
│        Collaborative Perception and Sensor Fusion            │
│ temporal alignment · data association · confidence fusion    │
└───────────────┬─────────────────────┬────────────────────────┘
                │                     │
      ┌─────────▼─────────┐  ┌────────▼─────────┐  ┌───────────┐
      │ Aerial Robots     │  │ Ground Robots    │  │ Beacons   │
      │ cameras · LiDAR   │  │ radar · audio    │  │ CO₂ · RF  │
      └───────────────────┘  └──────────────────┘  └───────────┘
```

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for a more detailed technical decomposition.

## Human-Centred Design Principles

RescueMind is conceived as a decision-support system, not an autonomous authority. Its design should follow several non-negotiable principles:

- **Human oversight:** trained professionals retain final authority;
- **Traceability:** every recommendation should be linked to supporting observations;
- **Uncertainty disclosure:** low-confidence predictions must be visibly distinguished from reliable evidence;
- **Fail-safe behaviour:** degraded communication or sensing should reduce functionality safely rather than create false certainty;
- **Privacy and dignity:** imagery and biometric indicators must be handled responsibly;
- **Operational realism:** evaluation must reflect dust, noise, darkness, damaged infrastructure, and unstable geometry.

## Relationship to Existing Research

RescueMind is inspired by advances in swarm robotics, collaborative perception, search-and-rescue robotics, SLAM, edge AI, and multimodal sensing. It is particularly aligned with research efforts that investigate robust cooperation among small autonomous robots in challenging environments.

Its proposed distinction is the shift from **robotic observation** to **integrated, uncertainty-aware rescue prioritization**. The research objective is not merely to deploy more sensors, but to convert distributed evidence into an interpretable operational picture for emergency decision-makers.

## Initial Research Questions

- How can heterogeneous agents share task-relevant information under severe communication constraints?
- How should contradictory thermal, acoustic, radar, and environmental evidence be fused?
- Can survivor hypotheses be ranked without concealing uncertainty or introducing unsafe automation bias?
- How can a digital twin remain useful when the environment changes faster than it can be mapped?
- Which explanations help rescuers trust correct recommendations while rejecting incorrect ones?
- How should autonomous exploration balance information gain, platform safety, and urgency?

## Development Roadmap

The project will evolve incrementally from simulation to controlled experimentation:

- **Phase 0 — Problem definition:** formalize use cases, assumptions, metrics, and ethical constraints;
- **Phase 1 — Simulation:** create a multi-agent disaster environment and baseline exploration pipeline;
- **Phase 2 — Perception prototype:** integrate selected sensing modalities and uncertainty estimates;
- **Phase 3 — Living Disaster Twin:** build a dynamic probabilistic map and survivor-hypothesis layer;
- **Phase 4 — Rescue Priority Index:** design, calibrate, and stress-test ranking mechanisms;
- **Phase 5 — Human interface:** evaluate interpretability with realistic coordination scenarios;
- **Phase 6 — Hardware validation:** test selected components on small aerial and ground platforms.

Detailed milestones are available in [ROADMAP.md](ROADMAP.md).

## Falling Walls Lab Vision

RescueMind is being developed as a candidate concept for the **Falling Walls Lab Greece 2026** under the theme:

### Breaking the Wall of Rescue Uncertainty

The three-minute pitch will focus on a simple transition:

> From robots that merely search, to intelligent systems that help rescuers decide where a life can most likely be saved.

## Current Status

**Concept and research-definition stage.**

No claim is made that the complete system described here has already been implemented or clinically/operationally validated. The repository will document assumptions, prototypes, simulations, experiments, limitations, and results as the project develops.

## Repository Structure

```text
RescueMind/
├── README.md
├── ROADMAP.md
├── CONTRIBUTING.md
└── docs/
    ├── ARCHITECTURE.md
    └── RESEARCH_VISION.md
```

Future directories may include:

```text
simulation/       Multi-agent simulation environments
perception/       Sensor-processing and fusion modules
mapping/          SLAM and Living Disaster Twin components
coordination/     Exploration and task-allocation algorithms
triage/           Rescue Priority Index models
interface/        Human command and visualization tools
tests/            Unit, integration, and scenario tests
```

## Responsible Use

RescueMind is a research concept for humanitarian disaster response. Any future real-world deployment would require extensive validation, consultation with certified emergency-response professionals, compliance with relevant aviation and safety regulations, cybersecurity assessment, and rigorous field testing.

## Author

**Panagiota Grosdouli**  
Electrical and Computer Engineering student

## Acknowledgements

The concept is motivated by the work of the international robotics, emergency-response, and scientific communities advancing autonomous systems for humanitarian applications.
