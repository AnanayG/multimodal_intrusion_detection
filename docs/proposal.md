# Project Proposal

## 1. Motivation & Objective

Home security cameras have been increasingly popular due to their effectiveness in deterring criminal activities, including burglary and property theft. However, conventional wired surveillance systems are often difficult to set up and can result in excessive, unnecessary energy usage. In this project, we propose an ultra-low-power human detection system with a multimodal wakeup hierarchy, designed for battery-powered security cameras. This approach enables the system to enter a sleep mode and only activates upon detecting human activities, drastically reducing energy consumption.

## 2. State of the Art & Its Limitations

Battery-operated consumer surveillance products in the market today often present three main issues: privacy concerns associated with cloud-based data processing, poor battery life due to frequent system wakeups, and the requirement of a costly monthly subscription. Typically, these systems rely solely on a PIR sensor to activate the system, which triggers recording and transmission to the cloud for processing like person detection and facial recognition, alerting the user only when an anomaly is detected. However, this approach is not only inefficient due to a high rate of false positives, but also compromises privacy by uploading the footage online. Furthermore, access to many of these processing services requires a costly monthly subscription.

On the other hand, there have been attempts at performing ultra-low-power person detection at the edge. Though effective in lowering power consumption, these methods often rely on specialized hardware accelerator designs, which are costly to implement and lack flexibility for updates. There is a definite need for a more flexible, general-purpose solution that utilizes readily-available, off-the-shelf components.

## 3. Novelty & Rationale

Our approach combines an always-on PIR sensor with a low-power monochrome image sensor to perform person detection locally at the edge. This method ensures privacy by keeping all footage directly on the device. To enable person detection on resource-limited devices, we leverage tinyML techniques such as model pruning and quantization. Moreover, our system is built on off-the-shelf components and open-source libraries, which enhances its adaptability and upgradeability.

## 4. Potential Impact

If the project is successful, what difference will it make, both technically and broadly?

## 5. Challenges

What are the challenges and risks?

## 6. Requirements for Success

What skills and resources are necessary to perform the project?

## 7. Metrics of Success

What are metrics by which you would check for success?

## 8. Execution Plan

Describe the key tasks in executing your project, and in case of team project describe how will you partition the tasks.

## 9. Related Work

### 9.a. Papers

List the key papers that you have identified relating to your project idea, and describe how they related to your project. Provide references (with full citation in the References section below).

### 9.b. Datasets

List datasets that you have identified and plan to use. Provide references (with full citation in the References section below).

### 9.c. Software

List softwate that you have identified and plan to use. Provide references (with full citation in the References section below).

## 10. References

List references correspondign to citations in your text above. For papers please include full citation and URL. For datasets and software include name and URL.
