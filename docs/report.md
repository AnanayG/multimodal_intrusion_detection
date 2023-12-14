# Table of Contents
* Abstract
* [Introduction](#1-introduction)
* [Related Work](#2-related-work)
* [Technical Approach](#3-technical-approach)
* [Evaluation and Results](#4-evaluation-and-results)
* [Discussion and Conclusions](#5-discussion-and-conclusions)
* [References](#6-references)

# Abstract

Provide a brief overview of the project objhectives, approach, and results.

# 1. Introduction

## Motivation & Objective

Home security cameras have been increasingly popular due to their effectiveness in deterring criminal activities, including burglary and property theft. However, conventional wired surveillance systems are often difficult to set up and can result in excessive, unnecessary energy usage. In this project, we propose an ultra-low-power human detection system with a multimodal wakeup hierarchy, designed for battery-powered security cameras. This approach enables the system to remain in deep sleep and only activates upon detecting human activities, drastically reducing energy consumption.

## State of the Art & Its Limitations

Battery-operated consumer surveillance products in the market today often present three main issues: privacy concerns associated with cloud-based data processing, poor battery life due to frequent system wakeups, and the requirement of a costly monthly subscription. Typically, these systems rely solely on a PIR sensor to activate the system, which triggers recording and transmission to the cloud for processing like person detection and facial recognition, alerting the user only when an anomaly is detected. However, this approach is not only inefficient due to a high rate of false positives, but also compromises privacy by uploading the footage online. Furthermore, access to many of these processing services requires a costly monthly subscription.

On the other hand, there have been attempts at performing ultra-low-power person detection at the edge. Though effective in lowering power consumption, these methods often rely on specialized hardware accelerator designs, which are costly to implement and lack flexibility for updates. There is a definite need for a more flexible, general-purpose solution that utilizes readily-available, off-the-shelf components.

## Novelty & Rationale

Our approach combines an always-on PIR sensor with a low-power monochrome image sensor to perform person detection locally at the edge. This method ensures privacy by retaining all footage directly on the device. To enable person detection on resource-limited devices, we leverage TinyML techniques such as model pruning and quantization. Moreover, our system is built with off-the-shelf components and open-source libraries, which enhances its adaptability and upgradeability.


## Potential Impact

Successful completion of this project will demonstrate the superiority of a multimodal person detection approach compared to the traditional motion-only or vision-only approach, facilitating the design of battery-operated and/or energy-harvesting security camera models that are user-friendly, energy-efficient, and privacy-conscious. In addition, the modular design of our system allows for easy adaptation to improve the power consumption of existing vision-only person detection systems. Finally, by demonstrating the effectiveness of TinyML compared to traditional cloud-based ML, this project could motivate further research and development in the emerging field of TinyML.

## Challenges

As with all TinyML applications, the key challenges of this project are two: the limited processing resources for executing the neural network and the strict energy constraints of battery-powered scenarios. Person detection is a complex task usually done on powerful computers; however, our project operates with a microcontroller that has significantly less processing power and available memory by comparison, greatly limiting the size of the neural network it can support. Moreover, being battery-powered, our system must minimize the energy consumption to ensure longevity. Under such tight constraints, the challenge is to perform person detection with accuracy comparable to models run on PCs and servers, while consuming energy magnitudes lower than these machines and maintaining a reasonable latency.

## Requirements for Success

The hardware required for this project is as follows:
* 1x [XIAO ESP32S3 Sense](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) by SEEED Studio (equipped with OV2640 camera module) 
* 1x [XIAO ESP32S3](https://www.seeedstudio.com/XIAO-ESP32S3-p-5627.html) by SEEED Studio
* Panasonic EKMB1303111K PIR sensor

The skills required are the following:
* Familiarity with embedded systems development, especially with sensing and power management
* Proficiency low-level programming in C/C++
* Understanding of machine learning, in particularly model optimization for deployment on a microcontroller (TinyML)
* Understanding of internet protocols and web server hosting

## Metrics of Success

For our project to be deemed successful, our system needs to perform at least 50 wakeup events per day while maintaining a power consumption of less than 170 µW (which equates to 14688 mJ per day), taken from a state-of-the-art vision-only implementation [1]. In addition, for demonstration purposes, our system must have the ability to capture footage of arbitrary length through the main colored camera upon detecting a person, as well as the ability to either store the footage locally or stream it over the internet.

# 2. Related Work

Most Commercial products (Arlo Essential 2K Outdoor Security Camera XL/eufy Security S220 SoloCam) on the market use a simple wakeup hierarchy of motion to the main camera followed by ML processing off the device. These products perform processing off the device, which inherently makes this prone to security attacks and other privacy concerns. Our approach is to protect privacy by doing all the processing on the edge itself.

The Paper ‘NeuriCam: Key-Frame Video Super-Resolution and Colorization for IoT Cameras’ uses a multimodal approach using a always-on grayscale camera(1.1mW) and heavily duty cycled high resolution colored camera(100mW) top reduce the energy consumption. This approach served as a spiritual inspiration to our project as initially we wanted to add another mode of PIR sensor to this to make this wakeup hierarchy even more efficient. Later, due to interfacing limitations, we ditched out the grayscale camera and woke up the main camera directly. One of the techniques used in this paper was to use the DMA channel to transfer the data from the sensor to the MCU, which allowed them to leave the MCU central core in the sleep mode. In line with this, we in our implementation also used techniques to put the CPU core into deep sleep as much as possible.
 
There are plenty of techniques to reduce power consumption in computer vision/ML based approaches like parameter quantisation, filter compression, knowledge distillation, hierarchical neural network. These approaches were not explored in our approach as the stimulus we expect is 20-60 times/day which is very sparse. We expected the passive power to be a large component of our energy budget and the NN by itself to be a very small fraction of the total energy cost. This also turned out to be the case as detailed in the later sections in the report. 

The generation expectation of the power characteristics when trading off between resolution, color, SNR applies to the choice of the camera as well. There is existing work to help with power-aware image compression and motion detection (Link) and many commercial cameras use advanced on-device compression including neural networks to reduce the data rate. Additionally there are approaches that use RL to detect the optimal moment to capture the key-frame(Link), which can also help with power optimisation. Albeit helpful, these approaches were also not considered for our project as our active power consumption of the camera is relatively very low.

Finally, as mentioned before, our project also draws inspiration from the paper “An ultra-low-power image signal processor for hierarchical image recognition with deep neural networks”[1]. This paper focuses on optimizing the power consumption for person detection, face detection, and facial recognition using change detection and neural network techniques, which is similar to our approach. The group was able to achieve extremely low power consumption through a custom ASIC design. The paper also serves as a power consumption benchmark for our work.

# 3. Technical Approach

# 4. Evaluation and Results

# 5. Discussion and Conclusions

# 6. References
