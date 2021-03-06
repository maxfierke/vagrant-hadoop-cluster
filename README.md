Derived from @DandyDev's setup. Upgraded to trusty, using official Ubuntu box on Vagrant Cloud and made it easier to add a new node by just adding a new symbol to the `worker_nodes` array.

# A working virtual Hadoop cluster

<blockquote>
With these files you can setup and provision a locally running, virtual Hadoop cluster in real distributed fashion for trying out Hadoop and related technologies. It runs the latest Cloudera Hadoop distribution: **CDH5.2.1**. It also allows you to practise the use of [Cloudera Manager](http://www.cloudera.com/content/cloudera/en/products-and-services/cloudera-enterprise/cloudera-manager.html) for installing the Hadoop stack. If you're looking for a fully automated install, without user intervention, look elsewhere. I specifically made this with the goal of creating an environment ideally suited for Cloudera Manager to do its job. This gives you the freedom to actually install the services you want, and change the configuration how you see fit.

This README describes how to get the cluster with Cloudera Manager up and running. For more detailed instructions on how to install the whole Hadoop stack on that, you can use [this guide](http://dandydev.net/blog/installing-virtual-hadoop-cluster).
<cite>@DandyDev's</cite>
</blockquote>

I (@maxfierke) may expand this to handle more automated deployments, depending on what my requirements end up being.

## Specs

The cluster conists of 3 nodes:

* Master node with 6GB of RAM (Running the NameNode, Hue, ResourceManager etc. after installing the Hadoop services)
* 2 workers with 2GB of RAM each (Running DataNodes)

As you can see, you'll need at least 10GB of free RAM to run this. If you have less, you can try to remove one machine from the Vagrantfile. This will lead to worse performance though!

## Usage

Depending on the hardware of your computer, installation will probably take between 15 and 25 minutes.

First install [VirtualBox](https://www.virtualbox.org/) and [Vagrant](http://www.vagrantup.com/).

Install the Vagrant [Hostmanager plugin](https://github.com/smdahlen/vagrant-hostmanager)

```bash
$ vagrant plugin install vagrant-hostmanager
```

Clone this repository.

```bash
$ git clone https://github.com/maxfierke/vagrant-hadoop-cluster.git
```

Provision the bare cluster. It will ask you to enter your password, so it can modify your `/etc/hosts` file for easy access in your browser. It uses the Vagrant Hostmanager plugin to do this.

```bash
$ cd vagrant-hadoop-cluster
$ vagrant up
```

Go to the [Cloudera Manager web console](http://hadoop-master:7180) and follow the installation instructions.

It may take a few minutes for the master node to boot and Cloudera Manager to get up and running.

For more detailed instructions on how to do that, you can use [this guide](http://dandydev.net/blog/installing-virtual-hadoop-cluster). Note the master node in the guide is called hadoop-node1. In this setup, it is hadoop-master.

**Done!** Have fun with your Hadoop cluster.
