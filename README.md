Vagrant CDH5
===================

This script provides an automatically way to install **Cloudera CDH5**. What I have done is I configed all the pre-installation requirements of CDH5 and packaged it into a **vagrant** box.

After running the script, you will use Cloudera Manager for install CDH5 by yourself. I think it's a good way to hand on with CDH5 instead of using Quickstart VM.


----------


Documents
-------------
The following services are included in the cluster on the master or the slave nodes (or both, eventually). Some of them have a WebUI interface. 

> * ZooKeeper (master)
* NodeManager (master, slave) - http://MASTER_IP:8042
* ResourceManager (master) - http://MASTER_IP:8088
* JobHistory (master) - http://MASTER_IP:19888
* Namenode (master) - http://MASTER_IP:50070
* Datanode (master, slave) - http://MASTER_IP:50075
* HBase (master) - http://MASTER_IP:60010
* HBase Region Server (slave)
* WebHDFS (master) - http://MASTER_IP:50070
* Oozie (master) - http://MASTER_IP:11000
* WebHCat (master) - http://MASTER_IP:50111
* Hue (master) - http://MASTER_IP:8888

Don't forget that only the master node has a MASTER_IP!
Default MASTER_IP is `192.168.100.100`
#### <i class="icon-file"></i> Pre-installation

> **This is what I've done in the box**
>
> - Turn of firewall, iptables
* Set password for root
* Install Ntp
* Disabled Selinux
* Turn off IPv6 support
* Install Java 1.7
* Change swappiness to 10
* Turn off Huge defrag

#### <i class="icon-pencil"></i> Version

* Cloudera CDH 5.5
* CentOS 6.5
* Script version v2

#### <i class="icon-hdd"></i> Configure the clusters

Before running, you need to config the parameters for the cluster. Currently, the default clusters are:

* One Master Node with 4Gb memory (`IP: 192.168.100.100`)
* 3 Slave nodes with 2GB memory each (`IP: 192.168.100.101 - 192.168.100.103`)

#### <i class="icon-refresh"></i> Installation

```sh
$ vagrant up
```

SSH into master node (default `IP: 192.168.100.100`)
```sh
./cloudera-manager-installer.bin
```
