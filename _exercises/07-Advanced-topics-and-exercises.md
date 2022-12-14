---
title: Advanced topics
---

# Advanced topics

## 1. Creating a new network

This exercise demonstrates that you are not limited to the flat network infrastructure provided to each project by default, but rather can create more complex setups if needs dictate. 

1. **Create an entirely new network**
    * Navigate to **Network > Networks**, click **Create Network**. Use the following values:
        * **Network Name**: `lastname_firstname_network`.
        * Navigate to the **Subnet** tab and provide a:
            * **Subnet Name** as `lastname_firstname_subnet`.
            * **Network Address** as `10.0.0.0/24`. This provides you with a private address space. 
              * **Gateway IP** as `10.0.0.1`. 
        * Navigate to the **Subnet Details** page and define a DHCP pool under **Allocation Pools** for the new subnet, e.g. `10.0.0.2,10.0.0.254`.
    * Now you can click on **create**. 

1. **Create a new router**
    * Navigate to **Network > Routers**, click in **Create Router** and use the following values:
        * **Router Name** as `lastname_firstname_router`
        * Under **External Network** select **public** to attach it to the public network and get a publicly routable address.  

1. **Attach the router to the newly created subnet**
    * Navigate to **Network > Network Topology**, select the router you have created and click *Add Interface*. Use the following values:
        * **Subnet**: select the subnet you have just created.
    * Now you can click on **Submit**.
    
1. **Create a VM using the new network and access it**
    * Your network should be available for selection under the **Networking** tab of the **Launch Instane** menu.

## 2. Lets Encrypt

In this exercise we will request a free TLS certificate to Let's Encrypt.

> Let's encrypt is a non-profit certificate authority run by Internet Security Research Group (ISRG) that provides X.509 certificates for Transport Layer Security (TLS) encryption at no charge. It launched on April 12, 2016. [https://en.wikipedia.org/wiki/Let's_Encrypt](https://en.wikipedia.org/wiki/Let%27s_Encrypt)

1. Install dependencies

    ```sh
    sudo yum install certbot python2-certbot-nginx nginx
    ```

1. Open the ports
    * You must open the ports for HTTP (80) and HTTPS (443), using security groups.

1. Get the associated domain name to your floating IP

    ```sh
    host <FLOATING_IP>
    ```

    * The domain name should be similar to `vmXXXX.kaj.pouta.csc.fi`.

1. Request the certificate using the certbot

    ```sh
    sudo certbot --nginx -d DOMAIN_NAME
    ```


