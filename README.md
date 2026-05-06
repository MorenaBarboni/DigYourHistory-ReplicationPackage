# Repetition Package
This repository contains the experiment data used in the study. The package includes the artifacts produced during the experiments, and is intended to support result inspection, replication, and further analysis.

# Repository Structure
At the top level, the repository contains a folder for each of the experiment subjects:

1) `BSTPStaking`
2) `Paladin`
3) `GMMToken`
4) `Lucids`
5) `DeDudes`

Each project is organized as follows:

```
<project>/
├── contracts/
├── llm/
│   ├── candidates/
│   ├── results-<model>/
|   │   ├── prompt/
|   │   └── response/
├── sumo/
│   ├── results/mutants/
│   └── results/mutations.json/
└──transactions/
   └── transactions.json
```

## /contracts
Contains the original, unmutated smart contracts (proxy and logic contracts) for the project.

## /llm
Contains all data of LLM-based transaction selection.

* `candidates/`: Candidate transaction sets built for each mutant. Each file defines the pool of transactions from which the LLM was asked to select replay tests.

* `results-<model>/prompt/`: 
All requests sent to the LLM. Each prompt includes the context (upgrade information, transaction data, and instructions) corresponding to a specific ablation configuration.

* `results-<model>/response/`: Raw LLM responses with the relative metrics. 

## /sumo
Contains the mutants generated using the SuMo mutation testing framework.

* `results/mutants/`: Contains the mutated Solidity source files. Each file represents a variant of the original logic contract with a single injected mutation.

* `results/mutations.json`: Provides metadata for the mutants, including mutation operators, mutation locations, and injected replacement.

## /transactions
The `transactions.json` is the transaction history from which the candidate transactions were sampled.