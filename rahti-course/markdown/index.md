
class: topicslide

.topic[

# Container clouds fundamentals

## (with Rahti OpenShift OKD)

Tewodros Deneke, Cloud System Specialist

Álvaro González, Cloud System Specialist
]

---

# Schedule

| When | What ||
|:-----:|:-----|:-|
|9:00 - 10:30|Lecture| What is Rahti? |
|||Introduction to containers|
|||Application templates|
|||Web interface Howtos|
| 10:30 - 10:45 | Coffee break |☕|
| 10:45 - 12:00 | Exercises ||
| 12:00 - 13:00 | Lunch break |🍽️|
|13:00 - 14:30|Lecture|Storage|
|||High level Kubernetes architecture|
|||Command line tool|
|||Command line interface Howtos|
| 14:30 - 14:45 | Coffee break |☕|
| 14:45 - 16:00 | Exercises ||
| 16:00 - 16:15 | Closing |Documentation and contact info|

---

layout: false
class: topicslide

.topic[

# What is Rahti?

## PaaS cloud

]

---

# ![:scale 10%, OpenStack](/csc-cloud/img/openshift-logo.png) Rahti

.bubble.bubble-bottom-left[
The Rahti Cloud is CSC's **Platform as a Service** (PaaS) offering. Based on **OpenShift**/**Kubernetes**.
]

## 😐

.bubble.bubble-bottom-left[
  Allows to run **Containers** on CSC's Data Center infrastructure. Provides the infrastructure (**OS**, **Middleware**, **Runtime**, ...), so you can just worry about running the Software and nothing else.
  ]

## 😶

---

# Containers (Software vs real life)

.container[
.col[
Before
.center[
![:scale 30%, old-cargo](/csc-cloud/img/old-time-cargo.jpg)
![:scale 30%, old-cargo](/csc-cloud/img/old-time-cargo-2.jpg)
![:scale 30%, old-cargo](/csc-cloud/img/Loading-goods.jpg)
]

* **Different installation methods**: compile from source, installation wizard, rpm/deb package, etc
* **Libraries dependency** problems: untested, hard to find, outdated, etc
* **No security** isolation
* **No assured** resources
]
.col[

After

.center[
![:scale 30%, modern-cargo](/csc-cloud/img/truck-cargo.jpg)
![:scale 30%, modern-cargo](/csc-cloud/img/train-cargo.jpg)
![:scale 30%, modern-cargo](/csc-cloud/img/modern-cargo.jpg)
]

* **Standard image registry**, fast and standard deployment.
* **Uniform resource identifier**
  * `host/name:version`
* **Included library dependencies** in the container
* **Isolated** from the rest of the system
* **Assured resources**

]]

---

# Rahti advantages

.container[.col60[

* Out of the box:
  * **health monitoring**, resource consumption, and liveness and readiness probes.
  * **scaling**, resources can be configured to scale up or down (fine grained lower limit) responding to load. (faster than VMs)
  * **failover**, in case of any failure, like hardware failure, the software will be restarted.
  * **rolling updates**, a new version of an application will be deployed with no downtime.
  * **load balancing**, automatically distributes load among resources.
  * **DNS**, no need to make any support request or wait\*.footnote[\*For a given pattern of URLs. `something.rahtiapp.fi`].
  * **certificates**, always valid, automatically renewed*.

  ]
.col[
  .right[![:scale 85%, Orchestration](/csc-cloud/img/container-158362.svg)]
]]

---

# More Rahti advantages

.container[.col60[

* Simple code deploying:
  * Source code. Rahti provides tools to build and deploy code automatically. **Source2Image (S2I)**.
  * Internal Rahti **template catalog**.
  * Upstream **Helm** charts.

* Support in the **web interface**:
  * Launch applications
  * Tune application parameters
  * Request storage
  * Debug and monitor applications
  * Check logs

* Also powerful **CLI** and **library** interfaces.

  ]
.col[
  .right[![:scale 85%, Orchestration](/csc-cloud/img/container-158362.svg)]
]]

---

# Interacting with Rahti control plane

