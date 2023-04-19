Gateway Load Balancer operates at Layer 3 of the OSI model.

### Layer 3

- Gateway: operates at [Layer 3](OSI.md#Layer%203): [IP](TCP-IP.md#IP%20Features) Protocol.
- 2 Functions: 
	- Transparent Network Gateway: Single entry/exit for all traffic.
	- Load Balancer: distributes traffic to virtual appliances.
	 ![Gateway Load Balancer| 256](gwlb.png)
	 Fig. GWLB Routes to a Target Group for inspection etc.
- #UseCase Deep packet inspection, firewalls, intrusion detection and prevention systems, deep packet inspection systems, payload manipulation.
- It maintains stickiness of flows to a specific target appliance using 5-tuple (for TCP/UDP flows) or 3-tuple (for non-TCP/UDP flows) by using the [[GENEVE]] protocol on port 6081.
- Cross-zone load balancing distributes traffic across registered targets in all enabled AZs.
- GWLB supports asymmetric flow only when the load balancer process the initial flow packet and the response flow packet is NOT routed through the load balancer.