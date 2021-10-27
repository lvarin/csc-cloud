layout: false
class: topicslide

.topic[

# How-tos

## For the exercises

]

---

# [Pouta] Creating a SSH Key pair

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

# [Pouta] Storing a (private) Key

.container[.col[
    ![UNIX](/csc-cloud/img/unix.png)

#### Linux and Mac OS X

1. Create `.ssh` directory in `$HOME` if it is not there already, copy the key pair to the `.ssh` directory, and fix permissions.

  ```bash
  mkdir -p  .ssh
  chmod 700 .ssh
  mv ~/Downloads/yourkey.pem ~/.ssh/
  chmod 400 .ssh/yourkey.pem
  ```

1. Protect key with passphrase (Optional)

  ```bash
  ssh-keygen -p -f yourkey.pem
  ```

]

.col[
    ![Win](/csc-cloud/img/win.png)

#### Windows

1. Download Putty and Puttygen tools if you don’t have them
1. Load your private key (`yourkey.pem`) into puttygen and change it to .ppk format
1. Open Putty, load .ppk file under Connection | SSH | Auth | Private key file for authentication
    1. Provide user name cloud-user
    1. Provide the password which you added to Puttygen (Optional)

]]

---

# [Pouta] Security groups

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

# [Pouta] Creating a security group rules

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

# [Pouta] Creating an Instance

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