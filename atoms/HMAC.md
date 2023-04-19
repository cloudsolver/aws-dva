HMAC stands for Hash-based Message Authentication Code. It is a type of message authentication code (MAC) that is used to verify the authenticity and integrity of messages sent between two parties over an untrusted network.

HMAC works by combining a secret key with a message, and then hashing the combination using a cryptographic hash function such as SHA-256 or SHA-512. The resulting hash is then used as the message authentication code.

When the recipient of the message receives the message and the HMAC, they can use the same secret key to compute the HMAC for the received message. They can then compare the computed HMAC with the HMAC that was sent with the message. If the two HMACs match, the recipient can be sure that the message has not been tampered with during transmission and that it came from the expected sender.

HMAC is widely used in various security protocols, such as SSL/TLS, IPsec, and SSH, to provide message authentication and integrity checking. It is also used in various authentication mechanisms, such as AWS Signature Version 4, to provide secure authentication and authorization for API requests.