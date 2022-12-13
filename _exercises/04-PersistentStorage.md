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
    sudo fdisk -l</code></pre>
    ```

1. **Create a file system on your volume**
    * We will use [xfs](https://en.wikipedia.org/wiki/XFS) as the filesystem for the volume we created. But Pouta does not set any kind of limitation on that regard, i.e. you may use any filesystem supported by the OS you are running.
    * Remember to enter the correct volume device path based on the output of **fdisk**, for ex. if your disk path was **/dev/vdb**, and if you have chosen `xfs` as filesystem, you should execute the following:

    ```sh
    sudo mkfs.xfs /dev/vdb</code></pre>
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

## 2. Create your own Bucket and Object using the WebUI

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
