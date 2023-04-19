## Summary

Generic Network Virtualization Encapsulation is an encapsulated data format that is designed to overcome the limitation of VLANs segmentation through extensibility. Geneve is extensible and not limited to larger addressable protocols like VXLAN (24-bits) or STT (64-bits) making it a good fit for multi-tenant clouds.


## About

Network virtualization involved the cooperation of devices with a wide variety of capabilities such as software and hardware tunnel endpoints, transit fabrics, and centralized control clusters.

Networking has long featured a variety of tunneling, tagging, and other encapsulation mechanisms. However, the advent of network virtualization has caused a surge of renewed interest and a corresponding increase in the introduction of new protocols. The large number of protocols in this space -- for example, ranging all the way from VLANs [[IEEE.802.1Q_2018](http://ieeexplore.ieee.org/servlet/opac?punumber=8403925)] and MPLS [[RFC3031](https://datatracker.ietf.org/doc/html/rfc3031)] through the more recent VXLAN (Virtual eXtensible Local Area Network) [[RFC7348](https://datatracker.ietf.org/doc/html/rfc7348)] and NVGRE (Network Virtualization using Generic Routing Encapsulation) [[RFC7637](https://datatracker.ietf.org/doc/html/rfc7637)] -- often leads to questions about the need for new encapsulation formats and what it is about network virtualization in particular that leads to their proliferation.

## Reference

- https://datatracker.ietf.org/doc/html/rfc8926
- https://www.redhat.com/en/blog/what-geneve