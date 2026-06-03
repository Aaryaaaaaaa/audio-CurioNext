# Embedded Audio Processing for Edge Devices

## Overview

This project implements a lightweight embedded audio processing pipeline for environmental sound recognition. The system is designed to operate on resource-constrained edge devices such as ESP32, ARM Cortex-M microcontrollers, and low-power DSP platforms.

The pipeline performs:

- Audio ingestion and buffering
- Log-Mel Spectrogram feature extraction
- Lightweight CNN inference
- INT8 model quantization
- Low-latency environmental sound classification

The final output can be used as an acoustic context layer for downstream Audio Question Answering (Audio QA) systems.

---

## Dataset

Dataset used: ESC-10 (subset of ESC-50)

Example sound classes:

- Dog Bark
- Rain
- Helicopter
- Sea Waves
- Chainsaw
- Clock Tick
- Fire Crackling
- Sneezing
- Rooster
- Crying Baby

Audio clips are 5-second environmental recordings.

---

## Audio Processing Pipeline

Raw Audio (.wav)
↓
16 kHz Resampling
↓
Log-Mel Spectrogram Extraction
↓
40 Mel Filter Banks
↓
Lightweight CNN
↓
Environmental Sound Classification
↓
Quantized INT8 TFLite Model

---

## Model Architecture

- Input: 40 × 500 Log-Mel Spectrogram
- Conv2D (16 filters)
- Batch Normalization
- Max Pooling
- Conv2D (32 filters)
- Batch Normalization
- Max Pooling
- Global Average Pooling
- Dense (64 units)
- Dropout (0.3)
- Output Layer (10 Classes)

---

## Optimization Strategy

To simulate deployment on embedded hardware:

- TensorFlow Lite conversion
- INT8 Quantization
- Reduced model memory footprint
- Low-latency inference

---

## Results

| Metric | Value |
|----------|----------|
| Dataset | ESC-10 |
| Features | 40-bin Log-Mel Spectrogram |
| Test Accuracy | 60.0% |
| Original Model Size | 145.48 KB |
| Quantized Model Size | 15.95 KB |
| Compression | 89.03% |
| Average Inference Latency | 1.64 ms |

---

## Edge Deployment Suitability

The quantized model achieves:

- 89.03% reduction in model size
- 1.64 ms average inference latency
- Small memory footprint suitable for edge devices

These characteristics make the model suitable for deployment on resource-constrained embedded systems.


## Future Improvements

- Knowledge Distillation
- Model Pruning
- Streaming Audio Inference
- TFLite Micro Deployment on ESP32
- Acoustic Embedding Generation for Audio QA

---

## Author

Assessment submission for Embedded Audio Processing PoC.
