---
title:	Persistent Storage
author:	CSC Training
lang: en
---


# Persistent Storage

## 1. Manage your own Persistent Volume

> Pre-requisites, a VM like the one create in [Creating and Configuring VMs](03-CreateConfigVMs.html)

As the name says, Persistent Volumes stay even when instances are removed. They can be attached to or detached from virtual machines while they are running. They are like a virtual external hard disks, you can save data in them and reattach to any other instances of your choice.

In this exercise, we will learn, using the web interface, how to add a persistent volume to one of the instances you created in past exercises.

1. **Create a volume**
    * Navigate to **Volume > Volumes** section in Pouta's Web Interface.
    * Click on **Create Volume**, name volume as your `lastname_firstname_vol` and size as `10GiB`

1. **Attach volume to your instance**
    * Click on **Attach Volume** from the dropdown next to your instance.
    * Attach volume to your instance.

1. **Mount this volume inside your virtual machine**
    * Connect to your cloud virtual machine.
    * Check disk partition using fdisk command and find your volume, you should be able to identify it on basis of its size.

    ```sh
    sudo fdisk -l
    ```

1. **Create a file system on your volume**
    * We will use [xfs](https://en.wikipedia.org/wiki/XFS) as the filesystem for the volume we created. But Pouta does not set any kind of limitation on that regard, i.e. you may use any filesystem supported by the OS you are running.
    * Remember to enter the correct volume device path based on the output of **fdisk**, for ex. if your disk path was **/dev/vdb**, and if you have chosen `xfs` as filesystem, you should execute the following:

    ```sh
    sudo mkfs.xfs /dev/vdb
    ```

1. **Create the mount directory**

    ```sh
    sudo mkdir -p /media/volume
    sudo chmod o+w /media/volume/
    ```

    * This is the path on where the files of the volume will be.

1. **Mount the volume**

    ```sh
    sudo mount /dev/vdb /media/volume
    ```

1. **Store some files on the volume**

1. **Detach the volume**
    * First umount the volume in the VM

    ```sh
    sudo umount /dev/vdb
    ```

    * Then go to **Detach Volume** and detach the volume

You may now repeat steps 2 and 6 to check that indeed the files you created in step 7 are still there.

## 2. Create a Snapshot of a VM

> Pre-requisites, a VM like the one create in [Creating and Configuring VMs](03-CreateConfigVMs.html)

In order to create copy of your cloud instance's OS, middleware, runtime configurations or application stacks you build inside it, you can create a snapshot of your VM. Snapshots also provide means to capture and store the filesystem state of your instance.

You can share snapshots with other Pouta users or use it for yourself to launch new VM's with the same configurations, applications and file system state. Snapshots also provide you mechanisms for saving billing units inside Pouta clouds, For example, you can take a snapshot of your ideal machine, and delete the machine. After being deleted the machine will no longer spend billing. Afterwards, when you need the VM again, you may relaunch it using that snapshot.

The snapshots are stored in Pouta as **Images**

1. **Shut down your instance**
    * In the Pouta web interface, **Compute > Instances > instance_name > Shut Off Instance**

1. **Create the Snapshot**
    * In the Pouta web interface, **Compute > Instances > instance_name > Create Snapshot**
        * Name it: `_lastname_firstname_vm_date_`
        * This creates a new Image in **Compute > Image**

1. **Review that the snapshot was created properly**
    * Go to **Compute > Images**
    * Click on the **name of your image (snapshot)** to see its details

1. **Delete your machine**
    * Go to **Instances**
    * Click on your instance and delete it.

1. **Relaunch new instance with same state**
    * Navigate to the **Instances** section and click **Launch Instance**.
        * **Instance Name**: `lastname_firstname_vm`.
        * **Flavor**: `standard.tiny`.
        * **Instance Boot Source**: `Boot from Snapshot`.
        * Find your Snapshot and select it.
        * Navigate to **Access and Security** in the same pop-up
        * Select **Key Pair** you created.
        * Select Security Group you created in same pop-up.
        * You can leave the rest as defaults and click on **Launch Instance**

This will launch new cloud machine which is in same state as of instance you deleted. Please verify if you still have your data and installed packages in VM. Notice that your VM's private IP is now different, but you can assign again the same Floating IP it had.

## 3. Create your own Bucket and Object using the WebUI

In this exercise we will store data in an Object storage system. The difference with Persistent Volumes is that, instead of using a file system with data as a file hierarchy, it stores data as blocks within buckets. A bucket (also called container) is a storage compartment for your data, the equivalent of Volume. Also normally, the files will be available using HTTP (and the S3/Swift protocol).

**Note:** A Public bucket will allow anyone with the Public URL to gain access to your objects in the container.

1. **Create a bucket**
    * Navigate to **Object Store > Containers** in Pouta's WebInterface.
    * Click on **+ Container** icon and name your container as **YYYYMMDD-yourlastname**.
    * Set Continer Access as Public and create your bucket.

2. **Upload a file to the bucket**
    * Create a text file on your local machine
    * Add some random lines of content, for example: "Hello World from Objectstore".
    * Save this file as **yourlastname.txt**.

3. **Upload the file to the bucket**
    * Go back to the webUI and using the upload icon: ![upload](../img/upload.png)
    * This file will be treated as a Object by Pouta Object Store.
    * Since bucket is **public**, all of its contents would be visible by anyone using the **Public URL** of your object.
    * You can access contents of your object over HTTPS by browsing its public URL which is <https://a3s.fi/$Your-Bucket-Name/$Your-ObjectName>.

4. **Check it works**

    * You can use your browser or Curl with the URL above. Using curl:

    ```sh
    curl https://a3s.fi/YYYYMMDD-yourlastname/yourlastname.txt
    ```
