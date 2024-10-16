[Documentation for my learning of CCI3]: #

## Getting Started

Oracle Cloud Infrastructure (OCI) is a set of complementary cloud services that enable you to build and run a range of applications and services in a highly available hosted environment. OCI provides high-performance compute capabilities (as physical hardware instances) and storage capacity in a flexible overlay virtual network that is securely accessible from your on-premises network.

### Learning about cloud basics

##### Physical Architechture

Physical architechture of OCI mainly divided into 4 categories:

1. Region
2. Availability Domain
3. Fault Domain
4. Realm

###### 1. Region:

A region is a localized geographic area. Oracle cloud regions are globally distributed data centers that provide secure, high performance, local environments. Regions allow for a business to move, build and run all workloads in the cloud from infrastructure to applications, while meeting regional data regulations.

Regions are independent of other regions and can be separeted by vast distances - across countries or even continents. Generally, you would deploy a application in a region where it is heavily used, because using nearby resources

![Region](pictures\regions.png)

###### 2. Availability Domain:

An availability domain is one or more data centers located within a region.

* Availability domains are isolated from each other.
* Availability domains are fault tolerant.
* Availability domains are very unlikely to fail simultaneously or be impacted by the failure of other availability domain.

The availability domains with in the same region are connected to each other through low-latency, high bandwidth network, which makes it possible for you to provide high availability connectivity to the internet or on-premises, and to build replicated systems in multiple availability domains for high-availability and disaster recovery.

<!-- ![Availability Domain](pictures\Availability_domain.png) -->

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-physical.htm#concepts-physical">
        <img src="pictures\Availability_domain.png" > 
    </a>

</p>

###### 3. Fault Domain:

A Fault domain is the groupin of hardware and infrastructure in a availability domain.
Each availability domain contains <strong>THREE</strong> fault domains

A Fault domain provides you anti-affinity, it lets you distribute your instaces so that not all the instances are on same physical hardware within a single availability domain.

A <strong><em>Hardware failure or compute hardware maintenance </em></strong> on one fault domain does not effect the instances of other fault domains.

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-physical.htm#concepts-physical">
        <img src="pictures/Fault_domain.png">
    </a>
</p>

###### 4. Realms:

A realm is a <strong>logical collection of regions</strong>.

Realms are <em> isolated </em> from each other and <em> do not share</em> any <strong> Data </strong>.


<strong>Note:</strong> Oracle has total of 41 regions and 9 more planned as of March 2023. and also have 12 Azure interconnected regions.


### Account and Access Concepts

###### 1. Tenancy:

When you sign up or subscribe to Oracle cloud, Oracle creates a tenancy for you.

<strong>Tenancy</Strong> is like an account, but Oracle tenancy is also a isolated and secure oracle cloud infrastructure where you can create, organize, and administer your cloud resources.

When you subscribe or signup tenancy is created in your home region, but you can subscribe to as many regions as possible. Large organizations have multiple tenancies.

###### 2. Compartments:

Compartment allows you to organize and access your cloud resources.

A compartment is a collection of related resources such as compute instances, virtual cloud networks, block volumes which can be accessed only by certain groups who have been given certain permissions by administrator.

A compartment can be thought as logical group not as physical container. When you start working with resources in the cloud, compartment works as filter for what resources your able to view and access.

When you signup or subscribe to Oracle Cloud a tenancy is created, which is your root compartment and it holds all your cloud resources. You then create additional compartments in tenancy (root compartment) and corresponding policies to control access to your cloud resources in each compartment. When you create a cloud resource such as compute instance, virtual network or block volumes you must specify to which compartment the resource belongs to.

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-account.htm#concepts-access">
        <img src="pictures/Compartment.png">
    </a>
</p>

###### 3. Identity domains and Policies:

Identity domain: 

An <em>Identity domain</em> is a container 
* For managing users and roles.
* Federating and provisioning users.
* Securing application integration through Oracle single sign on configuaration.
* OAuth administration.

Policies:

A policy is a document which specifies who can access which resource and how. You can write policies to control access to all the services with in Oracle cloud Infrastructure. Access is granted at group and compartment level, which means you can write a policy that gives a group a specific type of access within a specific compartment, or to the tenancy itself. If you give a group access to the tenancy, the group automatically gets the same type of access to all the compartments inside the tenancy. 

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-account.htm#concepts-access">
        <img src="pictures/Identity_domain_and_policies.png">
    </a>
