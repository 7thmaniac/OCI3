p[Documentation for my learning of CCI3]: #

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


### Identity and Access Management

###### What is OCI IAM?

IAM = Identity and Access Management Service

or 

Fine-grained access control

or

Role based access control

There are two key aspects to this service:

* Authorization
* Authentication

###### Authentication:

AuthN - Who are you?

###### Authorization:

AuthZ - What permissions do you have?

Authorization allows Users to be assigned one or more pre-determined roles. Each role comes with a set of permissions.

<strong>AuthZ syntax:</strong> Allow <group_name> to \<verb> <resource_type> in \<location> where \<conditions>

group_name: which group we are intended to give the authorization or permission for.

verb: Mainly there are four types of verbs or actions we can utilize.

* Manage
* Use
* Read
* Inspect

| Verb | Type of Access | Target User |
|------|----------------|-------------|
| manage | All permissions for the resource | Administrators |
| use | read + the actions vary by resource type | Resource end users |
| read | inspect + user specified meta-data | Internal auditors |
| inspect | Ability to list resources | Third-party auditors |

resource_type: It is all the available types of resources in a tenancy.

| Aggregate resource-type | Individual resource-type |
|-------------------------|--------------------------|
| all resources |                                    |
| database-family | db-systems, db-nodes, db-homes, databases |
| instance-family | instances, instance images, volume-attachments, console-histories |
| object-family | buckets, objects |
| virtual-network family | vcn, subnet, route-tables, security-lists, dhcp-options, and many more resources |
| volume-family | Volumes, volume-attachments, volume-backups |

###### Principals:

Principles are nothing but IAM entities which are allowed to interact with OCI resources. Principles can be either users using OCI tenancy or other resources and also resources themselves can be considered as principles as they can access other resources in OCI.

Principals are primarily of two types:
* IAM Users
* Resource Principals (e.g. Instance principal where this instance can make API call against storage.)

###### Groups:

Groups are a collection of users having same type of access configuaration to resources


### DEMO of creation of Compartment and Identity Domain:

##### Compartment:

Step 1: Login to your Oracle cloud account
Step 2: Navigate to the Identity and Access Management (IAM) service.

<p align="center">
    <img src="pictures/Compartment_Navigation.png">
</p>
Step 3: Click on the "Compartments" tab and then click on the "Create"

<p align="center">
    <img src="pictures/Compartment_Create.png">
</p>

Step 4: Give the Name and description of compartment and tags if you want to and then click on create compartment. at parent compartment you can choose in which compartment do you want to create the about to be created compartment. For now for simplicity's sake I chose root compartment.

<p align="center">
    <img src="pictures/Compartment_Details_and_Creation.png">
</p>


##### Identity Domain:

Step 1: Login to your Oracle cloud account.

Step 2: Navigate to the Identity and Access Management (IAM) service.

<p align="center">
    <img src="pictures/IdentityDomain_Navigation.png">
</p>

<p align="center">
    <img src="pictures/IdentityDomain_Navigation2.png">
</p>

Step 3: Click on the "Domains" tab and then click on the "Create"

<p align="center">
    <img src="pictures/IdentityDomain_Create.png">
</p>

Step 4: Give name and description of Domain and tags if you want to and then click on create Domain. At parent compartment you can choose
in which compartment do you want to create the about to be created compartment. For now for simplicity's sake I chose root compartment.

<p align="center">
    <img src="pictures/IdentityDomain_Creation.png">
</p>

### Demo on AuthN and AuthZ

Authentication is all about validating the user, who are you?
Authorization is all about what you can do, what permissions you have?

Now leveraging the SandBox_Domain created let us assign a user to the domain and create a group for the user.

###### Creating a USER

Step 1: Navigate to the Identity and Access Management (IAM) service.

<p align="Center">
    <img src="pictures/User_Creation_Step1.png">
</p>

Step 2: Navigate to Domains from Identity and Access Management service.

<p align="Center">
    <img src="pictures/User_Creation_step2.png">
</p>

Step 3: Navigate to the SandBox-Domain in the Domains.

<p align="center">
    <img src="pictures/User_Creation_Step3.png">
</p>

Step 4: In the SandBox-Domain select users tab.

<p align="center">
    <img src="pictures/User_Creation_Step4.png">
</p>

Step 5: In the users tab click on create users.

