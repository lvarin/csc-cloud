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

.center[![:scale 50%, Typical resources you get from Pouta clouds](/csc-cloud/img/typical_Resources_You_get_from_Pouta_Clouds.drawio.png)]


.footnote[\[1\] S3/Switf API access. \[2\] Network Address Translation]

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

# Hardware Flavor Options

.center[![:scale 60%, Pouta hardware options](/csc-cloud/img/pouta_hardware_options.drawio.svg)]

Diverse set of hardware options to support your computing needs

---


# VM Flavors (extract)

.footnote[Full list of flavor available at <https://docs.csc.fi/cloud/pouta/vm-flavors-and-billing/>

Billing units and Pricing at <https://research.csc.fi/pricing>

(1 BU ≈ 0.021 EUR)]

.stripetable[
|Flavor|Cores|Memory(GiB)|Disk(root)|Disk(ephemeral)|Disk(total)|Memory/core|Billing Units/h|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|standard.tiny|1|0.9|80GB|0GB|80GB|0.9|0.25|
|io.70GB|2|9.7|20GB|70GB|90GB|4.8|3|
|hpc.4.5core|5|21|80GB|0GB|80GB|4.2|6|
|standard.3xlarge|8|62|80GB|0GB|80GB|7.7|16|
|io.700GB|16|78|20GB|700GB|720GB|4.8|24|
|hpc.4.80core|80|343|80GB|0GB|80GB|4.2|100|
|hpc.5.128core|128|464|80GB|0GB|80GB|3.6|180|
|tb.3.1470RAM|80|1470|80GB|2500GB|2580GB|18|320|
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
