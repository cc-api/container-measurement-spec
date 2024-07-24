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
TPM PCR 0~15 is defined and used as firmware and system OS measurement in UAPI Group Specification Linux TPM PCR Registry, PCR 11 and 15 are used by multiple components and there are not conflicting uses, in container measurement, these two registers can be reused to extend the measurement of container runtime and application measurement inside a container.

| PCR Index | Usage |
| --- | --- |
| 11 | The measurement of container runtime caller |
| 15 | Application inside container |

## 4 Container Measurement Event Log
### 4.1 Container Measurement Event Types
The CEL Event Content field is encoded in a TLV includes CEL, PCCLIENT_STD, IMA_TEMPLATE, IMA_TLV. Add a new TLV format CM_TLV for container integrity measurement layer.

| \<CONTENT> TLV | | | |
| --- | --- | --- | --- |
| T | CEL          | 4 | Management Content Type |
|   | PCCLIENT_STD | 5 | PC Client WG defined encapsulated structure |
|   | IMA_TEMPLATE | 7 | Linux IMA_TEMPLATE format |
|   | IMA_TLV      | 8 | IMA directly stored in CEL-TLV format |
|   | CM_TLV       | 9 | Container Measurement TLV format |
| L | |                | The length of the value (V) network byte order |
| V | |                | The value, according to the type (T) |

### 4.1.1 CM_TLV Content Layer

| CM_TLV | | |
| --- | --- | --- |
| T | CM_TLV_CONTENT_ VERSION  | Version of container runtime and container runtime callers |
|   | CM_TLV_CONTENT_CONFIG    | Configuration of container image and container runtime and container runtime callers |
|   | CM_TLV_CONTENT_LAYER     | The layer of the container image |
|   | CM_TLV_CONTENT_PROCESS   | Process binaries of container runtime and container runtime callers |
|   | CM_TLV_CONTENT_CONTAINER | The status of container lifecycle |
|   | CM_TLV_CONTENT_POD       | The status of one or more containers that run applications |
|   | CM_TLV_CONTENT_CLUSTER   | The status of the cluster |
| L | | The length of the value (V) |
| V | | The value (V) containing data of the type (T) |

## Reference
TODO
