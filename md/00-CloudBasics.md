class: topicslide

.topic[

# CSC’s Cloud Services

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
]
.col[![Cloud Computing Characteristics](/csc-cloud/img/cloud_Computing_characteristics.drawio.svg)]
]

---

# Cloud computing "As A Service"

.center[![:scale 60%, Cloud computing Landscape](/csc-cloud/img/cloud_computing_landscape.drawio.svg)]

---

# CSC cloud services

* The **Pouta Cloud** is CSC’s Infrastructure as a Service ([IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)) offering. Based on [OpenStack](https://www.openstack.org/) ![:scale 3%, Openstack](/csc-cloud/img/openstack-icon.png).
  * Allows running Virtual Machines (VMs) on CSC’s Data Center infrastructure. Grants users **full control** over the OS, middleware and run time environments. On the flip side, users are responsible to **manage** and **secure** their VMs.
* Provides an IaaS cloud environment for your **sensitive data** processing (ePouta).

* The **Rahti Cloud** is CSC's Platform as a Service ([PaaS](https://en.wikipedia.org/wiki/Platform_as_a_service)) offering. Based on [Openshift](https://www.openshift.com/) ![:scale 3%, OpenStack](/csc-cloud/img/openshift-logo.png) (Kubernetes).
  * Allows to run Containers on CSC's Data Center infrastructure. Provides the platform (OS, Middleware, Runtime, ...), so you can just worry about running the Software and nothing else.

---

# CSC cloud services comparison 

.stripetable[
||cPouta|ePouta|Rahti|
|:-:|:-:|:-:|:-:|
||![:scale 20%, OpenStack](/csc-cloud/img/openStack.png)|![:scale 20%, OpenStack](/csc-cloud/img/openStack.png)|![:scale 20%, OpenStack](/csc-cloud/img/openshift-logo.png) ![:scale 20%, Kubernentes](/csc-cloud/img/kubernetes-logo.png)|
|Usage|General purpose VMs| Sensitive Data VMs|General purpose Containers|
|Network connection|Public Internet|Private OPN/MPLS|Public Internet|
|Interfaces|WEB, CLI, API|WEB, CLI, API|WEB, CLI, API|
|ISO27001 certification|✔️|✔️|❌|
|VAHTI 2010 certification|✔️|✔️|❌|
|Firewall, LB, VM installation, VM auto-recovery, Backups|Self-service|Self-service|Self-service|
|Supported Operating Systems|All|All|Containers|
|Version|Queens|Queens|v3.11|
|GPU|✔️|✔️|❌|
|Allas (S3/Swift) Object Storage|✔️|❌|✔️|
]