<p align="center">
    <img src="pictures/User_Creation_Step5.png">
</p>

Step 6: In the newly popped up window, fill in all the necessary user details to create the user and click on create at the bottom of the window.

<p align="center">
    <img src="pictures/User_Cretion_Step6.png">
</p>

Step 7: Once the user is created, you'll be redirected to the user page where you can view all the user details.

<p align="center">
    <img src="pictures/User_Creation_Step7.png">
</p>

###### Creating a Group

Step 1: Navigate to Domains from Identity and Access Management service.

<p align="center">
    <img src="pictures/Group_Creation_Step1.png">
</p>

Step 2: Navigate to Domains from Identity and Access Management service.

<p align="center">
    <img src="pictures/Group_Creation_Step2.png">
</p>

Step 3: Navigate to the SandBox-Domain in the Domains.

<p align="center">
    <img src="pictures/Group_Creation_Step3.png">
</p>

Step 4: In the SandBox-Domain select Group tab.

<p align="center">
    <img src="pictures/Group_Creation_Step4.png">
</p>

Step 5: In the users tab click on create Group.

<p align="center">
    <img src="pictures/Group_Creation_Step5.png">
</p>

Step 6: In the newly popped up window, fill in all the necessary user details to create Group and click on create at the bottom of the window.

<p align="center">
    <img src="pictures/Group_Creation_Step6.png">
</p>

Step 7: Once the group is created, you'll be redirected to the user page where you can view all the group details.

<p align="center">
    <img src="pictures/Group_Creation_Step7.png">
</p>

###### Now User Activation

Step 1: An activation email will be sent to the email address you have provided while creating the user with activation link.

<p align="center">
    <img src="pictures/User_Activation_Step1.png">
</p>

Step 2: Click on the activation link sent to your email address. and you'll will be redirected to set new password for the user in cloud.

<p align="center">
    <img src="pictures/User_Activation_Step2.png">
</p>

Step 3: Now the user is activate and can be accessed throught the domain sandbox.

<p align="center">
    <img src="pictures/User_Activation_Step3.png">
</p>


### Logging in as User From SandBox Domain

Step 1: At Oracle Login you'll be prompted with selection of domains.

<p align="center">
    <img src="pictures/Domain_User_Login_Step1.png">
</p>

Step 2: Select SandBox domain.

<p align="center">
    <img src="pictures/Domain_User_Login_Step2.png">
</p>

Step 3: Fill in the Username and Password, here while I created User I checked the box to use email as username hence I am using email.

<p align="center">
    <img src="pictures/Domain_User_Login_Step3.png">
</p>

Step 4: Now for the first time it will prompt you with setting up the user Authentication, User Oracle Authenticator.

<p align="center">
    <img src="pictures/Domain_User_Login_Step4.png">
</p>

Step 5: Once the Authentication is done you will login to your user account.

<p align="center">
    <img src="pictures/Domain_User_Login_Step5.png">
</p>

Now the User is authenticated but not authorised so user can login and view all the features but cannot access or perform anything in this account since he isn't authorised to do so.

So, let's provide authorization to the user.

For that we need to create policies to the group(note: policies are created for groups, compartments, or accounts not for users) OCI_Admin_Group.

###### Creating a Policy

Step 1: Navigate to Identity and Access Management services using hamburger menu.

<p align="center">
    <img src="pictures/Policy_Creation_Step1.png">
</p>

Step 2: In IAM services select Domains.

<p align="center">
    <img src="pictures/Policy_Creation_Step2.png">
</p>

Step 3: From Domain goto policies using policies tab.

<p align="center">
    <img src="pictures/Policy_Creation_Step3.png">
</p>

Step 4: Click on Create Policy.

<p align="center">
    <img src="pictures/Policy_Creation_Step4.png">
</p>

Step 5: Fill the Policy name and description for the policy and select the compartment where the policy is applicable and in the policy use cases there are several options listed, out of them I have selected Storage management.

<p align="center">
    <img src="pictures/Policy_Creation_Step5_1.png">
</p>
<p align="center">
    <img src="pictures/Policy_Creation_Step5_2.png">
</p>
<p align="center">
    <img src="pictures/Policy_Creation_Step5_3.png">
</p>

Step 6: Now select common policy templates.

<p align="center">
    <img src="pictures/Policy_Creation_Step6_1.png">