.container[
.col.center[

### Web console

.fillimg[
![:scale 80%, web-console](/csc-cloud/img/rahti-ui.png)
![:scale 80%, web-console](/csc-cloud/img/rahti-ui-browse.png)
]
]
.col.padleft[
.center[ ### Command line ]

```sh
oc create -f pod.yaml
oc replace --force pod.yaml
oc apply -f *.yaml
oc patch ...
oc expose ...
```

]
.col.padleft[
.center[ ### Using client library ]

```python
from kubernetes import client, config

k8s = config.new_client_from_config()
# etc...
```

.small[

* Official: Go, Python, Java, dotnet, JavaScript
* Community maintained: Clojure, Go, Java, Lisp, Node.js, Perl, PHP, Python, Ruby, Rust, Scala, dotNet, Elixir, Haskell]

]]

---

# Web console

.tighter[

### Service catalog .padleft[] .gray[Application console .padleft[] Cluster console]

]
.container[
.col[

* The default opening viewport
* Create projects
* Launch applications from templates
* Deploy from images

]
.padleft.maxhalf.col[
.fillimg[
![:scale 75%, web-console](/csc-cloud/img/gui/service catalog.png)
]]]

---

# Web console

.tighter[

### .gray[Service catalog] .padleft[] Application console .padleft[] .gray[Cluster console]

]
.container[
.col[

* Create some API objects
* Deploy images
* Claim storage
* View and modify workloads and API objects

* Monitoring
]
.padleft.maxhalf.col[
![:scale 75%, web-console](/csc-cloud/img/gui/application console.png)

]]

---

# Web console:

.tighter[

### .gray[Service catalog .padleft[] Application console] .padleft[] Cluster console

]
.container[
.col[

* Similar to application console but with different arrangement
* More fine-grained
]
.padleft.maxhalf.col[

![:scale 75%, web-console](/csc-cloud/img/gui/cluster console.png)
]]

---

# Containers with Docker I

.container[
.col[

Docker is a set of PaaS products that use **OS-level virtualization** to deliver **software in packages** called Open Container Initiative (OCI) \[2\] \[3\].footnote[\[2\]: [en.wikipedia.org/wiki/Docker](https://en.wikipedia.org/wiki/Docker_%28software%29) \[3\]: [OCI Containers](https://opencontainers.org/)]

There are other OCI compatible container run times ([CRI-O](https://cri-o.io/), [Podman](https://podman.io/), ...) but we will only focus in Docker.

* All containers running in the same hardware are run by a single operating system kernel and therefore use **fewer resources than virtual machines**.

]
.col[

.right[![:scale 90%, VMs vs. containers](/csc-cloud/img/vm_vs_container.png)]

]]

---

# Containers with Docker II

.container[
  .col[

* Container images are stored in "container registries"
  * Docker hub is the default registry.
      * <https://hub.docker.com>
  * Rahti provides a private registry. 
      * <https://registry-console.rahti.csc.fi/>

* Containers are stateless.
  * Any change to a file, done inside a container image will be **lost**.
  * Necessary to use **external volumes** to save data or configuration

]

.col[

.center[![:scale 80%, Docker logo](/csc-cloud/img/docker.drawio.svg)]

]]

---

# API Objects

.container[
  .col[

In Kubernetes/OpenShift everything is a object

* Set of API object **abstractions**:
  * Network
  * Container, management and creation
  * Job scheduling
  * Runtime of containers
]
  .col70[
.center[![:scale 85%, Objects](/csc-cloud/img/Kubernetes-fuller.drawio.svg)]
  ]]

---

# Project

A project sandboxes API objects (Pods and others) in a common namespace.
.container[
  .col[

* Similar to **Namespace**
  * (with extra features)
* Local **isolated network**
  * For security reasons, projects can not access other projects by default.
* A project has:
  * **Name**: Should be short and descriptive
  * **Display Name**: Should be understandable
  * **Description**: Must be `csc_project: 9999999`
        * where `9999999` is the project number


].col[
![:scale 100%, Project page](/csc-cloud/img/projectPage.png)
]]

---

# Pod

.container[
.col[

* A pod is a collection of **containers** sharing a network and Inter-process communication namespace
  * Containers live in one pod
* There is no *container object* in Kubernetes
* Nearly always one container per pod
  * Ex: Sidecar container design pattern

]
.maxhalf.col.padleft[
.boxcol.container[
.col[

```yaml
# my-pod.yaml
kind: Pod
apiVersion: v1
metadata:
 name: my-pod
spec:
 containers:
 - name: container-1
   image: container-1-image
 - name: container-2
   image: container-2-image
```

]
.padleft.scaleimg.col[
.center[![pod](/csc-cloud/img/pod-and-conts.drawio.svg)
]]]

Communicate via:

* localhost (network)
* shared folders (emptyDir)
* memory (Inter-process communication)

]]

---

# Service

An API object that provides pods a **load balanced** stable network identity.

.container[

.col[

* The IP of a Pod **may change**, the **IP** of a Service **will not change**.
  * Pods should communicate with each other using services

]
.col[

.center[![Service](/csc-cloud/img/servicePod.drawio.svg)]

]]

---

# Route

.container[
.col[

An API object that exposes a Service to the internet via HTTP/HTTPS.

* Every host with the pattern `*.rahtiapp.fi` will point **automatically** to Rahti:
  * `my-hello-openshift.rahtiapp.fi` is an alias for `rahtiapp.fi`.

  * If the host must be different to this pattern, a `DNS CNAME` entry must be configured by the user to point to `rahtiapp.fi`.
* Every host with the pattern `*.rahtiapp.fi` will have automatically a valid **TLS certificate**.

]

.col[

.center[![Route Service Pod](/csc-cloud/img/routeServicePod.drawio.svg)]

]]

---

# Templates

.container[
  .col[

* Ready to go applications
  * or components of applications (ex: Databases).
* Easy to deploy from the graphical interface:
  * Languages (S2I): Java, Ruby, Python...
  * Databases: MongoDB, MySQL, MariaDB, PostgreSQL...
  * Others: Jenkins

]
.col[
.center[![Catalog](/csc-cloud/img/templateCatalog.drawio.svg)

![Python](/csc-cloud/img/Python-logo-notext.svg)
![:scale 20%, Ruby](/csc-cloud/img/Ruby_logo.svg)
![PostgreSQL](/csc-cloud/img/PostgreSQL.svg)

![Jenkins](/csc-cloud/img/jenkins.svg)
![Hadoop](/csc-cloud/img/hadoop.svg)
![Redis](/csc-cloud/img/redis.svg)
]]]

---

# Catalog

.center[![:scale 45%, Catalog](/csc-cloud/img/catalog.png)]

---

# Source to image Python I

.center[![:scale 50%, Source2Image](/csc-cloud/img/PythonS2I-information.png)]

---

# Source to image Python II

.center[![:scale 50%, Source2Image](/csc-cloud/img/PythonS2I.png)]

---

# Source to image Python III

.container[.col66[
.center[![:scale 65%, Source2Image](/csc-cloud/img/PythonS2I-build.png)]
].col[
  Rahti will automatically:

* Fetch the code
* Analyze it
* Build a new image
* Deploy it
* Make it available to the Internet

]]

---

# Getting Access to Rahti

- content comming soon!

---

# [Rahti] Logging in on web console

.container[
.col[

* Navigate to [https://rahti.csc.fi:8443](https://rahti.csc.fi:8443).
* Use your CSC account to login

]

.col[
![:scale 100%, Logging page](/csc-cloud/img/logging-web-console.png)

]]

---

# [Rahti] Creating a project

.container[
.col66[

* Click in "Create Project"
  * **Name Short**, name that will be used to reference the project
  * **Display Name**, Descriptive name that should make clear what the project is
  * **Description**, It **must** be `csc_project: 2001316`. It must be associated to a CSC project for billing purposes.
* Initial quota of 5 projects

]
.col[
![:scale 80%, Logging page](/csc-cloud/img/creatingProject.png)
]]

---

# [Rahti] How to open a terminal session

.container[
  .col66[
![:scale 100%, Terminal in a Pod](/csc-cloud/img/terminalPod.png)
  ].col[
  
* Go to the "Pods page"
  **Applications** > **Pods**
* Click in the running Pod that you one to open an interactive session with
* Click in **Terminal**

]]

---

# [Rahti] How to see application logs?

.container[
  .col66[
.center[![:scale 95%, View log GUI](/csc-cloud/img/viewLog.png)]
  ]
  .col[

* Go to the "Deployments page"
  * **Applications** > **Deployments**
* Click in "View Log"

![:scale 100%, View Log Page](/csc-cloud/img/viewLogPage.png)

]]

---

# [Rahti] Editing API objects

.container[
  .col66[
![:scale 100%, Edit Pod](/csc-cloud/img/editPod.png)
  ].col[

* Go to the objects page, in this case the "Pods page"
* Click in the object you want to edit.
* Click in **Actions** > **Edit YAML**

  ]]
---
# Deploying Containerized Applications

- Exersise section might suffice for this 
  
  or 

- Add overview content (e.g. packaging, adding route, etc )



---

# OpenShift CLI

- Exersise section might suffice for this 
  
  or 

- Add overview content on OpenShift architecture, API and CLI 
---

# Packaging Containerized Applications

- Content comming soon (e.g. Helm charts and Templates) 
---

# Documentation Links

* The Rahti main page: [rahti.csc.fi](https://rahti.csc.fi/)
* These slides: <https://rahti-course.a3s.fi/basic.html>
* These slides in PDF: <https://rahti-course.a3s.fi/rahti-course-slides.pdf>
* Rahti documentation: [docs.csc.fi](https://docs.csc.fi/cloud/rahti/)
* [Command line tools](https://github.com/openshift/origin/releases/tag/v3.11.0)
* External documentation
  * Kubernetes documentation: [kubernetes.io/docs/home](https://kubernetes.io/docs/home/)
  * OpenShift documentation: [docs.okd.io ](https://docs.okd.io/)

### Accounts:

* [Create CSC account](https://docs.csc.fi/accounts/how-to-create-new-user-account/)
* [Rahti access](https://docs.csc.fi/cloud/rahti/access/)

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
---
---
---
---
---
---
---
---
---
---
---
---
---
---
---
---
