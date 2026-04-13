# OPPA — Open Protein Pocket Atlas 🧬

[![Status](https://img.shields.io/badge/Status-Early_Development-orange.svg)]()
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)]()

**A pocket-centric atlas of protein binding sites for drug repurposing, polypharmacology, and off-target risk discovery.**

## 📖 Overview

OPPA (Open Protein Pocket Atlas) is an open-source computational biology platform designed to map binding pocket similarities across the proteome. Instead of comparing whole protein sequences or overall structures, OPPA isolates and compares **binding pockets**—the specific functional sites where drugs and ligands bind. 

This pocket-centric approach reveals hidden relationships between proteins, drugs, and diseases, enabling researchers to discover cross-protein binding opportunities, detect repurposing candidates, and map off-target risks.

### The Problem
Drugs are typically designed for a single protein target, but they rarely bind exclusively to that target. Because structurally distinct proteins can share highly similar binding pockets, a drug may interact with unintended proteins, leading to side effects, toxicity, or entirely new repurposing opportunities. Despite the availability of millions of predicted protein structures, the scientific community lacks a global, searchable map of binding pocket similarity. 

### The Solution: A "Google Maps" for Binding Pockets
OPPA builds a proteome-wide similarity network. Instead of asking *"Does drug X bind protein Y?"*, OPPA asks: ***"Where else does this binding pocket exist?"*** ## ✨ Key Features

* **Pocket-Centric Discovery:** Compare the geometry and physicochemical properties of binding cavities across different, seemingly unrelated proteins.
* **Proteome-Scale Mapping:** Systematic analysis scalable across thousands of protein structures.
* **Drug Repurposing Engine:** Identify existing therapeutics that may bind to similar pockets on novel disease targets.
* **Off-Target Risk Detection:** Predict unintended protein interactions early in the drug development pipeline.
* **Graph-Based Knowledge Network:** Explore complex `Drug → Pocket → Protein → Disease` relationships.
* **Open Research Infrastructure:** Built modularly for extensibility and community contributions.

## ⚙️ How OPPA Works

OPPA processes data through a streamlined, automated pipeline:

`Protein Structures` ➔ `Pocket Detection` ➔ `Feature Extraction` ➔ `Similarity Engine` ➔ `Drug/Disease Mapping` ➔ `Knowledge Graph`

### Core Components

1.  **Pocket Detection:** Uses geometry-based detection (Voronoi tessellation, alpha-sphere clustering) via `fpocket` to identify spatial cavities and output coordinates, descriptors, and rankings.
2.  **Feature Extraction:** Converts each detected pocket into a high-dimensional numerical vector representing volume, surface area, shape descriptors, hydrophobicity, and residue composition.
3.  **Similarity Engine:** Compares pocket vectors using cosine similarity, Euclidean distance, and RMSD-based structural comparisons to find structural analogues.
4.  **Contextual Mapping:** * *Drug Mapping:* Links pockets to known binding drugs to enable repurposing and off-target prediction.
    * *Disease Linking:* Connects targeted proteins to specific diseases to map therapeutic pathways.
5.  **Knowledge Graph:** Consolidates all data into a queryable Neo4j graph database.

## 🕸️ Knowledge Graph Schema

OPPA uses a highly connected graph architecture to enable network-based discovery.

* **Nodes:** `(Drug)`, `(Pocket)`, `(Protein)`, `(Disease)`
* **Edges:** * `[BINDS_TO]` (Drug → Pocket)
    * `[LOCATED_ON]` (Pocket → Protein)
    * `[SIMILAR_TO]` (Pocket ↔ Pocket)
    * `[ASSOCIATED_WITH]` (Protein → Disease)

## 🛠️ Architecture & Tech Stack

OPPA is designed as a modular research platform.

```text
oppa/
├── data-ingestion/      # Fetching and parsing PDB/AlphaFold structures
├── pocket-detection/    # fpocket integration and cavity identification
├── feature-extraction/  # Vectorization of pocket properties
├── similarity-engine/   # Vector comparison and clustering
├── graph-builder/       # Neo4j ingestion scripts
├── api/                 # FastAPI backend
├── web/                 # Svelte/React frontend
├── notebooks/           # Jupyter notebooks for research & exploration
└── docs/                # Project documentation
