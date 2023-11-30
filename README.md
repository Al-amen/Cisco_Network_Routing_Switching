## Practical Lab for Academic Course CCE-416 (Network Routing and Switching Sessional)

#### Installations

* **Cisco Packet Tracer v7.3.1** can be downloaded from [here](https://drive.google.com/file/d/1LXq7vFTgzuyciKdXu7eNJ7aeOtxlyVZF/view?usp=drive_link)
* **Cisco Packet Tracer v8.2.0** can be downloaded from [here](https://drive.google.com/file/d/132jZYzdXUlHqpy4HtyAavAp6Ed-NmY8z/view?usp=drive_link)

Note: Use Packet Tracer version 7.3.1 or it won't give you 100% 
<hr/>


#### `Command:`
<br/>


```
Router> (This is User EXEC Mode.)
Router> en
Router# (This is Privileged EXEC Mode.)
Router# config terminal
Router(config)# (This is Configuration Mode.)
Router(config)# int fa0/0
Router(config-if)#	(This is Interface level within configuration mode)
```
<hr/>

* change hostname
    ```bash
    Router(config)# hostname HQ
    HQ(config)#
    ```
* assing IP address to interface fa0/0 and port status on
    ```bash
    HQ(config)#i nt fa0/0
    HQ(config-if)# ip address 192.168.1.129 255.255.255.192
    HQ(config-if)# no shutdown
    HQ(config-if)# exit
    HQ(config)#
    ```

* assing ip address to serial0/0/1 , port status on , set clock rate to 64000
    ```bash
    HQ(config)# int s0/0/1
    HQ(config-if)# ip address 192.168.1.229 255.255.255.252
    HQ(config-if)# clock rate 64000
    HQ(config-if)# no shutdown 
    HQ(config-if)# exit
    HQ(config)#
    ```


* set line console password to "cisco"
    ```bash
    HQ(config)# line console 0
    HQ(config-line)# password cisco
    HQ(config-line)# login
    HQ(config-line)# exit
    HQ(config)#
    ```

* set vty password to "cisco"
    ```bash
    HQ(config)# line vty 0
    HQ(config-line)# password cisco
    HQ(config-line)# login
    HQ(config-line)# exit
    HQ(config)#
    ```

* set privileged EXEC password to "cisco"
    ```bash
    HQ(config)# enable secret class
    ```

* encrypt the clear text passwords.
    ```bash
    HQ(config)# service password-encryption
    ```

* Require that a minimum of 10 characters be used for all passwords.
    ```bash
    HQ(config)# security passwords min-length 10
    ```

* Create a banner that warns anyone accessing the device that "unauthorized access is prohibited".
    ```bash
    HQ(config)# banner motd #Unauthorized access prohibited!#
    ```

* Disable DNS lookup (prevent the router from attempting to translate incorrectly entered commands as though they were hostnames.)
    ```bash
    HQ(config)# no ip domain-lookup
    ```

* Set the clock on the router;
    ```bash
    HQ# clock set 17:00:00 03 Oct 2023
    ```

* Set the clock timezone on the router;
    ```bash
    HQ# clock timezone BDT 6
    ```

* set line console idle EXEC sessions to 3 minutes and 30 seconds , and 4 minutes for vty
    ```bash
    HQ(config)#line con 0
    HQ(config-line)# exec-timeout 3 30
    HQ(config-line)# exit
    HQ(config)#line vty 0 4
    HQ(config-line)#exec-timeout 4 0
    HQ(config-line)# exit
    HQ(config)#
    ```

* set ip route for network 192.168.1.0/24 , mask 255.255.255.0 , hop s0/0/0
    ```bash
    HQ(config)# ip route 192.168.1.0 255.255.255.0 s0/0/0
    ```

* Save the running configuration to the startup configuration file.
    ```bash
    HQ# copy running-config startup-config
    Destination filename [startup-config]?  (Press enter)
    Building configuration...
    [OK]
    HQ#
    ```

* Display the routing table on the router.
    ```bash
    HQ# show ip route
    ```

* Display a summary list of the interfaces on the router
    ```bash
    HQ# show ip interface brief
    ```

* displays statistics for the network interfaces
    ```bash
    HQ# show interfaces
    ```

* erase the startup configuration file from NVRAM.
    ```bash
    HQ# erase startup-config
    ```

* Reload switch to remove old configuration information.
    ```bash
    HQ# reload
    ```

* HQ router needs to send the default route information 
    ```bash
    HQ(config)# router rip
    HQ(config-router)# default-information originate 
    ```

* HQ router need to disable RIP updates on FastEthernet0/0 interface
    ```bash
    HQ(config)# router rip
    HQ(config-router)# passive-interface FastEthernet0/0
    ```

<hr/>