---
# icon: simple/deutschetelekom

tags:
  - T Cloud Public
  - Security
  - Network
---

# Network Security Rundown

:simple-deutschetelekom:{ .deutschetelekom} **Cloud Public**

<div class="grid cards" markdown>

- __1. Security Groups__ 
- __2. VPC Firewall__
- __3. Cloud Firewall__
- __4. WAF__

</div>

## What To Use When, Where and Why?

In a recent conversation with a customer, We've realized that for those who are newcomers into T Cloud Public, some of the security services in the portfolio could be somewhat confusing. For this reason, We've created this short security rundown article in order to clarify which one you should use and where.

### Security Group

* **What:** Security Group is a virtual firewall for individual cloud resources.
* **Where:** Applied directly to an **Elastic Cloud Server** (ECS) and/or a **Relational Database Service** (RDS).
* **Why:** It is the first line of defense for an instance. Because it's stateful, if you allow inbound traffic, the outbound traffic is automatically allowed. Also, you can create nested Security Groups, where the source of the traffic could be other previously created security groups.
* **When:** Use it **always**! You should use Security Groups as your primary, most granular line of defense to control traffic based on IP, port, and protocol.

### VPC Firewall

* **What:** VPC Firewall is an access control list (ACL) for an entire VPC subnet.
* **Where:** Positioned at the **VPC subnet** boundary.
* **Why:** It acts as a "gatekeeper" for an entire VPC subnet. Being stateless, you must explicitly define rules for both inbound and outbound traffic. It provides a secondary layer of defense in case a Security Group is too permissive or misconfigured.
* **When:** Use this to **segment your network**. For example, to ensure that your database subnet can never be reached directly from the public internet, regardless of the individual instance settings.

### Cloud Firewall (CFW)

* **What:** Cloud Firewall is managed **Next-Generation Firewall** (NGFW) with deep packet inspection.
* **Where:** Positioned at the **VPC perimeter** (Internet Border) and between VPCs (East-West traffic).
* **Why:** Compared to the VPC Firewall that only checks IP addresses, ports and protocols, Cloud Firewall provides additional services like **Intrusion Prevention System** (IPS) and **Traffic Analysis**. It can detect and block complex attacks (trojans, worms, hacker tools, spyware, brute-force attacks, vulnerability exploits, SQL injection attacks, XSS attacks, and web attacks) by looking inside the data packets.
* **When:** Use this when you need comprehensive security management and **advanced threat protection** for your entire cloud environment. Important to note: an Enterprise Router is required when CFW is used in intra VPC mode (east-west).

### Web Application Firewall (WAF)

* **What:** Web Application Firewall is an **application-layer** (Layer 7) security service that examines all HTTP and HTTPS requests.
* **Where:** Positioned in front of **web applications** (HTTP/HTTPS) and **Elastic Load Balancers** (ELB).
* **Why:** It protects against Structured Query Language (SQL) injection, cross-site scripting (XSS), web shells, command and code injections, file inclusion, sensitive file access, third-party vulnerability exploits, Challenge Collapsar (CC) attacks, malicious crawlers, and cross-site request forgery (CSRF) attacks.
* **When:** Use this for any **public-facing website** or **API** to inspect the actual content of the HTTP(S) requests.

## Summary Table for Quick Reference

| Name           | Level          | Network Layer     | Used For                |
|----------------|----------------|-------------------|-------------------------|
| Security Group | Instance (NIC) | L4 (IP/Port)      | Micro-segmentation      |
| VPC Firewall   | Subnet         | L4 (IP/Port)      | Network-wide rules      |
| Cloud Firewall | VPC Perimeter  | L4 - L7 (IPS/IDS) | Advanced threat defense |
| WAF            | Application    | L7 (HTTP/HTTPS)   | Web-specific attacks    |


You can find this article on the T Cloud Public Community page: [Link](https://community.open-telekom-cloud.com/community?id=community_blog&sys_id=29e523762b93f690d15a410c2c01a010)
