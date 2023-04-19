Network Access Control List protects [[subnet]]. It is stateless and must support ephemeral ports.

You need to open ephemeral ports 1024-65535 outbound on a web-server with 80 and 443 inbound. You do not need to open 80 and 443 on the outbound - unless you're invoking a web-request.

- Operates at the [[subnet]] level
- Supports allow rules and deny rules
- Stateless: return traffic must be explicitly allowed by rules (think of Ephemeral ports)
- Rules are evaluated in order (lowest number to highest) - first match wins.
- Automatically applies to all EC2 instances in the [[subnet]]
- Default NACL accepts everything inbound and outbound
- #BestPractice create a custom NACL instead of modifying the default
