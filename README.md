# OPPA — Open Protein Pocket Atlas 🧬

[![Status](https://img.shields.io/badge/Status-Early_Development-orange.svg)]()
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)]()

**A pocket-centric atlas of protein binding sites for drug repurposing, polypharmacology, and off-target risk discovery.**

---

# Overview

**OPPA (Open Protein Pocket Atlas)** is an open-source computational biology platform designed to map binding pocket similarities across the proteome. Instead of comparing whole protein sequences or overall structures, OPPA isolates and compares **binding pockets** — the specific functional sites where drugs and ligands bind.

This pocket-centric approach reveals hidden relationships between proteins, drugs, and diseases, enabling researchers to discover cross-protein binding opportunities, detect repurposing candidates, and map off-target risks.

---

# The Problem

Drugs are typically designed for a single protein target, but they rarely bind exclusively to that target. Because structurally distinct proteins can share highly similar binding pockets, a drug may interact with unintended proteins, leading to:

* Side effects
* Toxicity
* Off-target interactions
* Drug repurposing opportunities

Despite the availability of millions of predicted protein structures, the scientific community lacks a **global, searchable map of binding pocket similarity**.

---

# The Solution: A "Google Maps" for Binding Pockets

OPPA builds a **proteome-wide similarity network**.

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

### Drug Repurposing Engine

Identify existing therapeutics that may bind to similar pockets on novel disease targets.

### Off-Target Risk Detection

Predict unintended protein interactions early in the drug development pipeline.

### Graph-Based Knowledge Network

Explore complex **Drug → Pocket → Protein → Disease** relationships.

### Open Research Infrastructure

Built modularly for extensibility and community contributions.

---

# How OPPA Works

OPPA processes data through a streamlined pipeline:

```
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

* Detect structurally similar pockets
* Identify cross-protein binding sites

---

## Contextual Mapping

### Drug Mapping

Links pockets to known binding drugs to enable:

* Drug repurposing
* Off-target prediction

### Disease Linking

Connects targeted proteins to diseases to map therapeutic pathways.

---

## Knowledge Graph

All relationships stored in a graph database.

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

```
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

* Svelte / React

---

# Example Research Questions

With OPPA, researchers can query:

* Where else does this drug-binding pocket exist?
* Which proteins share similar druggable pockets?
* What are potential off-target interactions?
* Can this drug be repurposed?
* Which diseases are indirectly connected?

---

# Roadmap

OPPA is currently in early development.

* [x] Define architecture
* [ ] Phase 1: Pocket detection + similarity MVP
* [ ] Phase 2: Knowledge graph integration
* [ ] Phase 3: Drug mapping integration
* [ ] Phase 4: Disease linking integration
* [ ] Phase 5: REST API development
* [ ] Phase 6: Web explorer frontend
* [ ] Phase 7: Proteome-scale atlas

---

# Contributing

We are building a community-driven research infrastructure.
We welcome contributions from:

* Software engineers
* Computational biologists
* Bioinformatics researchers
* Structural biology enthusiasts
* Students

Contribution guidelines coming soon.

---

# License

Apache License 2.0 (planned)

---

# OPPA

**Open Protein Pocket Atlas**
Mapping druggable pockets across the proteome.
