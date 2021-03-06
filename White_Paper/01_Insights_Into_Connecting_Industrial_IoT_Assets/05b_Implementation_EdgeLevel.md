[< Chapter 5.1: Implementation - Production Asset Level](05a_Implementation_ProductionAssetLevel.md)

## 5 Implementation
### 5.2	Edge Level
Edge nodes, whether installed on physical industrial PCs (IPCs) or a virtual edge device in the data center, enable a scalable, secure, and reliable architecture for connecting devices from the production asset level to the edge and cloud layer. Edge computing provides the benefit of applying logic at an immediate level. Different edge modules installed on an edge device take care of the functionality needed for a successful connectivity solution.

Communication modules ensure a secure and stable connection to the assets or other integration services. For modern protocols, like OPC UA and MQTT there are already various modules available, whereas proprietary protocols require vendor-specific communication modules. Additionally, cloud communication modules actively connected to the cloud are a vital feature of the edge level. Additional modules handle other functionalities that are necessary for an integrated solution: buffering, filtering, distribution of the messages to further endpoints, or other edge modules (e.g., AI modules), and preprocessing (e.g., message enrichment). The edge layer can run complex logic modules and act as a recipient of trained or updated machine learning models, applying the new logic to incoming data and making determinations from it. Device management modules for monitoring, updating, or security activities on the device are essential to managing large-scale edge ecosystems.

Due to the high volume of telemetry data, efficient processing and forwarding are essential. Filtering, compressing, and aggregating data at the edge can help to avoid overloading the network. Missing metadata is added, data formats get standardized, and short-term network failures can be bridged via buffer functionality. Due to the high volume of data, buffering or storing the data for an extended period on the edge device is not recommended. When making filtering and compression decisions, special attention should be paid to the potential future needs of applications and model training. Optimization for efficient transmission and storage based upon current data needs might result in missing or incomplete data sets for applications in the future. Data might not be recoverable, and the future deficiency needs to be weighed against the current costs of transmission and storage.

Control messages can be received from any layer. A cloud service sends a new production job to the production asset or an AI model that analyzes the edge node’s telemetry data, modifying the current production asset settings. Also, control messages from the production asset to an upper level, like alarm messages, are possible. Besides pure forwarding, control messages can also be intended for the edge device itself, e.g., config update. Due to the intermediate level, communication flows are vitally important, and the transmission of control messages needs to be reliable and secure. As a routing agent, the edge level needs to understand commands and route them throughout the system. If a control message needs to be acknowledged, control responses need to be mapped to the corresponding requests to route it back to the right sender.

Management data related to the production asset has to be interpreted and forwarded to the desired destination. Management data concerning the edge node must be routed between the device management edge modules and device management cloud services. A monitoring component provides logs and metrics, firmware and edge modules get updated, and certificates are renewed. Also, the settings need to be saved on a central service to restore them after a device outage or transfer it to a replacement device.

The edge level is inherently extending the network to remote site locations and increasing the number of possible attack vectors. Building a secure device is challenging, but challenges can be mitigated if we adhere to the principles and practices. Below are the attributes of secured and interconnected devices.

* Hardware-based root of trust: Physical measures resist side-channel attacks and protected by hardware
* Small trusted computing base:  Private keys stored in the hardware protected vault and make it inaccessible to any software
* Compartmentalization: Hardware-enforced barriers between software components prevent a breach in one from propagating to others.
* Certificate-based authentication: Signed certificate, proven by unforgeable cryptographic key, proves the device identity and authenticity.
* Renewable security: Renewal brings the device forward to a secure state and revokes compromised assets for known vulnerabilities or security breaches
* Failure reporting: Any failure-probing security is reported to the failure analysis system

While edge devices typically provide the capability to run containerized software, the software management must be checking the base images for vulnerabilities and providing update paths that ensure smooth operations.

[Chapter 5.3: Implementation - Cloud Level >](05c_Implementation_CloudLevel.md)
