
class: topicslide

.topic[

# Pouta Cloud Course

Tewodros Deneke,  Cloud System Specialist

Alvaro Gonzalez,  Cloud System Specialist
]

---

# Schedule

|When|What||
|:-:|:-:|:-|
| 9:00-10:30 | Introduction | Cloud computing basics |
||| Cloud service landscape |
||| OpenStack |
||| Pouta virtual resource basics |
| 10:30-10:45 | Coffee break |☕|
| 10:45-12:00 | Exercises ||
| 12:00-13:00 | Lunch |🍽️|
| 13:00-14:30 | Theory | cPouta vs. ePouta |
||| Storage |
||| Pouta management |
||| Practical information, installing software |
| 14:30-14:45 | Coffee break |☕|
| 14:45-16:00 | Exercises | |
| 16:00-16:15 | Closing | Documentation and contact info |

---

# Introduction

.bubble.bubble-bottom-left[
"This course gives you a practical introduction for using CSC's cloud services Pouta"
]

.footnote[If something **makes no sense**, you want to make a **question** or **correction**, **Please interrupt** and make your comment]

## 🙂

* The **Pouta Cloud** is CSC’s Infrastructure as a Service ([IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)) offering. Based on [OpenStack](https://www.openstack.org/).
  * Allows running Virtual Machines (VMs) on CSC’s Data Center infrastructure. Grants users **full control** over the OS, middleware and run time environments. On the flip side, users are responsible **manage** and **secure** their VMs.
* Provides an IaaS cloud environment for your **sensitive data** processing (ePouta).

---
class: topicslide

.topic[

# Cloud Basics

]

---

# Cloud computing

.container[
.col66[

.bubble.bubble-bottom-left[
"Is one such model for enabling convenient, **on-demand** network access to a **shared pool** of configurable computing resources. Resources like networks, servers, storage, applications, and services. They can be **rapidly** provisioned and released with **minimal management** effort or service provider interaction”[1].footnote[[1] <https://en.wikipedia.org/wiki/Cloud_computing>]
]

## 🙂

]

.col[![:scale 90%, cloud](/csc-cloud/img/cloud.png)]
]

---

# Cloud computing characteristics

.container[.col[

* Cloud Computing has 5 essential characteristics
  * On-demand self-service
  * Broad network access
  * Resource pooling
  * Rapid elasticity
  * Measured Service

* The trend so far
  * Colocation: rented space in shared facility, user-configured, user-managed
  * Virtualization: user-configured, provider-managed
  * Containerization: automatically managed and configured infrastructure

]
.col[![Cloud Computing Characteristics](/csc-cloud/img/cloud_Computing_characteristics.drawio.svg)]
]

---


# Cloud deployment models

.center[![:scale 60%, cloud deployment models](/csc-cloud/img/cloud_deployment_models.drawio.svg)]

---

# Cloud computing wishlist

.center[![Cloud computing wishlist](/csc-cloud/img/cloud_computing_wishlist.drawio.svg)]

---

# Cloud computing challenges

.center[![Cloud Computing Challenges](/csc-cloud/img/cloud_computing_challenges.drawio.svg)]

---
class: topicslide

.topic[

# Cloud computing Landscape

]

---

# Cloud computing "As A Service"

.center[![:scale 60%, Cloud computing Landscape](/csc-cloud/img/cloud_computing_landscape.drawio.svg)]

---

# Cloud Service Landscape: IaaS

.container[
.col[

* Infrastructure as a Service:

> "The network and hardware **infrastructure** is offered to you, the user, so you can just worry about running your Operating system of choice, the Software you need to run and nothing else".

  * No worries about: Hardware issues
  * Flexibility in scaling up and down
  * Control via API
  * Software defined network (**SDN**)

]
.col[
.center[![:scale 35%, IaaS](/csc-cloud/img/IaaS.drawio.svg)]]
]

---

# Cloud Service Landscape: PaaS

.container[.col[![:scale 80%, PaaS](/csc-cloud/img/PaaS.drawio.svg)]
.col[

* Platform as a Service:

  > "The network and hardware infrastructure, plus the Operating System and thge middleware is offered as a **platform** to you, the user, so you can just worry about installing, configuring and using the Software and nothing else".

  * No worries about: Hardware issues, Operation systems patches, etc.
  * Security: Containers allow software from independent teams of people to run isolated, even though they run in the same hardware.
  * Control via API
  * QoS: Orchestration services provide assured resources

]]

---

# Cloud Service Landscape: SaaS

.container[.col[

* Software as a Service

  > "Software is offered to you, the user, so you can just worry about using the Software and nothing else."

  * No worries, only use the software.
  * Examples:
     * myCSC
     * Web mail
     * Web Office platforms
     * ...
]
.col[.center[
![:scale 35%, Saas](/csc-cloud/img/SaaS.drawio.svg)
    ]]
]

---

# Typical IaaS Cloud Setup

.center[![cPouta Cloud Setup](/csc-cloud/img/cpouta_cloud_setup.drawio.svg)]

---

# Secure Cloud Setup

.center[![ePouta Cloud Setup](/csc-cloud/img/epouta_cloud_setup.drawio.svg)]

---

# CSC’s Cloud Computing Services

|<font size="6">cPouta</font>|<font size="6">ePouta</font>|<font size="6">Rahti</font>|
|:-|:-|:-|
|Community IaaS Cloud|Community IaaS Cloud|Community PaaS Cloud leveraging containers|
|General purpose|**Sensitive data**|General purpose HTTP(s) applications|
|Services accessible over internet|Accessible only from customer network|Services accessible over internet|
|Powered by OpenStack|Powered by OpenStack|Powered by OpenShift OKD|
|ISO27001 Certified|ISO27001 Certified||
|In Production since 2013|In Production since 2013|In Open Beta\*|
|Web UI, CLI & REST APIs supported|Web UI, CLI & REST APIs supported|Web UI, CLI & REST APIs supported|
|![:scale 20%, OpenStack](/img/openStack.png)|![:scale 20%, OpenStack](/img/openStack.png)|![:scale 20%, OpenStack](/img/openshift-logo.png)|

---
layout: false
class: topicslide

.topic[

# Basics of VMs

]

---

# OpenStack software

.container[.col66[

* CSC’s cPouta/ePouta cloud services are powered by OpenStack.
  * Current OpenStack version used by Pouta services is Queens
* OpenStack is a cloud software that allows end user to create  and use their VM instances, networks and storage.
* Virtualization is a technology that allows the creation of virtual computer resources such as CPU, storage, network, etc.
* Fast moving open source project with backing from industrial giants like: AT&T, Red Hat, IBM, Intel, HP etc.
* Flexible architecture which may support different types of scales.
* Used by many organizations from research institutes to service/content providers.
* Large customer base augments better availability of expertise, support and chances of continuity.
* Supports Web UI, CLI and REST Interfaces
]
.col[
.right[![:scale 90%, OpenStack](/csc-cloud/img/openStack.png)]
]]

---

# OpenStack Architecture

.center[![:scale 70%, Artichecture](/csc-cloud/img/artichecture.png)]

---

# OpenStack WebUI

.container[.col[
.center[![:scale 80%, WebUI](/csc-cloud/img/webui1.png)
![:scale 80%, WebUI](/csc-cloud/img/webui2.png)
]]
.col[
.center[![:scale 80%, WebUI](/csc-cloud/img/webui3.png)
![:scale 80%, WebUI](/csc-cloud/img/webui4.png)
]]]

---

# OpenStack CLI

.container[.col60[
.center[![:scale 90%, CLI](/csc-cloud/img/cli2.png)
]]
.col[
.center[![:scale 95%, CLI](/csc-cloud/img/cli3.png)]
.center[![:scale 95%, CLI](/csc-cloud/img/cli1.png)]
]]

---
layout: false
class: topicslide

.topic[

# Pouta

]

---

# Resources you get from Pouta Clouds

.center[![:scale 65%, Typical resources you get from Pouta clouds](/csc-cloud/img/typical_Resources_You_get_from_Pouta_Clouds.png)]

.footnote[*S3/Switf API access

*Network address translation]

---

# cPouta ☁️

* General purpose service.
* Serving cloud computing needs of Finnish research institutes and universities since 2013.
* VMs and Control plane can be accessed via **public** internet.
* Customers may decide access to VMs by creating firewall rules at OpenStack level known as “Security Groups”.
* Could be used for hosting:
  * Custom services such as Web servers, File servers, load balancer etc.,
  * Scientific applications,
  * Course computer resources for students,
  * Research Data Sharing etc.

---

# ePouta ☁️🔒

* **Sensitive Data** related services.
* Complete Isolation of VMs from rest of the world and other ePouta customers.
  * A (virtual) **private** data center.
* VMs accessible only from customer network.
* Virtual **Private** Cloud: Optical Private Network (OPN) or MPLS[1].footnote[[1] <https://en.wikipedia.org/wiki/Multiprotocol_Label_Switching>] VPN connection between the end customer and ePouta VM instances.
* Could be used for hosting:
  * Scientific applications dealing with **sensitive data**,
  * **Sensitive Data** Sharing, Archiving etc.

---

# cPouta/ePouta

.stripetable[
||cPouta public Cloud|ePouta private Cloud|
|:-:|:-:|:-:|
|Usage|General purpose| Sensitive Data|
|Network connection|Public Internet|Private OPN/MPLS|
|ISO27001 certification|✔️|✔️|
|VAHTI 2010 certification|✔️|✔️|
|Firewall, LB, VM installation, VM auto-recovery, Backups|Self-service|Self-service|
|Supported Operating Systems|All (commercial OSs require a license)|All (commercial OSs require a license)|
|OpenStack Version|Queens|Queens|
|GPU|✔️|✔️|
|Service availability target|99%|99%|
|Allas (S3/Swift) Object Storage|✔️|❌|
]

---

# ePouta Connection

.center[![:scale 50%, ePouta Connection](/csc-cloud/img/epouta_connection.png)]

Typical VM connections between ePouta and customer’s network. Such connections are normally coordinated between CSC’s cloud team, Funet[1].footnote[[1] <https://en.wikipedia.org/wiki/FUNET>] and customers IT department for initial setup.


---

# Pouta: Hardware Flavor Options

.center[![:scale 60%, Pouta hardware options](/csc-cloud/img/pouta_hardware_options.drawio.svg)]

---


# Pouta VM Flavors (extract)

.footnote[Full list of flavor available at <https://docs.csc.fi/cloud/pouta/vm-flavors-and-billing/>

Billing units and Pricing at <https://research.csc.fi/pricing>

(1 BU ≈ 0.021 EUR)]

.stripetable[
|Flavor|Cores|Memory|Disk(root)|Disk(ephemeral)|Disk(total)|Memory/core|Billing Units/h|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|standard.tiny|1|1GiB|80GB|0GB|80GB|1GiB|0.25|
|io.70GB|2|10GiB|20GB|70GB|90GB|5GiB|3|
|hpc.4.5core|5|20GiB|80GB|0GB|80GB|4GiB|6|
|standard.3xlarge|8|60GiB|80GB|0GB|80GB|7.5GiB|16|
|io.700GB|16|75GiB|20GB|700GB|720GB|4.7GiB|24|
|hpc-gen4.80core|80|335GiB|80GB|0GB|80GB|4.2GiB|120|
|hpc.5.128core|128|443GiB|80GB|0GB|80GB|3.46GiB|180|
|tb.3.1470RAM|80|1402GiB|80GB|2500GB|2580GB|17.2GiB|320|
]

---

# GPU Flavors in Pouta

.container[.col70[

* GPU VM flavors provide high performance computing leveraging **General-purpose** computing on graphics processing units (GPGPUs). PCI **passthrough** is used for performance.

|Flavor family|GPU Card|CPU|SSD|
|:-:|:-:|:-:|:-:|
|GPU 1.*|NVIDIA Tesla P100|Intel®️ Xeon®️|✔️|
|GPU 2.*|NVIDIA Tesla V100|Intel®️ Xeon®️|✔️|
|GPU 3.*|NVIDIA Ampere A100 [1]|AMD®️ EPYC®️|✔️|

* CSC’s Code Optimization Service is available to help you coding:
  * <https://research.csc.fi/optimization-service>
* GPGPUs are also available in the batch system on Puhti:
  * <https://docs.csc.fi/#computing/system/>

].col[
.right[![GPU card](/csc-cloud/img/gpu.drawio.svg)]

\[1\] With Multi-Instance GPU (MIG) support
]]

* OS images pre installed with latest [CUDA](<https://en.wikipedia.org/wiki/CUDA>) version are available. (You may also use your own OS images by installing required libraries yourself).
---
# cPouta Cloud Setup

.center[![cPouta Cloud Setup](/csc-cloud/img/cpouta_cloud_setup.drawio.svg)]

---

# ePouta Cloud Setup

.center[![ePouta Cloud Setup](/csc-cloud/img/epouta_cloud_setup.drawio.svg)]

"A private data center"

---

# Pouta Web UI

.container[.col[
.center[![:scale 80%, WebUI](/csc-cloud/img/webui1.png)
![:scale 80%, WebUI](/csc-cloud/img/webui2.png)
]]
.col[
.center[![:scale 80%, WebUI](/csc-cloud/img/webui3.png)
![:scale 80%, WebUI](/csc-cloud/img/webui4.png)
]]]

---

# Pouta CLI

.container[.col60[
.center[![:scale 90%, CLI](/csc-cloud/img/cli2.png)
]]
.col[
.center[![:scale 95%, CLI](/csc-cloud/img/cli3.png)]
.center[![:scale 95%, CLI](/csc-cloud/img/cli1.png)]
]]

---

# Workflow for Creating Resources I

.center[![:scale 60%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources.png)]

---

# Workflow for Creating Resources II

.center[![:scale 60%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources2.png)]

---

# Workflow for Creating Resources III

.center[![:scale 60%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources3.png)]

---

# Workflow for Creating Resources IV

.center[![:scale 60%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources4.png)]
---
layout: false
class: topicslide

.topic[

# How-tos

## For the exercises

]

---

# [Pouta] Creating a SSH Key pair

.container[.col[

From the WebInterface, navigate to:

* **Compute>Access and Security>Key Pairs**

Click on create Key Pair, name key as
**lastname_firstname**

].col[
.center[![:scale 90%](/csc-cloud/img/access_security.png)]
]]

.container[.col[

Download the *private* key and store it safely. It **will not** be possible to download the private key again.

The public key will be stored in Pouta.

It is also possible to create the key using the command line tool `ssh-keygen` and then upload the public key to Pouta.

]
.col[.center[![:scale 80%](/csc-cloud/img/create_key_pair.png)]
]]

---

# [Pouta] Storing a (private) Key

.container[.col[
    ![UNIX](/csc-cloud/img/unix.png)

#### Linux and Mac OS X

1. Create `.ssh` directory in `$HOME` if it is not there already, copy the key pair to the `.ssh` directory, and fix permissions.

  ```bash
  mkdir -p  .ssh
  chmod 700 .ssh
  mv ~/Downloads/yourkey.pem ~/.ssh/
  chmod 400 .ssh/yourkey.pem
  ```

1. Protect key with passphrase (Optional)

  ```bash
  ssh-keygen -p -f yourkey.pem
  ```

]

.col[
    ![Win](/csc-cloud/img/win.png)

#### Windows

1. Download Putty and Puttygen tools if you don’t have them
1. Load your private key (`yourkey.pem`) into puttygen and change it to .ppk format
1. Open Putty, load .ppk file under Connection | SSH | Auth | Private key file for authentication
    1. Provide user name cloud-user
    1. Provide the password which you added to Puttygen (Optional)

]]

---

# [Pouta] Security groups

A Security Group defines a set of cloud level firewall rules for filtering traffic, typically inbound, but also outbound.

.container[.col70[

* By default a "Security Group" blocks all incoming connections to your VM,
  * and allows all outgoing connections.
* VM level firewall rules are still possible as an extra layer of security.
* One security group includes one or several several “rules”.
* One security group can be assigned to one or several Virtual machines.
* One Virtual machine can be assigned one or several security groups.

]
.col[
.center[![Security Groups](/csc-cloud/img/security_groups.drawio.svg)]
]]

---

# [Pouta] Creating a security group rules

.container[.col50[

* Navigate to:
  * **Network > Security Groups**
* First create a security group (any sensible "Name" and "Description" are valid).
* Secondly, click in "Manage Rules" and create rule opening entries.
  * You may use a predefined rule, ex. SSH, where you only need to provide the range of IPs that will be able to connect using SSH.
  * You may also create a "Custom TCP/UDP/ICMP Rule", where more fine grained rules can be defined.

].col[

![:scale 80%, Add rule](/csc-cloud/img/add_rule.png)]

]

---

# [Pouta] Creating an Instance

.container[.col[

* Navigate to:
  * **Compute>Instances**
  * and click in "Launch Instance"
* Give **Instance name** as `lastname_firstname_instance`.
* Select a **Flavor** of your choice (`standard.tiny` is a good first choice)
* Select **Instance Boot Source** as "Boot from image".
* Pick an **Image Name** - any image
* Navigate to the **Access & Security** tab and select your **Key Pair**.
  * Make sure that the “SSH - World” Security Group is selected (otherwise the firewall will block the connection).

].col[
![:scale 75%, launch instance](/csc-cloud/img/launch_instance.png)
]]---
class: topicslide

.topic[

# Persistent Storage

]

---

# Persistent Data Volumes

.container[.col70[

A good practice is to separate the **data** from the **application** (OS and other software). Volumes are very helpful to achieve this. It is recommended to store the data in a volume, and the OS and software in another.

* Volumes are **project specific**, not user specific.
* A project can have **several volumes**.
* Volumes can be **transferred to other projects** in same cloud service.
* One volume can be **attached to one VM** at a time.
* Volumes can be management with **web interface** or **command line client**.
* Data stored in Persistent volumes is resilient to Disk Failures, Server failures, Accidental deletion of VMs, Crashing of VMs
  * But not to human errors ➡️ No Backups.
* It is easy to create and recover snapshots.

].col[
.center[![Data volume](img/dataVolume.drawio.svg)]
]]

---
class: topicslide

.topic[

# Object Storage

]

---

# What is Object Storage

.container[.col[

* Object storage is a computer data storage architecture that manages data as objects.
* Each object consists of three things: Data, Metadata and Globally unique identifier.
* Different from other data storage architectures like File Storage: Data as a file hierarchy and Block Storage: Data as blocks within sectors and tracks.
* Accessed via APIs at application-level, rather than via OS at system level.
* Scalable and Self healing storage.

]
.col[
![:scale 80%](img/objectStorage1.drawio.svg)
]]

---

# File Storage vs Object Storage

.container[.col[
.center[![File Storage](img/fileStorage.drawio.svg)]

]
.col[
.center[![Object Storage](img/objectStorage.drawio.svg)]
]]

---

# Where Object Storage Fits

## On basis of Data

.container[.col[

### Type

* Storage of Unstructured/ Semi structured Data like Media files, web contents, Backup Archives etc.
* Cold Storage of structured and semi structured data like Databases, Sensor Data, Log files etc.
* Archiving files in place of local tape drives.
* Big Data, large data sets

].col[

### Size

![data size](img/dataSize.drawio.png)
]]

---

# Where Object Storage does not fit

.container[.col[

* Hot Data.
* Relational/[OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) Databases.
* Latency intolerant applications.
* Data with Strict consistency requirements.

![MySQL](img/mySQL.png)
]
.col70[
.center[
![SQLServer](img/sqlServer.png)

![PostgeSQL](img/postgresql.png)
![Oracle](img/oracle.png)
]
]]

---

# Object Storage Around us

.container[.col[
.center[![:scale 40%, Amazon S3](img/amazonS3.png)]

![:scale 80%, Microsoft Azure](img/microsoftAzure.png)

![:scale 35%, IBM Cloud Object Storage](img/ibmCloudObjectStorage.png)
![:scale 50%, Google Cloud Storage](img/googleCloudStorage.png)

]
.col66[
  ![:scale 80%, Object Storage Around Us](img/objectStorageAround.png)
]]

---

# Allas: Object Storage in cPouta

* Launched for customers in 2018.
* REST API available, S3 and Swift API compatible, Supports WebUI and Swift/S3 CLI tools
* Charging on the basis of storage not transactions.
* Initial quota for object storage/project is **10 TiB**.
  * Buckets per project: **1000**
  * Objects per Bucket: **500000**
* Content Agnostic, Distributed, Scalable and Highly available Data Storage.
* Access control possible for buckets/objects.

Allas [billing and quotas](https://docs.csc.fi/data/Allas/introduction/#billing-and-quotas) documentation.

---

# Allas: Architecture

.center[![Storage API](img/storageAPI.drawio.svg)]


---
# OpenStack CLI

- Exersise section might suffice for this 
  
  or 

- Add overview content on OpenStack architecture, API and CLI  

---
# Deploying an Application on a VM 

- Exersise section might suffice for this 
  
  or 

- Add overview content (e.g. package management, installation, compiling? )
---

# Documentation Links

* The cPouta main page: [pouta.csc.fi](https://pouta.csc.fi/)
* These slides: <https://pouta-course.a3s.fi/index.html>
* These slides in PDF: <https://pouta-course.a3s.fi/pouta-course-slides.pdf>
* Pouta documentation: [docs.csc.fi](https://docs.csc.fi/cloud/pouta/)
* [Command line tools](https://docs.csc.fi/accounts/how-to-add-service-access-for-project/)

## Accounts

* [Create CSC account](https://docs.csc.fi/accounts/how-to-create-new-user-account/)
* [Pouta access](https://docs.csc.fi/accounts/how-to-add-service-access-for-project/)

---
class: align-middle

# Contact Us

If you have any problem, request, or you just need more information:

## <servicedesk@csc.fi>

---
background-image: url(/csc-cloud/img/author.png)

.fullname[
Tewodros Deneke, Cloud System Specialist, <Tewodros.Deneke@csc.fi>

Alvaro Gonzalez, Cloud system specialist, <Alvaro.Gonzalez@csc.fi>

CSC – IT Center for Science Ltd.
]
<div class="vl"></div>
.social[
<https://facebook.com/CSCfi>

<https://twitter.com/CSCfi>

<https://www.youtube.com/c/CSCfi>

<https://www.linkedin.com/company/csc--it-center-for-science>
]
