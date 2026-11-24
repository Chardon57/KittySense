# KittySense

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Unit tests](https://github.com/Chardon57/KittySense/actions/workflows/tests.yml/badge.svg)](https://github.com/Chardon57/KittySense/actions/workflows/tests.yml)

**KittySense** is an experimental computer vision project designed to estimate a cat's pain level from a photograph, using the **Feline Grimace Scale (FGS)** as its scientific reference.

The goal is to explore how image analysis and machine learning can help assess visible facial signs associated with pain in cats, and provide an interpretable score on a scale from **0 to 10**.

> **Important:** KittySense is a research and development project, not a veterinary diagnostic tool. Its output must not be used on its own to diagnose, rule out, or treat pain. If a cat may be in pain, contact a veterinarian.

## Table of contents

- [Project overview](#project-overview)
- [The Feline Grimace Scale](#the-feline-grimace-scale)
- [How KittySense is intended to work](#how-kittysense-is-intended-to-work)
- [Project status](#project-status)
- [Getting started](#getting-started)
- [Running the tests](#running-the-tests)
- [Repository structure](#repository-structure)
- [Scientific references](#scientific-references)
- [License](#license)

## Project overview

Cats can express pain through subtle changes in facial expression. These changes may be difficult to identify consistently, particularly for people who are not trained to recognise them.

The Feline Grimace Scale provides a structured way to assess these signs. KittySense aims to investigate whether computer vision techniques can analyse a photograph, identify the relevant facial features and estimate an overall FGS-based score.

The project focuses on:

- image-based analysis of feline facial expressions;
- recognition or estimation of the facial features used by the FGS;
- calculation of a score between 0 and 10;
- reproducibility, testing and transparent documentation of the approach.

## The Feline Grimace Scale

The **Feline Grimace Scale (FGS)** is a validated instrument for assessing acute pain in cats through five facial action units:

| Facial action unit | What is assessed |
|---|---|
| Ear position | Rotation and flattening of the ears |
| Orbital tightening | Narrowing of the eyes |
| Muzzle tension | Changes in the shape and tension of the muzzle |
| Whiskers change | Changes in whisker position and appearance |
| Head position | Position of the head relative to the shoulders |

Each action unit is scored from **0 to 2**:

- **0** — action unit absent;
- **1** — moderate or uncertain presence;
- **2** — obvious presence.

The five scores are added to obtain a raw total between **0 and 10**. The original FGS publication also reports a normalised score between 0 and 1 (the raw total divided by 10). A higher score indicates more pronounced facial signs associated with pain.

KittySense aims to estimate this score from an image. The automated estimate is not equivalent to a clinical assessment: image quality, head orientation, lighting, individual morphology and other factors may affect the result.

## How KittySense is intended to work

The intended processing pipeline is:

1. **Image input** — provide a photograph showing the cat's face.
2. **Image analysis** — detect and analyse the facial regions relevant to the FGS.
3. **Feature assessment** — estimate the five FGS action-unit scores.
4. **Score calculation** — combine the action-unit scores into a total from 0 to 10.
5. **Result presentation** — display the estimated score and, where available, the contribution of each action unit.

This describes the project's objective; the exact implementation, models and processing pipeline may evolve during development.

## Project status

KittySense is under development. Model architecture, datasets, training procedures, evaluation metrics and supported image conditions will be documented here as they become available.

No clinical performance or diagnostic accuracy is claimed at this stage.

## Getting started

The repository is being set up. Installation instructions will be added once the application dependencies and execution environment have been defined.

### Requirements

The definitive software requirements will be documented here when the implementation is available.

### Installation and execution

Instructions will be added in a future update.

## Running the tests

Unit tests are run automatically by GitHub Actions on every push. The workflow is defined in:

`.github/workflows/tests.yml`

To run the test suite locally, install the project's test dependencies and execute:

```bash
python -m pytest
```

The workflow currently uses **Python 3.14.7** and expects a Python project with tests discoverable by `pytest`. Add the project's dependencies to `requirements.txt` and its tests to a `tests/` directory (or configure pytest in `pyproject.toml`) as the codebase takes shape.

The badge at the top of this README reflects the latest status of the **Unit tests** workflow. A green `passing` status means the workflow completed successfully; a failing status means that at least one workflow step failed.

## Repository structure

The structure below is a suggested starting point and will be updated to match the actual implementation.

```text
KittySense/
├── .github/
│   └── workflows/
│       └── tests.yml
├── tests/
├── README.md
└── LICENSE
```

## Scientific references

- Evangelista, M. C. et al. (2019). *Facial expressions of pain in cats: the development and validation of a Feline Grimace Scale*. Scientific Reports, 9, 19128. https://doi.org/10.1038/s41598-019-55693-8

The Feline Grimace Scale was developed and validated as an instrument for assessing acute pain in cats. The original scoring system totals the five action-unit scores on a 0–10 scale; a normalized 0–1 representation is simply that total divided by 10. KittySense uses the 0–10 representation for user-facing results to make the score easier for cat owners to interpret. Please consult the original publication and the associated FGS resources when implementing or interpreting the scale.

## License

KittySense is distributed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**. See the [`LICENSE`](LICENSE) file for the full license text.

If you modify KittySense and make it available for use over a network, the AGPL-3.0 includes source-code sharing obligations. See the license for the exact terms.
