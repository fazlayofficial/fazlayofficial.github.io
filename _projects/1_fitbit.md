---
layout: page
title: Wearable Motor Behavior Monitoring for ASD
description: A continuous, passive IMU sensing platform using Fitbit Versa 3 for ASD behavioral monitoring.
importance: 1
category: Completed
---

## Overview
Individuals with Autism Spectrum Disorder (ASD) frequently exhibit characteristic motor behaviors — repetitive movements, postural shifts, and hyperkinetic patterns — that correlate with attentional and cognitive states. This project deploys the Fitbit Versa 3 as a continuous, passive IMU sensing platform to acquire 3-axis accelerometer data during educational sessions. The data feeds a signal processing pipeline aimed at identifying motor signatures associated with attentive and inattentive behavioral states, laying the groundwork for lightweight on-device classification via TinyML.

## Research Objectives
* Discriminate attentive from inattentive behavioral states using wrist-worn 3-axis accelerometer signals.
* Characterize motor signatures associated with repetitive movement and hyperactivity during structured tasks.
* Establish a feature engineering framework suitable for TinyML deployment on resource-constrained wearable hardware.

## System Architecture

```text
┌──────────────────────────────────┐
│      Fitbit Versa 3 (Watch)      │
│  Continuous accelerometer        │
│  sampling; Binary Int16 storage  │
└───────────────┬──────────────────┘
                │  Fitbit File Transfer API
                ▼
┌──────────────────────────────────┐
│     Companion Smartphone App     │
│  Binary → CSV; HTTP POST         │
└───────────────┬──────────────────┘
                ▼
┌──────────────────────────────────┐
│       Android Server App         │
│  CSV storage on device           │
└───────────────┬──────────────────┘
                ▼
┌──────────────────────────────────┐
│    Python Analysis Pipeline      │
│  Preprocessing · EDA · Features  │
└──────────────────────────────────┘


## Components:
fitbit-app/ — Fitbit OS watch app (JavaScript); handles accelerometer sampling and binary on-device storage.
android-app/ — Android companion server; manages Fitbit File Transfer API communication and CSV conversion.
analysis/ — Jupyter Notebook pipeline; data cleaning, descriptive statistics, and signal visualization.
Data Collection
Sensor Configuration
Parameter	Value
Device	Fitbit Versa 3
Sensor	3-axis MEMS Accelerometer
Axes	X — lateral, Y — vertical, Z — anteroposterior
Scalar	500 (resolution: 0.002 m/s²)
Storage Encoding	Binary Int16 (4× efficiency over plain text)
Output Format	CSV — Timestamp, X, Y, Z
Pilot Dataset Statistics
(n = 1,080 accelerometer records)
Axis	Mean (m/s²)	Std Dev	Min	Max
X	−0.11	2.45	−14.59	8.12
Y	6.32	2.24	−6.76	17.93
Z	7.12	2.49	−18.14	15.67
Setup & Deployment
Prerequisites
Node.js (v14+) and Fitbit SDK CLI for watch app compilation.
Android Studio to build and deploy the mobile data-bridge server.
Python 3.x with pandas, numpy, and matplotlib.
Data Collection Workflow
Launch the android-fitbit-fetcher server on the paired smartphone.
Open Accel Fetcher on the Fitbit Versa 3 and press START RECORDING.
After the session, press TRANSFER TO PHONE.
In the server app, tap GET DATA and save the CSV.
Load into analysis/fitbit_analysis.ipynb for processing.
Attribution & Acknowledgments
This pipeline builds upon the binary data transfer infrastructure of fitbit-accel-fetcher by gondwanasoft.
Key modifications:
Adapted for ASD behavioral monitoring and motor signature analysis.
Custom Python signal processing and analysis pipeline.
Structured for academic reproducibility in Biomedical Signal Processing research.
Ethics & Privacy: All data collection follows institutional research ethics protocols. No raw participant data is included in this repository. Only anonymized sample records are provided for reproducibility.