</p>

Step 7: Select the Identity Domain that this policy is being applied to.

<p align="center">
    <img src="pictures/Policy_Creation_Step7.png">
</p>

Step 8: Now select the group or groups to which this policy is applicable to.

<p align="center">
    <img src="pictures/Policy_Creation_Step8.png">
</p>

Step 9: Now select the location like compartment where the policy is being used.

<p align="center">
    <img src="pictures/Policy_Creation_Step9.png">
</p>

Step 10: Now click on create to create a policy for specific groups.

<p align="center">
    <img src="pictures/Policy_Creation_Step10.png">
</p>

Step 11: Once the policy is created you can see all the details regarding the policy in the domain.

<p align="center">
    <img src="pictures/Policy_Creation_Step11.png">
</p>

###### Working of Authorization
Even though we have created policies for the user,

User doesn't have access to do any functionality other than the compartments or tenancies where the policies are applicable.
For, example as the user logged in as specific domain user (SandBox_Domain) and navigated to other services other than where policies are applicable for the user. The User won't be able to perform any task.

Step 1: Login to the Cloud from SandBox_Domain as user created in that domain. and navigate to compute where there are no policies specified for the compartments. And click on the compute to access features or services in the compute service.

<p align="center">
    <img src="pictures/Authorization_Step1.png">
</p>

<p align="center">
    <img src="pictures/Authorization_Step2.png">
</p>

Step 2: Go into instances and create instance.

<p align="center">
    <img src="pictures/Authorization_Step3.png">
</p>

As you can see it is stating that "You don't have permission to view these resources in the compartment. Try another compartment or contanct your administrator for help.

Step 3: Navigate to Storage service.

<p align="center">
    <img src="pictures/Authorization_Step4.png">
</p>

Step 4: Click on Buckets.

<p align="center">
    <img src="pictures/Authorization_Step5.png">
</p>

Step 5: Click on Create Bucket.

<p align="center">
    <img src="pictures/Authorization_Step6.png">
</p>

Step 6: But it still prompts you with same message. This is because the policies for compartment are specified on different compartment. Now select the appropriate compartment.

<p align="center">
    <img src="pictures/Authorization_Step7.png">
</p>

Step 7: Now once the compartment is selected where the policies are specified you can perform certain actions like creation of buckets and maintenance of buckets.

<p align="center">
    <img src="pictures/Authorization_Step8.png">
</p>

Step 8: Create a bucket with default settings.

<p align="center">
    <img src="pictures/Authorization_Step9.png">
</p>

Step 9: Once the bucket is created the bucket is shown in the buckets services, and click on the bucket created where you can see all the details.

<p align="center">
    <img src="pictures/Authorization_Step10.png">
</p>

<p align="center">
    <img src="pictures/Authorization_Step11.png">
</p>


### Tenancy Setup

###### Tenancy admin:

Tenancy administrator is a person who creates a account and responsible for day to day operations.

<strong>But the best practice is to have multiple OCI admins to handle day to day operations instead of Tenancy admin.</strong> the OCI admins can be a set of users and you can group them
into a group and assign the group policies and let them operate on their own specific compartment.

<Strong>Second best practice would be to create dedicated compartments to isolate resources.</strong>
<strong>Third best practice is use of Multi Factor Authentication.</strong>

These are the 3 best practices you must follow as you setup your tenancy.

<p align="center">
    <img src="pictures/Tenancy_Setup_bestpractices.png">
</p>

###### Policies - OCI Admin

Policies written for OCI Admin group to replace the Tenancy admin are as shown in the figure.

<p align="center">
    <img src="pictures/Policies_for_OCI_Admin_Group.png">
</p>

we can also specify a specific compartment instead of tenancy in the policies mentioned in the picture.

The above mentioned are least amount of policies for OCI Admins to perform day to day operations.

### Networking

###### VCN Introduction

Virtual Cloud Network is a private software defined network you create in Oracle Cloud. You use it for secure communication. VCN is regional(it lives in a region). It is highly available, massively scalable and highly secure.

<strong>VCN:</strong> A Virtual Cloud Network (VCN) is a software-defined network that you set up in Oracle Cloud Infrastructure data center in a particular region.

