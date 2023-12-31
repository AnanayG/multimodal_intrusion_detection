# Project Proposal

## 1. Motivation & Objective

Home security cameras have been increasingly popular due to their effectiveness in deterring criminal activities, including burglary and property theft. However, conventional wired surveillance systems are often difficult to set up and can result in excessive, unnecessary energy usage. In this project, we propose an ultra-low-power human detection system with a multimodal wakeup hierarchy, designed for battery-powered security cameras. This approach enables the system to enter a sleep mode and only activates upon detecting human activities, drastically reducing energy consumption.

## 2. State of the Art & Its Limitations

Battery-operated consumer surveillance products in the market today often present three main issues: privacy concerns associated with cloud-based data processing, poor battery life due to frequent system wakeups, and the requirement of a costly monthly subscription. Typically, these systems rely solely on a PIR sensor to activate the system, which triggers recording and transmission to the cloud for processing like person detection and facial recognition, alerting the user only when an anomaly is detected. However, this approach is not only inefficient due to a high rate of false positives, but also compromises privacy by uploading the footage online. Furthermore, access to many of these processing services requires a costly monthly subscription.

On the other hand, there have been attempts at performing ultra-low-power person detection at the edge. Though effective in lowering power consumption, these methods often rely on specialized hardware accelerator designs, which are costly to implement and lack flexibility for updates. There is a definite need for a more flexible, general-purpose solution that utilizes readily-available, off-the-shelf components.

## 3. Novelty & Rationale

Our approach combines an always-on PIR sensor with a low-power monochrome image sensor to perform person detection locally at the edge. This method ensures privacy by keeping all footage directly on the device. To enable person detection on resource-limited devices, we leverage TinyML techniques such as model pruning and quantization. Moreover, our system is built with off-the-shelf components and open-source libraries, which enhances its adaptability and upgradeability. The multi-modal approach of our project focuses on energy rather than power optimization, with the latter done by most low-power related academic papers.

## 4. Potential Impact

Successful completion of this project will significantly reduce the power consumption in security camera systems, facilitating the design of battery-operated or energy-harvesting models that are user-friendly, energy-efficient, and privacy-conscious. Additionally, by demonstrating the effectiveness of TinyML compared to traditional cloud-based ML, this project could motivate further research and development in the emerging field of TinyML.

## 5. Challenges

As with all TinyML applications, the key challenges of this project are two: the limited processing resources for executing the neural network and the strict energy constraints of battery-powered scenarios. Person detection is a complex task usually done on powerful computers; however, our project operates with a microcontroller that has significantly less processing power and available memory by comparison, greatly limiting the size of the neural network it can support. Moreover, being battery-powered, our system must minimize the energy consumption to ensure longevity. Under such tight constraints, the challenge is to perform person detection with accuracy comparable to models run on PCs and servers, while consuming energy magnitudes lower than these machines and maintaining a reasonable latency.

## 6. Requirements for Success

The hardware required for this project is as follows:
* [XIAO ESP32S3 Sense](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) by SEEED Studio (equipped with OV2640 camera module) 
* [Arducam HM01B0 Monochrome QVGA SPI Camera Module](https://www.arducam.com/product/arducam-hm01b0-qvga-spi-camera-module-for-raspberry-pi-pico-2/)
* Generic PIR motion sensor

The skills required are the following:
* Familiarity with embedded systems development, especially with sensing and power management
* Proficiency with a variety of programming languages including C/C++ and Python (microPython and circuitPython)
* Understanding of machine learning, in particularly model optimization for deployment on a microcontroller (TinyML)

## 7. Metrics of Success

System requirements: 
* 50 wakeups/day (including false positives)
* Consumes less power on average than the state-of-the-art implementation (quantified below)
* The ability to capture footage from the colored main camera for at least 1 minute (not included in power calculations)
* The ability to transmit captured footage and live stream over the internet

Target power: [1] has a total system power consumption of 340 µW, which equates to an energy expenditure of about 30J per day. Excluding main colored camera (which is not present in the reference design), the criteria for success would be achieving an average energy draw that is less than 340 µW.

Calculations indicate that the power consumption of our system in deep sleep mode (microcontroller + PIR sensor) is approximately 250 µW. Over the span of a day, our system consumes 22J. Accounting for the standby energy consumption, our energy budget for active mode is 160 mJ/wakeup (over 50 wakeups). This serves as our target for energy consumption during uptime.

TL;DR
Target Power: 250 µW (sleep), 160 mJ/wakeup (active)

## 8. Execution Plan

Instead of relying on a single PIR sensor for wakeup, our system employs a wakeup hierarchy consisting of a PIR sensor and a monochrome image sensor to significantly reduce the false-positive rate. During most of the day, the system remains in deep sleep mode, drawing less than 300 µW of power (excluding the main recording camera). Upon detecting motion, the system is woken up to capture one or a few images by the monochrome camera and execute the neural network to detect the presence of a human in the frame(s). If a person is detected, the main recording camera will wake up to take a recording of desired length; if not, the system will revert to deep sleep mode. 

The system can be further optimized to reduce energy consumption and provide advanced features. To reduce unnecessary recording time, motion and person detection can be run intermittently during recording and terminate prematurely after not detecting the human for a certain period of time. We can also reduce the energy draw in standby mode by using a more efficient motion sensor (our current one draws 250µW on standby). Moreover, by combining some traditional CV techniques such as image cropping and frame differencing, we can reduce the input size to the NN and occasionally make a decision without needing to run the NN. And to further improve the system, we may optionally implement a facial recognition algorithm that prevents unnecessary recording of recognized individuals.

## 9. Related Work

### 9.a. Papers

Our project draws inspiration from the paper "An ultra-low-power image signal processor for hierarchical image recognition with deep neural networks"[1]. This paper focuses on optimizing the power consumption for person detection, face detection, and facial recognition using change detection and neural network techniques, which is similar to our approach. The group was able to achieve extremely low power consumption through a custom ASIC design. The paper also serves as a power consumption benchmark for our work.

### 9.b. Datasets

[Visual Wake Words Dataset](https://arxiv.org/abs/1906.05721)[2]

### 9.c. Software

* Tensorflow Lite
* [TensorFlow Lite Micro for Espressif Chipsets](https://github.com/espressif/esp-tflite-micro)
* Visual Studio Code
* Arduino IDE

## 10. References

[1] An, H. et al. (2021) ‘An ultra-low-power image signal processor for hierarchical image recognition with deep neural networks’, IEEE Journal of Solid-State Circuits, 56(4), pp. 1071–1081. doi:10.1109/jssc.2020.3041858. 

[2] Chowdhery, A. et al. (2019) Visual wake words dataset, arXiv.org. Available at: https://arxiv.org/abs/1906.05721 (Accessed: 11 November 2023). 
