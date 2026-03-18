# AML-Capstone-Project
ML-based detection of PortScan attacks in encrypted-like traffic using CIC-IDS-2017 flow metadata. Includes preprocessing, binary labeling, train/test split, and a Random Forest baseline with feature importance on the Friday Working Hours PortScan file.
# ML-Based Detection of Encrypted Malware Traffic (CIC-IDS-2017 PortScan Subset)

This repository contains the **first stage** of a capstone project on detecting malicious activity in encrypted network traffic using only **flow-level metadata** (no payload inspection). The current work focuses on a single CIC-IDS-2017 metadata file containing benign traffic and **PortScan** attacks and implements:

- Data loading and cleaning for the PortScan CSV
- Binary label creation (benign vs PortScan)
- Train–test split with stratification
- Basic preprocessing (clipping, median imputation, scaling)
- A Random Forest baseline model
- Initial feature importance analysis

> Dataset: CIC-IDS-2017 – Friday WorkingHours Afternoon PortScan (`Friday-WorkingHours-Afternoon-PortScan.pcap_ISCX.csv`). [web:43][web:59]

---

## 1. Project Goal (Current Scope)

The overarching project goal is to detect malware and attack traffic in **encrypted channels** (e.g., TLS/HTTPS) using only metadata such as:

- Flow duration
- Packet counts and byte lengths
- Inter-arrival times (IAT)
- Packet size statistics
- TCP flag counts

Since payloads are not available when traffic is encrypted, the classifier must rely purely on these flow-level statistics. [file:1]

At this milestone, the implementation is restricted to:

- A **single attack type**: PortScan
- A **single CSV** from CIC-IDS-2017: Friday WorkingHours Afternoon PortScan
- A **single model**: Random Forest (baseline)

---

## 2. Repository Structure (Current)

```text
ml-encrypted-malware/
├── data/
│   ├── raw/
│   │   └── Friday-WorkingHours-Afternoon-PortScan.pcap_ISCX.csv
│   └── processed/        # reserved for future cleaned/split datasets
├── notebooks/
│   └── 01_eda.ipynb      # current work: EDA, preprocessing, RF baseline
├── src/                  # planned for future scripts (not yet populated)
├── results/              # planned for figures/metrics
└── venv/                 # local Python virtual environment (not committed)
