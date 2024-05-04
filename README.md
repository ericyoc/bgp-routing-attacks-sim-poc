# BGP Routing with Sub-Prefix Hijacking and BGP Prepending Attacks

This Python program simulates the Border Gateway Protocol (BGP) routing process and demonstrates two common BGP attacks: sub-prefix hijacking and BGP prepending. The program illustrates how these attacks can manipulate the routing paths and potentially intercept or manipulate traffic.

## Motivating Article
Kowalski, M., & Mazurczyk, W. (2023). Toward the mutual routing security in wide area networks: A scoping review of current threats and countermeasures. Computer Networks, 109778.

https://doi.org/10.1016/j.comnet.2023.109778.

## Border Gateway Protocol (BGP)
BGP is a standardized exterior gateway protocol designed to exchange routing and reachability information among autonomous systems (ASes) on the Internet. An autonomous system (AS) is a collection of connected Internet Protocol (IP) routing prefixes under the control of one or more network operators on behalf of a single administrative entity or domain.

BGP plays a crucial role in the Internet's routing infrastructure, as it enables the exchange of routing information between ASes, allowing them to determine the best paths to reach specific network prefixes. Without BGP, the Internet would not be able to function as a globally interconnected network.

## Program Overview
The program consists of the following main components:
- `Router` class: Represents a BGP router with its own AS number (ASN), neighbors, and routing table.
- `simulate_bgp` function: Simulates the BGP routing process by iteratively updating the routers' routing tables.
- `perform_subprefix_hijacking` function: Simulates a sub-prefix hijacking attack by advertising a more specific prefix of the target ASN.
- `perform_bgp_prepending` function: Simulates a BGP prepending attack by artificially increasing the length of the AS path.

The program demonstrates the normal BGP routing process and then simulates the two attacks separately, showing how they affect the routing tables and paths.

## Pre-Attack
![](https://github.com/ericyoc/bgp-routing-attacks-sim-poc/blob/main/pre_attack_bgp.jpg)

## Sub-Prefix Hijacking Attack
In a sub-prefix hijacking attack, the attacker (AS4 in the example) advertises a more specific prefix of the target ASN (AS1). This causes other routers to prefer the more specific route advertised by the attacker, effectively hijacking the traffic destined for the target ASN.

![](https://github.com/ericyoc/bgp-routing-attacks-sim-poc/blob/main/post_sub-prefix_hijack.jpg)

## BGP Prepending Attack
In a BGP prepending attack, the prepender (AS2 in the example) artificially increases the length of the AS path by prepending its own ASN multiple times. This makes the route appear less attractive to other routers, discouraging them from using the prepender as a transit point.

![](https://github.com/ericyoc/bgp-routing-attacks-sim-poc/blob/main/post_prepending_attack.jpg)

## BGP History and Security
BGP was first introduced in the early 1990s and has since undergone several revisions and improvements. The current version of BGP is BGP-4, which is defined in RFC 4271.

Over the years, various security vulnerabilities and attacks have been identified in BGP, including prefix hijacking, route leaks, and BGP session hijacking. To mitigate these risks, several security measures and best practices have been developed, such as:
- Route filtering: Implementing strict filters to prevent the propagation of invalid or malicious routes.
- RPKI (Resource Public Key Infrastructure): A security framework that allows the validation of BGP route origins using cryptographic signatures.
- BGPsec: An extension to BGP that provides cryptographic protection for BGP routing messages.

Additionally, BGP routers can be configured to use MD5 authentication between neighbors to ensure the integrity and authenticity of BGP messages exchanged between them. This helps prevent unauthorized entities from injecting fraudulent routing information into the BGP system.

## Conclusion
This BGP routing simulator program demonstrates the normal operation of BGP and highlights the potential impact of sub-prefix hijacking and BGP prepending attacks on the routing process. By understanding these attacks and implementing appropriate security measures, network operators can help protect the integrity and stability of the Internet's routing infrastructure.
