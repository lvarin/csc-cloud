layout: false
class: topicslide

.topic[

# Virtual Machines, OpenStack

## cPouta/ePouta

]

---

# Pouta: Resources you get

.center[![:scale 65%, Typical resources you get from Pouta clouds](/csc-cloud/img/typical_Resources_You_get_from_Pouta_Clouds.png)]

.footnote[*S3/Switf API access

*Network address translation]

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

* You can use CSC’s Code Optimization Service in case you are coding your own application.
  * <https://research.csc.fi/optimization-service>
* GPGPUs are also available in the batch system on Puhti:
  * <https://docs.csc.fi/#computing/system/>
* OS images pre installed with latest [CUDA](<https://en.wikipedia.org/wiki/CUDA>) version are available. (You may also use your own OS images by installing required libraries yourself).

].col[
.right[![GPU card](/csc-cloud/img/gpu.drawio.svg)]
]]