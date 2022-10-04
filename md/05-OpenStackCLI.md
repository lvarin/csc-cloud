layout: false
class: topicslide

.topic[

# OpenStack CLI

]

---

# Install OpenStack CLI

First you need to install the OpenStack command line client:

* This client is written in python.
* The latest version only support Python v3.8 or newer
* The easiest way to install it is via pip:

```sh
pip install python-openstackclient
```

For other installation methods, and always up to date information you can visit:

  <https://pypi.org/project/python-openstackclient/>

To confirm the client is installed you can run:

```sh
$ openstack --version
openstack 6.0.0
```

---

# Login using an OpenStack RC file

.container[.col[

First you need to download the RC file. Go to the [Pouta web UI](https://pouta.csc.fi), click in your name and then in "OpenStack RC File v3". Then you need to "source" the file you downloaded:

```sh
$ source <OpenStackRCFile>
Please enter your OpenStack Password for project project_yyyy as user xxx

```

].col[

.center[![:scale 40%, OpenStack RC file](/csc-cloud/img/OpenStack-RC-file.png)]

]]

.container[.col[

The script will ask for your CSC account password and then set up the environment variables

].col70[

```sh
$ env | grep OS
OS_AUTH_URL=https://pouta.csc.fi:5001/v3
OS_PROJECT_ID=vcItXBbYIjZDDL5RD55mQK7Wh1Qra68PQ
OS_PROJECT_NAME=project_zzzzzzz
OS_USER_DOMAIN_NAME=Default
OS_PROJECT_DOMAIN_ID=default
OS_USERNAME=xxxxxxxxx
OS_PASSWORD=yyyyyyyyyyyyyyyyyy
OS_REGION_NAME=regionOne
OS_INTERFACE=public
OS_IDENTITY_API_VERSION=3
```

]]

---

# Flavors

The first requirement is to decide which flavor to use. Different flavors will provide different resources.

```sh
$ openstack flavor list
+--------------------------------------+------------------+--------+------+-----------+-------+-----------+
| ID                                   | Name             |    RAM | Disk | Ephemeral | VCPUs | Is Public |
+--------------------------------------+------------------+--------+------+-----------+-------+-----------+
| 0143b0d1-4788-4d1f-aa04-4473e4a7c2a6 | standard.tiny    |   1000 |   80 |         0 |     1 | True      |
| (...)                                | (...)            |  (...) | (..) |    (...)  | (...) | (...)     |
+--------------------------------------+------------------+--------+------+-----------+-------+-----------+
```

The more resources, the higher will be the cost.

For a whole and updated flavor list go to <https://docs.csc.fi/cloud/pouta/vm-flavors-and-billing/>. There you will also find the cost associated with it.

---

# Images

Next, you need to decide the image to use. You can get a list of images by:

```sh
$ openstack image list
+--------------------------------------+----------------------+--------+
| ID                                   | Name                 | Status |
+--------------------------------------+----------------------+--------+
| f505d49e-55e6-4f3f-9790-cc8250cace1b | CentOS-7             | active |
| 72251ff8-607d-451a-8769-bb2741464577 | CentOS-7-Cuda        | active |
| ea8d1ff7-1f2f-4255-ba27-62a67bc9c6bd | CentOS-8-Stream      | active |
| 2ca237c5-bd0a-4469-ae9f-20878dd288a9 | Fedora Cloud Base 31 | active |
| 2cce570c-a98d-4bab-b329-8d657c77c72e | Ubuntu-18.04         | active |
| 67f975c8-af09-4a7e-be1e-42f5a16e0cd8 | Ubuntu-20.04         | active |
| 0d952564-c0f2-4b54-ad4a-78ce6d32edb7 | Ubuntu-22.04         | active |
| 3a9aad67-0f9c-4493-b574-17fe28d40afc | cirros               | active |
| 646c6051-19ba-48e8-b8e7-397e12a55be1 | ftp-test             | active |
| dc94c6f7-38b7-412a-b231-ed161b30eb75 | geant-test-setup     | active |
+--------------------------------------+----------------------+--------+
```

In that list above, there is a list of `public` and `private` (Fedora Cloud Base 31, ftp-test, and geant-test-setup) images.

It is possible to upload your own images, or create an image using snapshots. <https://docs.csc.fi/cloud/pouta/images/>

---

# Network

The Virtual Machine needs to be connected to a network.

```sh
$ openstack network list
+--------------------------------------+-----------------+--------------------------------------+
| ID                                   | Name            | Subnets                              |
+--------------------------------------+-----------------+--------------------------------------+
| 26f9344a-2e81-4ef5-a018-7d20cff891ee | public          |                                      |
| c55bc796-841f-4704-a1a2-8f29bb9a699a | project_xxxxxxx | bef20f4d-015d-4eff-a120-1cb571eb89a9 |
+--------------------------------------+-----------------+--------------------------------------+
```

By default all projects will have a network called `project_xxxxxxx` where `xxxxxxxx` is the project number. If unsure, choose this network.

---

# Security groups

Last but not least, you need to specify a security group. By default no incoming security group is created. You need to create an incoming SSH security group and a rule:

```sh
$ openstack security group create ssh-ip
$ openstack security group rule create --ingress --dst-port 22 --remote-ip $(curl ifconfig.co -4) \
                                       --protocol tcp ssh-ip
```

The rule above will create an `ingress` opening, in the port `22` for your IPv4 ip [1].footnote[\[1\] `ifconfig.co` returns the IP of the client that makes the request, your IP], in the `tcp` protocol.

You can also list the existing security groups.

```sh
$ openstack security group list
+--------------------------------------+---------+------------------------+----------------------------------+------+
| ID                                   | Name    | Description            | Project                          | Tags |
+--------------------------------------+---------+------------------------+----------------------------------+------+
| aa4243ab-120d-439a-9156-938b1202540c | default | Default security group | 384ce70c8a604e6e8eb69aa0d5bd6997 | []   |
| 172921f5-4b26-42c6-8d60-0e77206823f8 | SSH-IP  | ssh-ip                 | 384ce70c8a604e6e8eb69aa0d5bd6997 | []   |
+--------------------------------------+---------+------------------------+----------------------------------+------+
```

---

# SSH Key

We will use the SSH protocol to login in Virtual machines. For that, you need a ssh key pair.

To create run:

```sh
$ openstack keypair create any-name-is-fine >~/.ssh/any-name-is-fine
```

This will do two things, return via the command line the private key and store it at `~/.ssh/any-name-is-fine`. And store the public key into the OpenStack servers.

You can list the available keys [1].footnote[\[1\] After creation, you will not be able to obtain again the private key] by:

```sh
$ openstack keypair list
+------------------+-------------------------------------------------+------+
| Name             | Fingerprint                                     | Type |
+------------------+-------------------------------------------------+------+
| any-name-is-fine | f2:b1:23:7f:58:ea:fc:e4:0a:1d:5a:f3:2f:f7:dd:35 | ssh  |
+------------------+-------------------------------------------------+------+
```

---

# Create a Virtual Machine

Once all the previous steps were followed, the last is to create the Virtual Machine:

```sh
$ openstack server create --flavor standard.tiny \
                          --image cirros \
                          --nic net-id=project_2001316 \
                          --security-group ssh-ip \
                          --key-name any-name-is-fine \
                          VM-name
```

You can list the all your Virtual Machines:

```sh
$ openstack server list
+--------------------------------------+---------+--------+--------------------+--------+---------------+
| ID                                   | Name    | Status | Networks           | Image  | Flavor        |
+--------------------------------------+---------+--------+--------------------+--------+---------------+
| 550fa2a8-0932-45f9-b579-dbbed4df2dc4 | VM-name | ACTIVE | project_XX=x.x.x.x | cirros | standard.tiny |
+--------------------------------------+---------+--------+--------------------+--------+---------------+
```

---

# Other commands

.container[.col[

The OpenStack command line interface supports much more commands, here is a short subset of them:

* `$ openstack --help`, shows all available commands and options

* `$ openstack server`, shows all available commands on the `server` subsection.

* `$ openstack server show VM-name`, shows the information of a VM.

* `[-f {csv,json,table,value,yaml}]`, allows to change the default `table` format of the output.

The OpenStack CLI offers all functionality that is offered by the API (or the web UI).

].col[

.center[![:scale 50%, OpenStack](/csc-cloud/img/openStack.png)]

]]
