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

