# Ultra Low Power Person Detection with Multimodal Wakeup Hierarchy for Battery-Powered Security Cameras
This project implements person detection by combining a PIR motion sensor and a monochrome image sensor, aimed at reducing the uptime of the power-hungry primary camera used for recording. All inferences are done at the edge using a neural network built with TensorFlow Lite, applying TinyML techniques such as quantization and model pruning in order to optimize the NN model for microcontroller use. The system is built on an off-the-shelf microcontroller: XIAO ESP32S3 Sense from SEEED Studio, powered by the dual-core Xtensa® 32-bit LX7 MCU.

## Team
1. Christopher Yang
2. Ananay Garg

## Project Files

* [Website](https://ananayg.github.io/multimodal_intrusion_detection/)
* [Proposal](https://ananayg.github.io/multimodal_intrusion_detection/proposal)
* [Midterm Checkpoint Presentation Slides](https://docs.google.com/presentation/d/1T94JXZVgJFIabmHr8B4qjJHL0yj9VK4nZ_z1BhGEb8g/edit?usp=sharing)
* [Final Presentation Slides](https://docs.google.com/presentation/d/1U2bdHlef-A1cob_oj03bhjhw77Q7Prq9A0cpEgVMt5c/edit?usp=sharing)
* [Final Report](https://ananayg.github.io/multimodal_intrusion_detection/report)
* [Demo Video](https://www.youtube.com/watch?v=8JuSE7JUu0g&t=1s&ab_channel=AnanayGarg)

## Cloning the repo

This main repo contains a reference to another repo that contains all the software code. You need to do a couple of extra steps to ensure proper initilisation.
Once you clone the repo. Please do a 'git submodule init' followed by 'git submodule update' to initialise all the submodules.
