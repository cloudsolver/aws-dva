## Summary of CAP Theorem
Theorem that states you can pick only two of the following three: Consistency, Availability and Partition Tolerance. 
## CAP Theorem Details
A partition is when there is a network fault, latency or some delay or disconnection between nodes in a distributed system. If a partition cannot be tolerated 

You can categorize a given workload, such as a database CA, AP, or CP.

-   **CP database:** When consistency and partition is a priority. [[ACID]] ensures transactions.

-   **AP database:** An AP database delivers availability and partition tolerance at the expense of consistency. When a partition occurs, all nodes remain available but those at the wrong end of a partition might return an older version of data than others. (When the partition is resolved, the AP databases typically resync the nodes to repair all inconsistencies in the system.)  
      
    
-   **CA database:** A CA database delivers consistency and availability across all nodes. It can’t do this if there is a partition between any two nodes in the system, however, and therefore can’t deliver fault tolerance.

## References

1. [IBM CAP Theorem](https://www.ibm.com/topics/cap-theorem)