---
layout: page
title: Posts
nav: true
nav_order: 2
permalink: /posts/
---

# TinySenseNet: A Lightweight sEMG-IMU Fusion Network Using TinyML

**A Lightweight sEMG-IMU Fusion Network Using TinyML for Mechanical Arm Control in Low-Resource Settings**

* **Published in:** IEEE 2nd International Conference on Computing, Applications and Systems (COMPAS 2025)
* **Conference Location:** Kushtia, Bangladesh | **Date:** 23–24 October 2025
* **Date Added to IEEE Xplore:** February 12, 2026
* **DOI:**[10.1109/COMPAS67506.2025.11381831](https://doi.org/10.1109/COMPAS67506.2025.11381831)

---

## Overview
This paper addresses a critical gap in assistive technology access. According to the World Health Organization, an estimated 35–40 million people globally require prosthetic or orthotic services, yet fewer than one in ten can access them due to cost, availability, and limited trained personnel. In low-resource settings such as Bangladesh, where advanced rehabilitation infrastructure is scarce, affordable and clinically viable alternatives remain urgently needed.

TinySenseNet is a lightweight deep learning architecture designed for real-time robotic arm control using multimodal surface electromyography (sEMG) and inertial measurement unit (IMU) signals. Optimized for TinyML deployment on an ESP32 microcontroller, the system achieves low-latency gesture recognition within a 150 ms input window, requiring no cloud connectivity or high-performance computing hardware. The complete hardware platform, including the ESP32, Myo Armband, and servo-driven 6-DoF robotic arm, was assembled for approximately $223 — representing over 80% in cost savings compared to commercial prosthetic alternatives.

## Abstract
This paper introduces TinySenseNet, a lightweight and memory-efficient deep learning model for real-time robotic arm control using multimodal surface electromyography (sEMG) and inertial measurement unit (IMU) signals. Optimized for embedded deployment, the system processes 150 ms input windows to achieve low-latency gesture recognition with TinyML. The architecture employs depthwise 1D convolutions and an attention mechanism for efficient temporal feature extraction and robust multimodal fusion. Unlike CNNs, LSTMs, and SVMs — which are either computationally heavy, slow, or noise-sensitive — TinySenseNet offers both efficiency and resilience on low-power hardware.

Key innovations include cross-modal delay features that capture timing between muscle activation and motion onset, a confidence-based actuation mechanism with haptic feedback to improve operational safety, and a culturally adapted gesture set for enhanced usability. Evaluation across controlled lab settings, real-world noisy conditions, and clinical trials with transradial amputees at Dhaka Medical College demonstrates strong generalization. TinySenseNet achieved 97.2% accuracy for able-bodied users, 95.7% for amputees, and 93.3% in real-world scenarios, outperforming CNN, LSTM, and SVM baselines. With a model size of 1.46 KB and 23.8 ms end-to-end latency, TinySenseNet provides an affordable, scalable, and clinically viable solution for assistive robotic control in low-resource environments.

## Key Contributions

* **Compact CNN-Attention Architecture:** A depthwise separable 1D convolutional network paired with a lightweight attention gate enables real-time gesture inference on resource-constrained embedded devices. The resulting model occupies 1.46 KB — 26× smaller than LSTM counterparts — while delivering 23.8 ms latency, well within the 50 ms real-time threshold.
* **Cross-Modal Delay Feature:** A novel cross-modal feature quantifying the temporal delay between muscle activation onset (sEMG) and the corresponding physical motion (IMU). This feature captures dynamic interaction between the two sensor modalities and reduces false positives by 38% during passive arm movements.
* **Confidence-Based Actuation with Haptic Feedback:** A safety-first control mechanism that conditions servo actuation on a model confidence threshold of 0.8. When confidence falls below this threshold — indicating signal noise or ambiguous input — haptic vibration feedback is triggered via the Myo Armband rather than issuing a potentially erroneous command. This mechanism eliminated over 90% of incorrect servo activations in clinical trials.
* **Clinical Validation in a Low-Resource Context:** Unlike most prior work evaluated solely in controlled laboratory conditions, TinySenseNet was validated with transradial amputees at Dhaka Medical College under real-world noise conditions. Accuracy declined by only 4.9% from lab to field deployment, compared to declines exceeding 14% reported for CNN-based baselines.

## Performance Summary

**Gesture Recognition Accuracy (%, Mean ± SD):**
* **TinySenseNet:** 97.2 ± 1.8 (able-bodied) | 95.7 ± 2.4 (amputees) | 93.3 ± 3.1 (real-world)
* **LSTM baseline:** 95.1 ± 2.9 | 82.4 ± 3.8 | 76.2 ± 6.1
* **CNN baseline:** 92.7 ± 2.4 | 84.1 ± 4.2 | 78.5 ± 5.7
* **SVM baseline:** 86.3 ± 3.1 | 79.6 ± 5.3 | 72.8 ± 6.9

**System Efficiency:**
* **End-to-end latency:** 23.8 ms *(requirement: < 50 ms)*
* **Model size:** 1.46 KB *(requirement: < 20 KB)*
* **Power consumption:** 126.7 mW *(requirement: < 200 mW)*
* **Peak RAM usage:** 5.96 KB *(requirement: < 15 KB)*
* **Battery life:** 18 hours continuous operation

## Citation
> F. Rabby, M. R. Aknda, M. T. Mahi, S. R. Ahmed Ratul and B. Z. Shezan, "TinySenseNet: A Lightweight sEMG-IMU Fusion Network Using TinyML for Mechanical Arm Control in Low-Resource Settings," 2025 IEEE 2nd International Conference on Computing, Applications and Systems (COMPAS), Kushtia, Bangladesh, 2025, pp. 1-6, doi: 10.1109/COMPAS67506.2025.11381831. 

## Authors
* **Fazlay Rabby** — Department of EEE, University of Liberal Arts Bangladesh
* **Md. Rifat Aknda** — Department of CSE, University of Liberal Arts Bangladesh
* **Mumtahina Tasnim Mahi** — Department of EEE, University of Liberal Arts Bangladesh
* **Shaikh Radwan Ahmed Ratul** — Department of CSE, University of Liberal Arts Bangladesh
* **Bahadur Zamn Shezan** — Department of CSE, University of Liberal Arts Bangladesh
