# Multi-Service Fabric (MSF)
MSF is the architectural design of carrier-grade SDN that provides wide logical network slices with general purpose switches. We are studying architectual designs with the aim of solving the following problems we are having.

- **Immutable low-cost architecture**
	- Capable to employ any product that is most economical and suitable at each moment, for providing functions required for service provider network.
- **Unlimited and adaptive Scalability**
	- Capable to provide any level of scale needed for any use case.
- **Applicability of *Any-vendor* product**
	- Simplified functions and unified specification in order to enable to select Any-vendor's products as you like.
- **Easy Maintenance**
	- Capable to make use of small, simple and transparent equipment in order to let it easy to detect and fix the cause in case of failure.

## Design Policy
- Applicable to both data center and service provider network with the same architecture
- Use commodity hardware and open source software, open interface as much as possible
- Support carrier-grade scalability and stability by making use the autonomous and distributed IP function of the switches
- Provide service common functions on the switches and service dependent functions on servers in cloud
- In order for quick commercial deployment, it must be interoperable with existing networks using legacy protocols
- Solving limitation of commodity switches is assisted by the controller that organizes the swtich cluster as a fabric

## Architecture
- Centralized management: Network management and abstraction are performed by the controller, such as managing IP-VPN, swtich set-up, or switch clustering (switch cluster with clos-topology is treated as one logical switch).
- Distributed/Autonomous: Network routing is done among the switches.

![architecuture](/doc/img/architecture.png)

## Controller
Controller is in charge of managing both overlay and underlay network. In overlay, the controller ***adds/removes the L2/L3 slice*** (VPN) or ***creates/deletes CP*** (Connection Point with cluster network). In underlay, ***automatic configuration for switches*** (with Zero Touch Provisioning (ZTP)), and connection to the network are supported. Controller also has some functions to improve operability, reliability.

 Controller consists of three major components.
- **Fabric Controller (FC)** is managing switch fabric model and network model.
- **Element Controller (EC)** converts logical and physical information.
- **Element Manager (EM)** provides switch driver to absorb difference of vendor-specific.

![controller_architecuture](/doc/img/controller_architecture.png)

#### Fabric Controller (FC)
[Repository](https://github.com/multi-service-fabric/fabric-controller)

#### Element Controller (EC)
[Repository](https://github.com/multi-service-fabric/element-controller)

#### Element Manager (EM)
[Repository](https://github.com/multi-service-fabric/element-manager)

## Document
[Concept_Functionality_and_NetworkScale](/doc/Concept_Functionality_and_NetworkScale.pdf) (PDF) describes concept and overview, for your understanding of our project.

[Technical_Details](/doc/Technical_Details.pdf) (PDF) describes more technical information about typical functions and basic operations for using controllers.

## Support
If you have any questions, enhancement requests,  let us know with issue, or please contact `msf-contact [at] lab.ntt.co.jp`.

## Project
This project is a part of [Multi-Service Fabric](https://github.com/multi-service-fabric/).
