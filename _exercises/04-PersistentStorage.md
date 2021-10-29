---
title:	Persistent Storage
author:	CSC Training
lang: en
---


# Persistent Storage

# Manage your own Persistent Volume

> Pre-requisites, the VM you created in exercise A2.

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

    <pre><code>$ sudo fdisk -l</code></pre>

1. **Create a file system on your volume**
    * We will use [xfs](https://en.wikipedia.org/wiki/XFS) as the filesystem for the volume we created. But Pouta does not set any kind of limitation on that regard, i.e. you may use any filesystem supported by the OS you are running.
    * Remember to enter the correct volume device path based on the output of **fdisk**, for ex. if your disk path was **/dev/vdb**, and if you have chosen `xfs` as filesystem, you should execute the following:

    <pre><code>$ sudo mkfs.xfs /dev/vdb</code></pre>

1. **Create the mount directory**

    <pre><code>sudo mkdir -p /media/volume
    sudo chmod o+w /media/volume/</code></pre>

    * This is the path on where the files of the volume will be.

1. **Mount the volume**

    <pre><code>$ sudo mount /dev/vdb /media/volume</code></pre>

1. **Store some files on the volume**

1. **Detach the volume**
    * First umount the volume in the VM

    <pre><code>$ sudo umount /dev/vdb</code></pre>

    * Then go to **Detach Volume** and detach the volume

You may now repeat steps 2 and 6 to check that indeed the files you created in step 7 are still there.

