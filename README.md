# HK-UrbanSpoof
This repository provides a GNSS spoofing dataset collected from realistic urban scenarios and laboratory-based warm-start synchronous spoofing attacks. The dataset is intended for research on GNSS spoofing detection, mitigation, receiver-level signal processing, and robust navigation under spoofing and urban propagation effects.

📥 IF data files download link: [TO BE ADDED]  
📩 For questions, contact: [jingxiaotao2.fang@connect.polyu.hk](mailto:jingxiaotao2.fang@connect.polyu.hk)  

---

## Overview

The dataset is designed around **synchronous spoofing attacks**. Before spoofing injection, the victim receiver is already locked onto authentic GNSS signals and outputs stable navigation solutions for at least 36 s. The spoofing signal is then injected with negligible power and gradually increased until it overshadows the authentic signal. After the initial alignment stage, the spoofer enters the takeover / pull-off stage, where the spoofing code phase and Doppler frequency are smoothly shifted according to a predefined false trajectory. The victim receiver is therefore gradually pulled away from the authentic signal and finally converges to a false navigation solution.

The dataset contains:

- 4 clean authentic GNSS IF recordings
- 17 spoofed IF recordings generated from the clean scenarios
- GNSS/INS reference trajectories as user ground truth
- Ray-tracing-based labels for urban scenarios

Currently, the released raw IF data are based on **GPS L1 only**. Multi-constellation and multi-frequency extensions, such as Galileo and BeiDou datasets, will be gradually added in future releases.

---

## Experiment Setup

The dataset is built from authentic GNSS recordings and laboratory-generated spoofing tests.

The main equipment includes:
| Equipment | Role |
|---|---|
| USRP N210 | Transmits authentic and spoofing signal streams during laboratory spoofing tests |
| LabSat 3W | Records spoofed IF signals during laboratory spoofing tests |
| NovAtel SPAN-CPT | Provides GNSS/INS reference solution for selected scenarios |
| GNSS antenna and Ublox F9P | Used for authentic signal collection and victim receiver testing |

<p align="center">
  <img src="figures/spoofing_testbed.jpg" alt="Spoofing testbed and test flow" width=600">
</p>

<p align="center">
  <em>Figure 1. Laboratory spoofing transmission testbed: (a) overall experimental flow and (b) implementation inside the shielded anechoic chamber.</em>
</p>

<p align="center">
  <img src="figures/GNSS_recording.jpg" alt="Recordings" width="600">
</p>

<p align="center">
  <em>Figure 2. Authentic GNSS signal recording platforms for urban data collection: (a) static and pedestrian scenarios and (b) vehicle scenarios.</em>
</p>


| Scenario | Description | Released data |
|---|---|---|
| Scenario 1 | Static receiver; open-sky environment | Clean IF data and spoofed IF data |
| Scenario 2 | Low-dynamic receiver; sub-urban environment | Clean IF data, spoofed IF data, receiver ground truth, and ray-tracing-based labels |
| Scenario 3 | High-dynamic receiver; urban environment | Clean IF data, spoofed IF data, receiver ground truth, and ray-tracing-based labels |
| Scenario 4 | Static receiver; simulated open-sky environment | Clean IF data and spoofed IF data |

<p align="center">
  <img src="figures/four_scenarios.jpg" alt="Scenarios" width="750">
</p>

<p align="center">
  <em>Figure 3. The test environment, victim receiver trajectory, and sky plot for (a) scenario 1, (b) scenario 2, (c) scenario 3, and (d) scenario 4. Green satellites indicate line-of-sight (LOS) reception, while orange satellites indicate multipath-affected signals identified by ray-tracing analysis.</em>
</p>


---

## IF Data Configuration

| Center frequency | Intermediate frequency | Sampling rate | Data type | Bandwidth |
|---:|---:|---:|---:|---:|
| 1580 MHz | -4.58 MHz | 58 MHz | 8 bit I/Q | 56 MHz |

---
## Clean IF Recordings

| File ID | Suggested file name | Scenario | File length (s) | Approx. raw IF size |
|---|---|---|---:|---:|
| S1_Clean | `S1_Clean.bin` | 1: Static; open sky | 90 | 10.44 GB |
| S2_Clean | `S2_Clean.bin` | 2: Low dynamic; sub-urban | 87 | 10.09 GB |
| S3_Clean | `S3_Clean.bin` | 3: High dynamic; urban | 95 | 11.02 GB |
| S4_Clean | `S4_Clean.bin` | 4: Static; open sky simulated | 118 | 13.69 GB |

---
## Spoofing Test Configuration

| File ID | Suggested file name | Scenario | Injection time (s) | Pull-off start time (s) | File length (s) | Spoofing power advantage (dB) | Target spoofing distance (m) | Approx. raw IF size |
|---|---|---|---:|---:|---:|---:|---:|---:|
| S1_T1 | `S1_T1.bin` | 1: Static; open sky | 41 | 60 | 90 | 4 | 750 | 10.44 GB |
| S1_T2 | `S1_T2.bin` | 1: Static; open sky | 41 | 60 | 90 | 11 | 750 | 10.44 GB |
| S2_T1 | `S2_T1.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 3 | 600 | 10.09 GB |
| S2_T2 | `S2_T2.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 6 | 600 | 10.09 GB |
| S2_T3 | `S2_T3.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 7 | 600 | 10.09 GB |
| S2_T4 | `S2_T4.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 1.5 | 300 | 10.09 GB |
| S2_T5 | `S2_T5.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 4 | 300 | 10.09 GB |
| S2_T6 | `S2_T6.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 6 | 300 | 10.09 GB |
| S2_T7 | `S2_T7.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 3.5 | 90 | 10.09 GB |
| S2_T8 | `S2_T8.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 7 | 90 | 10.09 GB |
| S2_T9 | `S2_T9.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 11 | 90 | 10.09 GB |
| S2_T10 | `S2_T10.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 6 | 30 | 10.09 GB |
| S2_T11 | `S2_T11.bin` | 2: Low dynamic; sub-urban | 38 | 50 | 87 | 10 | 30 | 10.09 GB |
| S3_T1 | `S3_T1.bin` | 3: High dynamic; urban | 38 | 50 | 95 | 3.5 | 600 | 11.02 GB |
| S3_T2 | `S3_T2.bin` | 3: High dynamic; urban | 38 | 50 | 95 | 5 | 600 | 11.02 GB |
| S3_T3 | `S3_T3.bin` | 3: High dynamic; urban | 38 | 50 | 95 | 6 | 600 | 11.02 GB |
| S4_T1 | `S4_T1.bin` | 4: Static; open sky simulated | 41 | 60 | 118 | 3 | 400 | 13.69 GB |

---
## Citation
📖For detailed information about the dataset, please refer to our paper：[TO BE ADDED]

If you use this dataset in your research, please cite:

```bibtex
TBC
```

---

## 17. Acknowledgement

The authors would like to thank Huang Feng, Liu Xikun, Tan Qijun, Zhou Zihong, and Li Zhengdao from the Intelligent Positioning and Navigation Laboratory for their valuable assistance with data collection.
