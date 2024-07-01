#data-engineering 

---

## EC2

---

## EC2 (Elastic Compute Cloud)

- Service that allows you to rent virtual computers on which you can run your own applications
- 'Elastic' because you pay by the second for what you use!
- You get control over the geographical location of your virtual computers

Before cloud computing, you'd need to put in a request for physical hardware which could take weeks to provision, now it takes seconds, with a few clicks.


### EC2 Pricing Types

**On Demand**:

Allows you to pay a fixed rate by the hour/minute/second with no commitment.

**Reserved**:

Provides you with a capacity reservation and a significant discount on the hourly charge of an instance. Locked into contract terms of 1 or 3 years.

### EC2 Pricing Types II

**Spot**:

Enables you to bid whatever price you want for instance capacity, making better savings if your applications have flexible start/end times.

**Dedicated Hosts**:

Physical EC2 server dedicated for your own use.

### EC2 - Concepts

**Image**: what is being used to build an instance (similar to Docker)

**Instance**: the machine you're creating

**Security**: security groups, key management, network interfaces

Notes: Image - essentially a sort of template that contains the software configuration required to launch your instance.

Security Group - a virtual firewall for your EC2 instances to control incoming & outgoing traffic.

Key management: You use key pairs to connect to your EC2 instances (public key is stored in .ssh directory of instance).

Network interface: Configuring stuff like port numbers and network access.


### C2 & EBS

- Elastic Block store - high performance, highly available storage for EC2
- Block-level (organised/identified in blocks) storage that can be attached to EC2 instances
- 2 options available: SSD or HDD

Notes: Block storage breaks up data into blocks and then stores those blocks as separate pieces, each with a unique identifier.

The SAN places those blocks of data wherever it is most efficient. That means it can store those blocks across different systems and each block can be configured (or partitioned) to work with different operating systems.

SSD - Solid State Drive HDD - Hard Disk Drive