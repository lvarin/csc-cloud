
layout: false
class: topicslide

.topic[

# Creating and Configuring VMs

]

---

# User Interfaces

* Web User Interface
  * Suitable for administering individual VMs, keys, images, volumes…
  * The only UI to support Haka federated login

* CLI tools
  * Suitable for more elaborate resource provisioning and possibly some lightweight (scripted) software integrations
  * More info at <https://research.csc.fi/pouta-install-client>

* Programming APIs
  * Suitable for building very large systems and stacks
  * Support from individual services (compute, storage) to full-fledged orchestration
  * List of APIs available at <https://pouta.csc.fi/dashboard/project/api_access/> (login required).

---

# Workflow for Creating Resources I

.center[![:scale 50%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources.drawio.png)]

---

# Workflow for Creating Resources II

.center[![:scale 50%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources2.drawio.png)]

---

# Workflow for Creating Resources III

.center[![:scale 50%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources3.drawio.png)]

---

# Workflow for Creating Resources IV

.center[![:scale 50%, Workflow Creating Resources](/csc-cloud/img/workflow_creating_resources4.drawio.png)]

---

# SSH

.bubble.bubble-bottom-left[
SSH or Secure Shell is a cryptographic network protocol for operating services **securely** over an **unsecured network**.[1].footnote[[1]<https://en.wikipedia.org/wiki/SSH>, [2]<https://wiki.archlinux.org/index.php/SSH_keys>]]

## 🧑‍

## SSH keys

.bubble.bubble-bottom-left[
SSH keys serve as a means of identifycation to an SSH server using **public-key cryptography** and **challenge-response** authentication. Key-based authentication is not prone to brute-force attacks and credentials are not exposed to the server.[2]
]

## 👩‍

---

# Creating a SSH Key pair

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

# Storing a (private) Key

.container[.col[
    ![UNIX](/csc-cloud/img/unix.png)

#### Linux and Mac OS X

].col[

![Win](/csc-cloud/img/win.png)


#### Windows (PowerShell)

]]

1. Create `.ssh` directory in `$HOME` if it is not there already, copy the key pair to the `.ssh` directory.

  .container[.col[

  ```bash
mkdir -p -m=700  .ssh
  mv ~/Downloads/yourkey.pem ~/.ssh/
  chmod 400 .ssh/yourkey.pem
  ```
  ].col[

  ```bash
mkdir ~/.ssh
  mv ~/Downloads/yourkey.pem ~/.ssh/
  ```
  ]]

1. Protect key with passphrase (Optional)

.container[.col[

  ```bash
ssh-keygen -p -f yourkey.pem
  ```

].col[

  ```bash
ssh-keygen.exe -p -f yourkey.pem
  ```

]]

---

# Storing a (private) Key II

![Win](/csc-cloud/img/win.png)

#### Putty (for older Windows)

1. Download Putty and Puttygen tools if you don’t have them
1. Load your private key (`yourkey.pem`) into puttygen and change it to .ppk format
1. Open Putty, load .ppk file under Connection | SSH | Auth | Private key file for authentication
    1. Provide user name cloud-user
    1. Provide the password which you added to Puttygen (Optional)

---

# Security groups

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

# Creating a security group rules

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

# Creating an Instance

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
]]

---

# Attaching a Floating IP

.container[.col60[

* Navigate to:
    * **Compute > Instances**
    * Under Actions click in **Associate Floating IP**

* In the dialog that appears, select an IP address. If no IP is available, click in the plus sign.

![:scale 80%, Instances](/csc-cloud/img/instances.png)

].col[

![:scale 100%, Managing floating IP](/csc-cloud/img/manage-floating-ip.png)

]]

---

# Connect to the VM by SSH

```sh
ssh <USER>@<FLOATING-IP>
```

* `<FLOATING-IP>`, must be the floating ip that was set up in the previous step
* `<USER>`, must be the username suitable for the distribution used:
    * `ubuntu` for Ubuntu distributions
    * `centos` for Centos8 distributions
    * `cloud-user` for Centos7 distributions

* In most cases if you try to connect as `root`, it will fail, but you will get back the correct username:

```sh
$ ssh root@XXX.YYY.ZZZ.WWW
Please login as the user "centos" rather than the user "root".
```

---


# Create and access a VM in cPouta
## _(Checklist)_

* ☑️ Internet access
* ☑️ A CSC account
* ☑️ Access to a Pouta project
    * ☑️ Access to Pouta Web UI
* ☑️ One IPv4 address - a public “Floating IP”
* ☑️ Security Group permitting access from User’s computer
* Identity:
  * ☑️ SSH Key-Based Authentication (**recommended**)
  * Password (only for tests)
* ☑️ SSH client software


