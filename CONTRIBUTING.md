# Contributing to RescueMind

Thank you for your interest in RescueMind. The project is currently at the concept and research-definition stage. Contributions are welcome when they improve scientific clarity, technical reproducibility, safety, or operational relevance.

## Contribution Principles

Contributions should:

- distinguish clearly between implemented functionality, planned work, and speculative research;
- avoid unsupported claims about life-saving performance;
- document assumptions, limitations, and failure cases;
- prefer reproducible baselines over unnecessary complexity;
- treat uncertainty as a first-class output;
- preserve meaningful human oversight;
- respect privacy, safety, and responsible-research requirements.

## Useful Contribution Areas

Potential areas include:

- literature mapping and related-work summaries;
- disaster-scenario simulation;
- ROS 2 integration;
- multi-agent exploration;
- SLAM and collaborative mapping;
- thermal, acoustic, radar, or environmental sensing;
- probabilistic sensor fusion;
- uncertainty calibration;
- resilient communications;
- task allocation;
- human–robot interaction;
- visualization and interface design;
- experimental design and evaluation metrics;
- documentation and reproducibility.

## Before Opening a Pull Request

1. Describe the problem being addressed.
2. Explain the proposed approach and alternatives considered.
3. State all important assumptions.
4. Add or update tests when code is introduced.
5. Document expected failure modes.
6. Avoid presenting simulated results as real-world validation.
7. Update relevant documentation.

## Scientific Claims

Any quantitative or scientific claim should be supported by one or more of the following:

- a reproducible experiment;
- a public dataset;
- a peer-reviewed reference;
- a clearly described simulation;
- an explicitly labelled hypothesis.

Results should include the evaluation conditions and should not be generalized beyond them.

## Safety-Critical Changes

Changes related to survivor detection, risk estimation, route safety, rescue prioritization, or autonomous control require especially careful review. Such contributions should include:

- uncertainty and confidence behaviour;
- expected false-positive and false-negative modes;
- fallback or abstention behaviour;
- test scenarios involving degraded inputs;
- a clear statement of what remains under human control.

## Documentation Style

Documentation should be written in clear technical English. Define specialist terms at first use and prefer precise language over promotional language.

Use:

- “the model estimates” rather than “the system knows”;
- “candidate survivor hypothesis” rather than “confirmed survivor” unless confirmation exists;
- “decision support” rather than “autonomous decision-making” when humans retain authority;
- “tested under these conditions” rather than broad claims of reliability.

## Repository Conduct

Technical disagreement is welcome; personal attacks are not. Discussions should remain respectful, evidence-based, and focused on improving the work.