</p>


###### 4. OCID:

Every Oracle Cloud resource has an Oracle assigned unique ID called Oracle Cloud Identifier (OCID). This OCID is provided as resource information in both console and API.

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-account.htm#concepts-access">
        <img src="pictures/OCID.png">
    </a>
</p>

###### 5. Security Zones:

Security Zones lets you be confident about your compute instances, virtual networks, object storage, data base and other resources comply according to the oracle security principles and best practices. A security zone consists of one or more compartments and a security zone recipe. When a resource is created or updated the oracle cloud infrastructure validates these operations against security zone policies in the security zone recipe. If any security zone priciple is violated, the operation is denied.

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-account.htm#concepts-access">
        <img src="pictures/Security_zone.png">
    </a>
</p>

### Core Services Concepts

###### 1. VCN:

A Virtual Cloud Network is a virtual version of traditional network—including subnets, route tables, and gateways—on which your instances run. A cloud network resides within a single region but includes all the region's availability domains.

* Each subnet you define in the cloud network can either be in a single availability domain or span across all the availability domains (recommended).
* You need to set up at least one cloud network to launch your instances. 
* You can configure the cloud network with an optional internet gateway to handle public traffic, and an optional IPSec connection or FastConnect to securely extend your on-premises network.

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-core.htm">
        <img src="pictures/VCN.png">
    </a>
</p>

###### 2. Instance:

Instance is a compute host running in the cloud. Oracle Cloud Infrastructure Compute instance allows you to utilise hosted physical hardware unlike other traditional software virtual machines, ensuring a high level of security and performance.

Image: The <em>image</em> is a template of a virtual hard drive that defines the operating system and other software for an instance, for example, Oracle Linux.

* When you launch an instance, you can define its characteristics by choosing its image.
* [Oracle provides a set of platform images](https://docs.oracle.com/iaas/Content/Compute/References/images.htm) you can use.
* You can also save an image from an instance that you have already configured to use as a template to launch more instances with the same software and customizations.

Shape: In Compute, the <em>shape</em> specifies the number of CPUs and amount of memory allocated to the instance.

* Oracle Cloud Infrastructure offers shapes to fit various computing requirements. See the [list of compute shapes](https://docs.oracle.com/iaas/Content/Compute/References/computeshapes.htm).

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-core.htm">
        <img src="pictures/Instance.png">
    </a>
</p>

###### 3. Block Volume:

A block volume is a virtual hard drive which provides persistent block storage space for oracle cloud infrastructure instances.

* A block volume can be used as physical hard drive in a computer to store data and applications.
* A block volume can be detached from an instance and attached to other instane like external physical hard drive.

<p align="center">
    <a href="https://docs.oracle.com/en-us/iaas/Content/GSG/Concepts/concepts-core.htm">
        <img src="pictures/Block_Volume.png">
    </a>
</p>


### Oracle Distributed Cloud

Oracle Distributed Cloud offers exceptional flexibility and offers.

###### 1. Public Cloud:

Oracle 100+ cloud services are available from 48 commercial, government, and sovereign regions in 24 countries.

###### 2. Multi Cloud:

Oracle Cloud Infrastructure lets you combine cloud services from multiple clouds to optimize cost, functionality and performance.

###### 3. Hybrid Cloud:

Oracle supports the widest range of hybrid cloud services, from portable devices on the edge to cloud services in customer data centers.
* Services include Oracle cloud@customer, Oracle Roving Edge Infrastructure and others.

<p align="center">
    <img src="pictures/Hybrid_cloud.png">
</p>

###### 4. Dedicated Cloud:

Dedicated Region is a complete OCI cloud region in your data center that offers the agility, scalability, and economics of OCI public cloud combined with the granular control, security and predictability of an on-premises infrastructure.

<p align="center">
    <img src="pictures/Dedicated_Region.png">
</p>

<strong>Note:</strong> All these cloud offerings are to ensure the same pricing all over the world and sovereignity and to maintain low latency of applications. According to the needs one can adopt to the above specified cloud. 
