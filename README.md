# OPPA — Open Protein Pocket Atlas 🧬

[![Status](https://img.shields.io/badge/Status-Early_Development-orange.svg)]()
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)]()

**A pocket-centric platform for exploring protein binding site similarity, drug repurposing opportunities, and off-target interactions.**

---

# Overview

**OPPA (Open Protein Pocket Atlas)** is an open-source computational biology platform designed to identify and explore similarities between protein binding pockets.

Instead of comparing entire protein sequences or overall structures, OPPA focuses on binding pockets — the functional regions where drugs and ligands interact with proteins.

By analyzing pocket-level similarity, OPPA aims to help researchers investigate potential drug repurposing opportunities, explore polypharmacology, and identify possible off-target interactions.

OPPA is currently focused on building a reproducible and scalable framework for pocket detection, representation, and similarity search.

---

# The Problem

Drugs are typically designed for a single protein target, but they rarely bind exclusively to that target. Because structurally distinct proteins can share highly similar binding pockets, a drug may interact with unintended proteins, leading to:

* Side effects
* Toxicity
* Off-target interactions
* Drug repurposing opportunities

Despite major advances in structural biology and protein structure prediction, large-scale exploration of binding pocket similarity remains fragmented across datasets, tools, and research workflows.

---

# The Vision: A Search Engine for Binding Pockets

OPPA aims to build a searchable framework for exploring functional similarity across proteins through their binding pockets.

Instead of asking:

> Does drug X bind protein Y?

OPPA asks:

> Where else does this binding pocket exist?

---

## Key Features

### Pocket-Centric Discovery

Compare the geometry and physicochemical properties of binding cavities across different, seemingly unrelated proteins.

### Proteome-Scale Mapping

Systematic analysis scalable across thousands of protein structures.

### Drug Repurposing Exploration

Identify existing therapeutics that may interact with similar pockets on novel disease targets.

### Off-Target Risk Analysis

Explore unintended protein interactions that may arise from pocket similarity.

### Graph-Based Knowledge Network

Explore complex **Drug → Pocket → Protein → Disease** relationships.

### Open Research Infrastructure

Built modularly for extensibility, reproducibility, and community contributions.

---

# Current Scope

OPPA is currently in the research and prototyping stage.

The initial objective is intentionally narrow:

* Detect protein binding pockets
* Generate comparable pocket representations
* Identify structurally similar pockets across proteins
* Evaluate similarity retrieval against known biological relationships

At this stage, OPPA does not attempt to predict binding affinity, docking outcomes, or clinical efficacy.

The focus is on building a robust pocket similarity framework that can support future drug and disease analyses.

---

# How OPPA Works

OPPA processes data through a streamlined pipeline:

```text
Protein Structures
        ↓
Pocket Detection
        ↓
Feature Extraction
        ↓
Similarity Engine
        ↓
Drug/Disease Mapping
        ↓
Knowledge Graph
```

---

# Core Components

## Pocket Detection

Uses geometry-based detection (Voronoi tessellation, alpha-sphere clustering) via **fpocket** to identify spatial cavities.

Outputs:

* Pocket coordinates
* Pocket descriptors
* Pocket rankings

---

## Feature Extraction

Each detected pocket is converted into a numerical feature vector:

* Volume
* Surface area
* Shape descriptors
* Hydrophobicity
* Residue composition

---

## Similarity Engine

Compares pocket vectors using:

* Cosine similarity
* Euclidean distance
* RMSD-based structural comparison

Purpose:

* Retrieve structurally similar pockets
* Explore potential cross-protein functional relationships
* Generate hypotheses for downstream investigation

Similarity scores should be interpreted as indicators of structural resemblance rather than evidence of biological activity.

Future directions:

* Learned pocket embeddings
* Geometric deep learning
* Graph neural networks

---

## Contextual Mapping

### Drug Mapping

Links pockets to known binding drugs to enable:

* Drug repurposing exploration
* Off-target hypothesis generation

### Disease Linking

Connects targeted proteins to diseases to map potential therapeutic pathways.

---

## Knowledge Graph

All relationships are stored in a graph database for large-scale exploration and querying.

---

# Knowledge Graph Schema

### Nodes

* Drug
* Pocket
* Protein
* Disease

### Edges

* BINDS_TO (Drug → Pocket)
* LOCATED_ON (Pocket → Protein)
* SIMILAR_TO (Pocket ↔ Pocket)
* ASSOCIATED_WITH (Protein → Disease)

---

# Architecture & Tech Stack

```text
oppa/
├── data-ingestion/      # Fetching and parsing structures
├── pocket-detection/    # fpocket integration
├── feature-extraction/  # Vectorization
├── similarity-engine/   # Pocket comparison
├── graph-builder/       # Neo4j ingestion
├── api/                 # FastAPI backend
├── web/                 # Frontend explorer
├── notebooks/           # Research experiments
└── docs/                # Documentation
```

### Core Computation

* Python
* NumPy
* SciPy
* pandas
* BioPython

### Pocket Detection

* fpocket

### Similarity Search

* scikit-learn
* FAISS (planned)

### Database

* Neo4j

### API

* FastAPI

### Frontend

* React

---

# Example Research Questions

With OPPA, researchers can explore questions such as:

* Where else does this drug-binding pocket exist?
* Which proteins share structurally similar pockets?
* What are potential off-target interactions?
* Could an existing drug be investigated for repurposing?
* Which diseases are indirectly connected through similar targets?

---

# Validation Strategy

Scientific credibility is a primary goal of the project.

The initial evaluation strategy will focus on:

* Recovery of known pocket similarities
* Benchmarking against existing pocket comparison methods
* Retrieval quality and ranking performance
* Reproducibility of results

Future releases may include biological case studies involving known off-target interactions and drug repurposing examples.

---

# Roadmap

OPPA is currently in early development.

* [x] Define architecture
* [ ] Phase 1: Pocket detection, representation, and similarity benchmark MVP
* [ ] Phase 2: Knowledge graph integration
* [ ] Phase 3: Drug mapping integration
* [ ] Phase 4: Disease linking integration
* [ ] Phase 5: REST API development
* [ ] Phase 6: Web explorer frontend
* [ ] Phase 7: Large-scale pocket atlas and public exploration platform

---

# What OPPA Is Not

OPPA is not:

* A molecular docking engine
* A protein structure prediction system
* A clinical recommendation tool
* A replacement for experimental validation

OPPA is intended as a hypothesis-generation and exploration platform for structural biology research.

---

# Contributing

We are building a community-driven research infrastructure.

We welcome contributions from:

* Software engineers
* Computational biologists
* Bioinformatics researchers
* Structural biology enthusiasts
* Machine learning researchers
* Students

Contribution guidelines coming soon.

---

# License

Apache License 2.0 (planned)

---

# OPPA

**Open Protein Pocket Atlas**

*Exploring functional similarity through protein binding pockets.*
