
class: topicslide

.topic[

# Pouta management

]

---

# Pouta: Managing Project

.container[.col60[

* A Pouta project contain a set of resources: cores, memory, storage, ip-addresses
* A default project contains:
  * For cPouta: 8 cores, 32 GB memory, 1 TB disk space, 2 floating IP addresses.
  * For ePouta: Negotiated between customer and CSC
* If needed, you can ask for more resources for your project.
* Project members can build one or several VMs and volumes based on the granted resources.
* When VMs and Volumes are active they are consuming billing units (even if no one is using them).
* Project members can manage other members machines and volumes too.
* Your CSC account can be a member of many cPouta projects.

].col[
.center[![:scale 80%, Project Management](/csc-cloud/img/project_management.png)]
]]

---

# Billing

.container[.col70[

* CSC uses [Billing Units (BUs)](https://research.csc.fi/pricing) to allocate, monitor and charge for resource usage.
* Open research and educational use fall under [Free-of-charge use cases](https://research.csc.fi/free-of-charge-use-cases).
* In Pouta you are hourly billed for
  * VM usage based upon your [VM flavor](https://docs.csc.fi/cloud/pouta/vm-flavors-and-billing/).
  * Storage volumes, Object Storage and Public IPs are all [accounted hourly](https://docs.csc.fi/cloud/pouta/accounting/).
* VMs start consuming BUs once you create them, they consume BU regardless you use them or not.
  * Shutting down VM **does not stop them consuming BUs**.
  * You can **Shelve**/**Terminate** your VM for stopping BU consumption.
* Object/Volume Storage start consuming BUs once you create them
  * Even if they are **not attached** to virtual machines.
* Floating IPs are billed once they are allocated, assigned to a VM or not.
* Users can monitor usage and apply for addtional BUs through [My CSC](https://my.csc.fi).

].col[
  .center[![:scale 50%, Calculator](/csc-cloud/img/calculator.drawio.svg)]
]]

---

# Pouta: VM Lifecycle

.container[.col[

* **Active** – Consumes billing units regardless of the real usage.
* **Shut off** – Not active, but still reserves the resources. Consumes still billing units.
* **Suspended** – Temporarily suspended. Current state saved. Can be revoked. Consumes billing units
* **Shelved** – VM is shut off, resources are freed & Sate is saved. Can be later on revoked if resources are free (un-shelved). Does not use billing units.
* **Terminated** – Removes the Virtual Machine and all its data.
].col66[
  ![VM States](/csc-cloud/img/vmStates.drawio.svg)
]]

