# Container Measurement Specification
## 1 Scope and Introduction
### 1.1 Scope
This specification is a companion to the “TCG PC Platform Firmware Profile Specification” and the “Canonical Event Log Format”, which aims to expand integrity measurement and chain of trust to the container application level and specifies integrity measurement for a container.
The specification explains the concepts and usage of container measurement, the focus includes container runtime measurement and container runtime caller measurement. The scope does not include boot firmware measurement, boot loader measurement, and operating system measurement, but it requires the boot process to be measured to build a chain of trust for container measurement.
This specification defines the chain of trust for containers, container measurement register, and container event log. 

## 2 Container Measurement
### 2.1 Measurement Process
TODO

### 2.2 Chain of Trust for Container
TODO

### 2.3 Measuring Container
OCI develops the specifications for standard container image format and container runtime, both container image and container runtime SHALL be measured. The container runtime caller also SHALL be measured.

### 2.3.1 Measuring Container Image
TODO

### 2.3.2 Measuring Container Runtime
TODO

### 2.3.3 Measuring Container Runtime Caller
TODO

## 3 Container Measurement Register
TODO

## 4 Container Measurement Event Log
TODO

## Reference
TODO