<strong>Oracle Cloud Infrastructure Networking</strong> provides virtual versions of traditional network components. It uses VCN Gateway to connect to internet, or to connect to other VCN's, to connect to other networks on premesis.

Use Network security Group or Security Lists to allow or restrict traffic to your resources.

Security groups can be applied to any selected group in VCN

Security lists are applied to all resources in a subnet.

<p align="center">
    <img src="pictures/VCN2.png">
</p>

VCN's comes with default security lists that can be applied if no specific subnet security list is created.

<strong>Subnets:</strong> Subnets are subdivided containers with in a VCN. Resources hosted in a subnet uses same route table and security list and DHCP options. Each subnet has a contiguous range of IP address that do not overlap with other subnets in a VCN.

<p align="center">
    <img src="pictures/Subnet.png">
</p>

You can designate subnets as public and private when you create them.

In a public subnet the resources can connect to other resources on premesis or to internet.

<p align="center">
    <img src="pictures/Subnet_Public.png">
</p>

In a private subnet the resources can connect to other resources on premesis but not to internet.

<p align="center">
    <img src="pictures/Subnet_Private.png">
</p>

Every compute instance is created with fixed private virtual network interface card (VNIC). You can also add one or more secondary (VNIC's). A secondary VNIC can be in same VNC as primary VNIC or in different subnet in same VCN or even in different VCN.

A VNIC resides in a single subnet allows compute instance to connect to other resources in the subnets VCN.

Each VNIC has single primary ip address which doesn't change during instances lifetime.

<p align="center">
    <img src="pictures/VNIC.png">
</p>

<p align="center">
    <img src="pictures/VNIC_Connection.png">
</p>

You can add or remove additional private IP address or public IP addresses of IPV4 or IPV6.

### Demo: VCN Creation using wizard

We will create a VCN following the topology mentioned in the picture using wizard.

<p align="center">
    <img src="pictures/Topology_for_VCN_creation.png">
</p>

Lets get started!

Step 1: Login to your OCI console.

<p align="center">
    <img src="pictures/Cloud_console.png">
</p>

Step 2: To bring the networking services, Navigate to Network using navigation menu on left-hand side.

<p align="center">
    <img src="pictures/Network.png">
</p>

Step 3: Click on Virtual Cloud Network to bring up the VCN services tab.

<p align="center">
    <img src="pictures/Virtual_Cloud_Netowrk.png">
</p>

Step 4: In the VCN tab, we are provided with two options.

    
    - Create Virtual Cloud Network
    - Create Virtual Cloud Network using Wizard
    
<p align="center">
    <img src="pictures/VCN_Creation_Options.png">
</p>

And again in the start using wizared we are prompted to select one out of two possible ways.

    - Create VCN with Internet connectivity.
    - Add Internet Connectivity and Site-to-Site VPN to a VCN

As the second option is a little complex for now lets create a VCN using wizard with Internet Connectivity.

<p align="center">
    <img src="pictures/Start_VCN_with_wizard.png">
</p>

Step 5: Click on the start VCN wizard, while the option selected is Create VCN with Internet connectivity. It will take you to Configuaration page, where you need to fill details regarding the VCN that is being created and its properties.

<p align="center">
    <img src="pictures/VCN_Configuaration_pt1.png">
</p>

<p align="center">
    <img src="pictures/VCN_Configuaration_pt2.png">
</p>

<p align="center">
    <img src="pictures/VCN_Configuration_pt3.png">
</p>

Step 6: Review and create, in this section you can reverify the VCN details and once you are satisfied with the configuaration settings you can proceed with creation of VCN

<p align="center">
    <img src="pictures/VCN_Review_and_Create1.png">
</p>

<p align="center">
    <img src="pictures/VCN_Review_and_Create2.png">
</p>

<p align="center">
    <img src="pictures/VCN_Review_and_Create3.png">
</p>

<p align="center">
    <img src="pictures/VCN_Review_and_Create4.png">
</p>

<p align="center">
    <img src="pictures/VCN_Review_and_Create5.png">
</p>

<p align="center">
    <img src="pictures/VCN_Review_and_Create6.png">
</p>

Step7: Once VCN is created you can check the newly created VCN details on the VCN page.

<p align="center">
    <img src="pictures/VCN_Details.png">
</p>

### VCN Routing:

VCN uses route tables to send traffic from VCN to Internet, On-Premises Network and Peered VCN