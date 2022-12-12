layout: false
class: topicslide

.topic[

# Deploying an Application on a VM

]

---

# Installing software to your VM

.container[.col[

* The VM images provided by CSC include only just the basic linux tools.
* You can/must add the tools you need with using tools like:
  * System level repository installation. ex. `apt` or `yum`.
  * Language specific package managers, ex. `pip` or `npm`.
  * Compile from source
  * Docker
  * Conda

].col[
.center[![:scale 40%, Conda](/csc-cloud/img/rpm.png)] .right[![scale 100%, PyPi](/csc-cloud/img/pypi.svg)]
.center[![:scale 70%, Conda](/csc-cloud/img/docker.png)]
.right[![:scale 70%, Conda](/csc-cloud/img/conda_logo.svg)]
]]

---

# `sudo` command for system administration

.container[.col[

The default user, `cloud-user`, does not have superuser rights, but can do admin operations with sudo (**su**peruser **do**).

```bash
sudo linux-command-to-execute
```

* Repository installations
* System libraries and directories
* User accounts, ex:

```bash
sudo reboot
sudo yum install nano
sudo nano /etc/yum.conf
sudo useradd apache
```
].col[

.center[[![:scale 40%, Sandwich](https://imgs.xkcd.com/comics/sandwich.png)](https://xkcd.com/149)


<https://xkcd.com/149/>]
]]

---

# Repository installation: `yum`

.container[.col[

## In CentOS and RedHat

* List commands and options:
  * `yum help`
* Install a package from repository
  * `sudo yum install package`
* Install locally available RPM file
  * `sudo yum localinstall package.rpm`
* Update one or all packages in the system
  * `sudo yum update`
* Check what packages include the defined file
  * `yum provides filename`
  ]
  .col[

.center[![RedHat](/csc-cloud/img/Red_Hat_logo.svg)]

* Search package names and descriptions
  * `yum search term`
* Remove the package:
  * `sudo yum remove package`
  ]]

---

# Repository installation: `apt`

.container[.col[

## In Debian and Ubuntu

* List commands and options:
  * `apt --help`
* Install a package from repository
  * `sudo apt install package`
* Install locally available DEB file
  * `sudo apt install ./package.deb`
* Update one or all packages in the system
  * `sudo apt update`
* Check what packages include the defined file
  * `apt-file filename`
  ]
  .col[

.center[![:scale 40%, Debian file](/csc-cloud/img/Application-x-deb.svg)]

* Search package names and descriptions
  * `apt search term`
* Remove the package:
  * `sudo apt remove package`
  ]]

---

# Conda / Bioconda

.container[.col70[

* Easy way to install software tools together with their dependencies
* Bioconda- repository contains over 700 bioscience tools
* Does not need superuser privileges
* For installing  conda and browsing bioconda packages, check bioconda home page:
  * <https://bioconda.github.io/>
* Once you have conda installed, you can install application software with commands like:

```bash
conda create -n aligners bwa bowtie hisat star
source activate aligners 
bwa
```

].col[
  .right[![:scale 70%, Conda](/csc-cloud/img/conda_logo.svg)]
]]

---

# cPouta in action

.center[![cPouta Workflow](/csc-cloud/img/cPoutaWorkflow.drawio.svg)]


