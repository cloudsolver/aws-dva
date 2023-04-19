Single tenant hardware security module. #AWSService #secure 

### Details 
- A Hardware Security Module (HSM) provides secure key storage and cryptographic operations within a tamper-resistant hardware device.
- HSMs are designed to securely store cryptographic key material and use the key material without exposing it outside the cryptographic boundary of the hardware.

#Q How do you create a CloudHSM Cluster?
Clusters can contain multiple HSMs, spread across multiple [[AZ]] in a region. HSMs in a cluster are automatically synchronized and load-balanced. You receive dedicated, single-tenant access to each HSM in your cluster. Each HSM appears as a network resource in your [[VPC]].

*References*
https://aws.amazon.com/cloudhsm/
