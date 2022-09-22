class: topicslide

.topic[

# Persistent Storaget

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


