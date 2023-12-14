# Abstract

This project implements ultra-low-power person detection by combining a PIR motion sensor and a monochrome image sensor, aimed at reducing the uptime of the power-hungry primary camera used for recording. Our approach puts the system to sleep, only activating the monochrome image sensor upon detecting motion, which then determines whether to wake up the main video camera based on the output of the person detection neural netwrok. All inferences are done at the edge using a neural network built with TensorFlow Lite Micro for Espressif Chipsets, preventing the need to offload sensitive footage to be processed on the cloud. The system is built on an off-the-shelf microcontroller: XIAO ESP32S3 Sense from SEEED Studio, powered by the dual-core Xtensa® 32-bit LX7 MCU.

# Team

* Christopher Yang
* Ananay Garg

# Required Submissions

* [Proposal](proposal)
* [Midterm Checkpoint Presentation Slides](https://docs.google.com/presentation/d/1T94JXZVgJFIabmHr8B4qjJHL0yj9VK4nZ_z1BhGEb8g/edit?usp=sharing)
* [Final Presentation Slides](https://docs.google.com/presentation/d/1U2bdHlef-A1cob_oj03bhjhw77Q7Prq9A0cpEgVMt5c/edit?usp=sharing)
* [Final Report](report)
* Demo Videos:
  * [Master Demo Video](https://www.youtube.com/watch?si=UEJS8G_MfGbzbT3T&v=8JuSE7JUu0g&feature=youtu.be)
  * [5V Demo Video](https://youtube.com/shorts/ZmwHzCMsa_o?feature=share)
  * [Wifi Streaming Demo Video](https://www.youtube.com/watch?v=NmRjGxvr8ks)
