# Table Of Content

[Definition of Kubernetes](#definition-of-kubernetes)<br>
[Definition of MetalLB](#definition-of-metallb)<br>
[Deﬁnition of Docker](#deﬁnition-of-docker)<br>
[Definition of Minikube](#definition-of-minikube)<br>
[What is the difference between MetalLB and Nginx?](#what-is-the-difference-between-metallb-and-nginx)<BR>
[What do you mean by cluster?](#what-do-you-mean-by-cluster)<BR>
[What do you mean by 'orchestration platform'?](#what-do-you-mean-by-orchestration-platform)<BR>
[Requirement of MetalLB](#requirement-of-metallb)<br>
[Environment detail OS Version](#environment-detail-os-version)<br>
[Configuration Required](#configuration-required)<br>
[Command for the setup](#command-for-the-setup)<br>
[Install Docker](#install-docker)<br>
[Install kubeadm, kubelet, and kubectl](#install-kubeadm-kubelet-and-kubectl)<br>
[Installation of Minikube ](#installation-of-minikube)<br>
[Installation of the MetalLB](#installation-of-the-metallb)<br>
[Create a deployment with a sample application](#create-a-deployment-with-a-sample-application)





# Definition of Kubernetes

 Kubernetes is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications.
* Originally developed by Google, Kubernetes provides a robust framework for efficiently managing containerized workloads across a cluster of machines. 
* It abstracts the underlying infrastructure, offering a consistent and declarative way to define, deploy, and scale applications, ensuring high availability and fault tolerance.
* Kubernetes facilitates the seamless coordination of containerized components, automates application scaling based on demand, and provides powerful tools for monitoring, logging, and maintaining the health of distributed applications.
* The platform has become a standard for container orchestration, fostering portability, scalability, and resilience in modern cloud-native application development.

**Kubernetes is like a smart manager for computer programs that come in little packages called containers. Its job is to make sure these programs run smoothly, no matter where they are or how many of them there are. It helps in starting, stopping, and managing these programs, making sure they work well together. Think of it as a traffic controller for your software, making everything organized and efficient.**

# Definition of MetalLB


MetalLB is an open-source software load balancer designed to provide network load balancing for services in Kubernetes clusters.
* Unlike traditional load balancers that might be tied to specific hardware or cloud providers, MetalLB is designed to work in any environment, including on-premises data centers or cloud platforms.

* **Load Balancing:** MetalLB ensures that incoming traffic is distributed evenly across multiple instances of a service, improving the availability and reliability of applications.
* **External Service Access:** It provides a way for services within the Kubernetes cluster to be accessed from outside the cluster. This is particularly useful for applications that need to be exposed to the internet or other networks.

* **On-Premises Deployments:** MetalLB is valuable in on-premises environments where traditional cloud-based load balancers might not be available. It allows organizations to set up and manage load balancing for their Kubernetes services in their own data centers.

* **Simplifying Networking:** MetalLB simplifies the configuration and management of network load balancing within Kubernetes, abstracting away the complexity of handling external traffic and IP addresses for services.

* **Scalability:** As applications and services scale within a Kubernetes cluster, MetalLB helps in distributing the incoming traffic efficiently, contributing to the scalability of the overall system.

# Deﬁnition of Docker

* Docker is an open-source platform that automates the process of developing, shipping, and running applications in lightweight, portable containers.

* Containers are standalone, executable software units that package an application along with its dependencies, libraries, and runtime, ensuring consistent and reliable performance across various computing environments.

# Definition of Minikube

Minikube is an open-source tool designed to facilitate local development and testing of applications within a Kubernetes environment.

* It allows developers to set up and run a single-node Kubernetes cluster on their local machine, providing a lightweight and isolated environment for experimenting with containerized applications.

* Minikube serves as a valuable resource for developers who seek to replicate Kubernetes functionalities in a smaller scale, enabling them to build, test, and debug applications locally before deploying them to larger-scale Kubernetes clusters.

# Requirement of MetalLB

In the bare metal deployment kubernetes does not provide the functionality of creating Load Balancer on
service by default

## Technologies Used

* Kubernetes
* MetalLB
* Docker

## Environment detail OS Version

* Distributor ID:	Ubuntu<br>
* Description:	Ubuntu 22.04.3 LTS<br>
* Release:	22.04<br>
* Codename:	jammy

## Configuration Required

### Configuration required to run the Kubernetes Clusters

A minimum mutlicore proccessor is required.
A minimum 2GB of RAM is required.
A minimum 20GB free space is reqiured.  


### My system configuration

* Model name: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
* RAM size is 8 GB
* Storage 256 GB

# What is the difference between MetalLB and Nginx?

MetalLB and Nginx serve different roles in managing network traffic within a Kubernetes environment. 

#### MetalLB

* MetalLB is like a traffic manager for Kubernetes clusters on bare-metal servers. It helps external users connect to services by handling IP addresses and balancing the load on the network. 
* MetalLB focuses on network protocols like TCP and UDP.

#### Nginx

* Nginx, originally designed as a web server, is a versatile tool. It acts as a traffic cop for web traffic, managing HTTP and HTTPS requests and serving as a reverse proxy. 
* Nginx has a broader job, handling web traffic but also being adaptable for other protocols.

# What do you mean by cluster?

* A Kubernetes cluster is like a group of computers that team up to make sure everything runs smoothly. In this group, there's one computer that takes charge (called the master node) and others that do the actual work (called worker nodes). They communicate a lot, share tasks, and help each other out.
* It is a way for computers to work together seamlessly, making it easy to manage and run various applications without any hiccups. The cluster ensures that everything stays organized and efficient, like a well-coordinated team of computers.

# What do you mean by 'orchestration platform'?

* An "orchestration platform" in computing refers to a system or tool that manages and coordinates the deployment, configuration, and operation of various software components or services within a complex application or infrastructure. It's like a conductor in an orchestra, coordinating the different instruments to play together harmoniously.


  
# Command for the setup
#### Step 1-System Update
* Before installing Kubernetes we have to update the system packages and cache configured in our system.
* #### 1-Command:

```
sudo apt-get update
```

* **sudo:** This command is used to execute another command with superuser (administrator) privileges.
  
* **apt-get:** This is the package management command-line tool for Debian-based Linux distributions.
It's used to interact with the Advanced Package Tool (APT) system, which handles package
installation, removal, and maintenance.

* **update:** This is a subcommand of apt-get. When you run apt-get update, it refreshes the local
package cache by contacting the package repositories conﬁgured on your system.

* #### 2-Command:

```
sudo apt-get upgrade
```
* **upgrade:** This is a sub-command of apt-get. When used in combination with apt-get, it tells the
package manager to upgrade the currently installed packages to their latest versions.

#### Step 2-

# Install Docker

Kubernetes relies on Docker for containerization. Install Docker using the following commands:

#### 1-command:
```
sudo apt-get install docker.io
```
* **install:** This is a sub-command of apt-get. When used in combination with apt-get, it speciﬁes that
you want to install a package.
* **docker.io:** This is the name of the package you want to install. In this case, it's the Docker package.
Docker is a platform that allows you to automate the deployment, scaling, and management of
applications using containerization.

#### 2-Command:
```
sudo systemctl enable docker
```
* **enable:** This is an option of the systemctl command. When you use enable, you're instructing
systemd to set up the speciﬁed service to start automatically when the system boots up.

* **docker:** This is the name of the service you want to enable. In this case, it refers to the Docker
service. The Docker service manages the Docker daemon, which in turn manages container processes
on the system.
* **systemctl:** This is a command-line tool used to interact with systemd, which is the init system and
service manager for modern Linux distributions. It's responsible for managing the services and
processes that run on the system.

#### 3-Command:
```
sudo systemctl start docker
```
* **start:** This is an option of the systemctl command. When you use start, you're instructing systemd to
initiate the speciﬁed service and start running it.

#### 4-Command:
```
systemctl status docker
```
* Above command is used to check the status of docker running or not. 

```
brijesh@brijesh-Inspiron-5567:~$ systemctl status docker
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset>
     Active: active (running) since Sat 2024-01-13 10:23:07 IST; 37min ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 1993 (dockerd)
      Tasks: 10
     Memory: 95.6M
        CPU: 577ms
     CGroup: /system.slice/docker.service
             └─1993 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/cont>

Jan 13 10:23:06 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:06.>
Jan 13 10:23:06 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:06.>
Jan 13 10:23:06 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:06.>
Jan 13 10:23:06 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:06.>
Jan 13 10:23:06 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:06.>
Jan 13 10:23:06 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:06.>
Jan 13 10:23:07 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:07.>
Jan 13 10:23:07 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:07.>
Jan 13 10:23:07 brijesh-Inspiron-5567 dockerd[1993]: time="2024-01-13T10:23:07.>
Jan 13 10:23:07 brijesh-Inspiron-5567 systemd[1]: Started Docker Application Co>
lines 1-22/22 (END)

```


#### Step 3:
# Install kubeadm, kubelet, and kubectl
These are the essential components of Kubernetes.

#### Command 1:

```
sudo apt-get install -y apt-transport-https curl
```
```
brijesh@brijesh-Inspiron-5567:~$ sudo apt-get install -y apt-transport-https curl
[sudo] password for brijesh: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
curl is already the newest version (7.81.0-1ubuntu1.15).
apt-transport-https is already the newest version (2.4.11).
The following packages were automatically installed and are no longer required:
  gyp javascript-common libc-ares2 libevent-core-2.1-7 libevent-pthreads-2.1-7
  libjs-events libjs-highlight.js libjs-inherits libjs-is-typedarray libjs-psl
  libjs-source-map libjs-sprintf-js libjs-typedarray-to-buffer libmecab2
  libnode-dev libnode72 libprotobuf-lite23 libssl-dev libuv1-dev mecab-ipadic
  mecab-ipadic-utf8 mecab-utils node-abbrev node-ansi-regex node-ansi-styles
  node-ansistyles node-are-we-there-yet node-arrify node-asap node-asynckit
  node-balanced-match node-brace-expansion node-chownr node-clean-yaml-object
  node-color-convert node-color-name node-commander node-core-util-is
  node-decompress-response node-delayed-stream node-delegates node-depd
  node-diff node-encoding node-end-of-stream node-err-code
  node-escape-string-regexp node-fancy-log node-foreground-child
  node-fs.realpath node-function-bind node-get-stream node-glob node-growl
  node-has-flag node-has-unicode node-hosted-git-info node-iconv-lite
  node-iferr node-imurmurhash node-indent-string node-inflight node-inherits
  node-ini node-ip node-ip-regex node-is-buffer node-is-plain-obj
  node-is-typedarray node-isarray node-isexe node-json-parse-better-errors
  node-jsonparse node-kind-of node-lodash-packages node-lowercase-keys
  node-lru-cache node-mimic-response node-minimatch node-minimist
  node-minipass node-mute-stream node-negotiator node-npm-bundled node-once
  node-osenv node-p-cancelable node-p-map node-path-is-absolute
  node-process-nextick-args node-promise-inflight node-promise-retry
  node-promzard node-pump node-quick-lru node-read node-readable-stream
  node-resolve node-retry node-safe-buffer node-set-blocking node-signal-exit
  node-slash node-slice-ansi node-source-map node-spdx-correct
  node-spdx-exceptions node-spdx-expression-parse node-spdx-license-ids
  node-sprintf-js node-stealthy-require node-string-decoder
  node-supports-color node-text-table node-time-stamp node-tmatch
  node-typedarray-to-buffer node-universalify node-util-deprecate
  node-validate-npm-package-license node-webidl-conversions node-whatwg-fetch
  node-wrappy node-yallist nodejs-doc
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

```
* **-y:** This is an option for apt-get that automatically answers "yes" to any prompts that might appear
during the installation process.
* **apt-transport-https:** This is the name of the package you want to install. It provides the ability to
securely download packages using the HTTPS protocol instead of regular HTTP.
* **curl:** This is the name of another package you want to install. It's a command-line tool used to
transfer data to or from a server, supporting various protocols including HTTP and HTTPS.

#### Command 2:
```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-
key add -
```
* **-s:** This is an option for curl that stands for "silent" or "quiet." It suppresses the progress output and
only displays the ﬁnal result of the command.
* **https://packages.cloud.google.com/apt/doc/apt-key.gpg:** This is the URL from which the GPG key is
being downloaded. This key is used to verify the authenticity of packages from the Google Cloud
package repository.
* **|:** This is a pipe operator that takes the output of the command on its left side and uses it as input for
the command on its right side.

* **apt-key:** This is a command used to manage GPG keys in the APT package manager. It's used to add
or remove keys from the keyring that APT uses to verify package authenticity.
* **add -:** This part of the command tells apt-key to add a GPG key to the keyring. The - at the end
indicates that the input for the key is taken from standard input, which in this case is the output of
the curl command on the left side of the pipe.

#### Command 3:

**For adding repository for Kubernetes.**

```
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
```
* **curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key:** This uses curl to download the GPG key from the specified URL. The -fsSL flags are used to make the curl command silent and follow redirects.

* **|:** This is a pipe operator, which passes the output of the curl command as input to the next command.

* **sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg:** This uses gpg to dearmor the GPG key and save it in binary format to the specified file (/etc/apt/keyrings/kubernetes-apt-keyring.gpg). The sudo command is used to run the gpg command with elevated privileges, as writing to system directories usually requires superuser permissions.

#### Command 4:

```
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring,gpg] http://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
* **echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] http://pkgs.k8s.io/core:/stable:/v1.29/deb/ /':** This echo command outputs the specified APT repository line. The line includes the URL of the Kubernetes repository and specifies the GPG keyring file for package verification.

* **|:** This is a pipe operator, which takes the output of the echo command and passes it as input to the next command.

* **sudo tee /etc/apt/sources.list.d/kubernetes.list:** This uses tee with sudo to write the output of the echo command to the /etc/apt/sources.list.d/kubernetes.list file. The tee command is used here to both display the output on the console and write it to a fil

#### Command 5:
```
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee
/etc/apt/sources.list.d/kubernetes.list
```

* **"deb https://apt.kubernetes.io/ kubernetes-xenial main":** This is the text that the echo command
is printing. It's a repository source conﬁguration line for APT, the package manager used in Debian-
based Linux distributions.
* **|:** This is a pipe operator that takes the output of the command on its left side and uses it as input for
the command on its right side.
* **tee:** This command is used to read from standard input and write to standard output and ﬁles. When
used with the sudo command, it allows you to write to ﬁles with root privileges.
* **/etc/apt/sources.list.d/kubernetes.list:** This is the ﬁle path where the output of the echo command
will be written. It's adding the new repository source to a ﬁle in the /etc/apt/sources.list.d/ directory
with the name kubernetes.list.

#### Command 6:
```
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
```
```
brijesh@brijesh-Inspiron-5567:~$ sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
kubeadm is already the newest version (1.29.0-1.1).
kubectl is already the newest version (1.29.0-1.1).
kubelet is already the newest version (1.29.0-1.1).
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
brijesh@brijesh-Inspiron-5567:~$ 

```
* **kubelet:** This is one of the Kubernetes components. The kubelet is an agent that runs on each node
in the cluster. It ensures that containers are running in a Pod.
* **kubeadm:** This is a tool used to bootstrap and manage a Kubernetes cluster. It simpliﬁes the process
of setting up a cluster on multiple nodes.
* **kubectl:** This is the command-line tool for interacting with Kubernetes clusters. It allows you to
manage and control Kubernetes resources and deployments.

#### Step 4:

* **Initialize Kubernetes Master Node (Control Plane) :** On the master node, you'll initialize Kubernetes
using kubeadm. Run the following command to initialize the master node:

#### Command 1:
```
sudo kubeadm init
```

* **init:** This is a sub-command of kubeadm. When you run kubeadm init, you're instructing kubeadm to
initialize the control plane of the Kubernetes cluster.


# Installation of Minikube 

#### Command 1:

```
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-
amd64
```
```
brijesh@brijesh-Inspiron-5567:~$ wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-
amd64
--2024-01-13 11:12:33--  https://storage.googleapis.com/minikube/releases/latest/minikube-linux-
Resolving storage.googleapis.com (storage.googleapis.com)... 2404:6800:4009:81b::201b, 2404:6800:4009:821::201b, 2404:6800:4009:822::201b, ...
Connecting to storage.googleapis.com (storage.googleapis.com)|2404:6800:4009:81b::201b|:443... connected.
```

#### Command 2:

```
cp minikube-linux-amd64 /usr/local/bin/minikube
```
```
brijesh@brijesh-Inspiron-5567:-$ sudo cp minikube-linux-amd64 /usr/local/bin/minikube
```

* **cp:** This is used copying files or directories.
  
* **minikube-linux-amd64:** This is the name of the source ﬁle that you want to copy. It seems to be a
binary ﬁle for the Minikube tool speciﬁcally built for 64-bit Linux systems.

* **/usr/local/bin/minikube:** This is the destination path where you want to copy the ﬁle. It's specifying
that you want to copy the "minikube-linux-amd64" ﬁle to the "/usr/local/bin/" directory and rename
it to "minikube" without the "-linux-amd64" part.

#### Command 3:

```
chmod 755 /usr/local/bin/minikube
```
```
brijesh@brijesh-Inspiron-5567:-$ sudo chmod 755 /usr/local/bin/minikube
```
* Above command is used to provide execution permission.
* **chmod:** This command is used to chnaging the permissions of files or directories.
*  **755:** This is a numeric representation of the permissions you want to set. In Linux ﬁle permissions,
these three digits represent diﬀerent levels of access: owner, group, and others.
* **/usr/local/bin/minikube:** This is the path to the "minikube" binary ﬁle for which you're changing the
permissions.

#### Command 4:

This command is used to check the Minikube version.

```
minikube version
```
```
brijesh@brijesh-Inspiron-5567:~$ minikube version
minikube version: v1.32.0
commit: 8220a6eb95f0a4d75f7f2d7b14cef975f050512d
brijesh@brijesh-Inspiron-5567:~$ 
```
#### Step 5:
Install Kubectl and other tools to manage applications on Kubernetes. First, add the GPG key with the
following command:
```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key
add
```
* **curl:** This is a command-line tool used to transfer data to or from a server using various protocols,
including HTTP and HTTPS.
* **-s:** This is an option for curl that stands for "silent" or "quiet." It suppresses the progress output and
only displays the ﬁnal result of the command.
* **https://packages.cloud.google.com/apt/doc/apt-key.gpg:** This is the URL from which the GPG key is
being downloaded. GPG keys are used to sign and verify packages to ensure their authenticity.
* **|:** This is a pipe operator that takes the output of the command on its left side and uses it as input for
the command on its right side.
* **apt-key add:** This command is used to manage GPG keys in the APT package manager. It's used to
add keys to the trusted keys list, allowing APT to verify the authenticity of packages from speciﬁc
repositories.

#### Step 6:
* Now we have to add kubectl repository
  
#### Command 1:

```
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee
/etc/apt/sources.list.d/kubernetes.list
```
```
brijesh@brijesh-Inspiron-5567:~$ echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee
/etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
bash: /etc/apt/sources.list.d/kubernetes.list: Permission denied
root@brijesh-Inspiron-5567:/home/brijesh#
root@brijesh-Inspiron-5567:/home/brijesh#
root@brijesh-Inspiron-5567:/home/brijesh# echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee
/etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
root@brijesh-Inspiron-5567:/home/brijesh#
```

* **deb http://apt.kubernetes.io/ kubernetes-xenial main:** This is the actual repository information that is being printed. It specifies the Kubernetes repository with the Xenial release (for Ubuntu 16.04) and the main component.

* **tee /etc/apt/sources.list.d/kubernetes.list:** The tee command is used to read from standard input and write to standard output and files. In this case, it is writing the repository information to a file named kubernetes.list in the /etc/apt/sources.list.d/ directory.

#### Step 7:

Now we have to install the Kubectl

```
apt-get update -y
apt-get install kubectl kubeadm kubectl -y
```

## Now we have to start Minikube

#### Step 8:

#### Command

```
minikube start --force
```
```
root@brijesh-Inspiron-5567:/home/brijesh# minikube start --force
😄  minikube v1.32.0 on Ubuntu 22.04
❗  minikube skips various validations when --force is supplied; this may lead to unexpected behavior
✨  Using the docker driver based on existing profile
🛑  The "docker" driver should not be used with root privileges. If you wish to continue as root, use --force.
💡  If you are running minikube within a VM, consider using --driver=none:
📘    https://minikube.sigs.k8s.io/docs/reference/drivers/none/
💡  Tip: To remove this root owned cluster, run: sudo minikube delete
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
🔄  Restarting existing docker container for "minikube" ...
🐳  Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image docker.io/kubernetesui/dashboard:v2.7.0
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
    ▪ Using image docker.io/kubernetesui/metrics-scraper:v1.0.8
💡  Some dashboard features require the metrics-server addon. To enable all features please run:

	minikube addons enable metrics-server	


🌟  Enabled addons: storage-provisioner, default-storageclass, dashboard
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
root@brijesh-Inspiron-5567:/home/brijesh# 

```

* **start:** This sub-command is used to start a Minikube cluster.

* **--force:** This flag is used to forcefully start a new Minikube cluster, overriding any existing one. It's useful when you want to start fresh or if you encounter issues with the existing cluster.
* **minikube:** This is the Minikube command-line tool used for managing local Kubernetes clusters.

#### Step 9:
### Now for checking cluster information

#### Command

```
kubectl cluster-info
```
```
root@brijesh-Inspiron-5567:/home/brijesh# kubectl cluster-info
Kubernetes control plane is running at https://192.168.49.2:8443
CoreDNS is running at https://192.168.49.2:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
root@brijesh-Inspiron-5567:/home/brijesh# 

```
#### Step 9:
#### Command for check all the running nodes

```
kubectl get nodes
```
```
root@brijesh-Inspiron-5567:/home/brijesh# kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   9d    v1.28.3
root@brijesh-Inspiron-5567:/home/brijesh# 

```

* **get nodes:** This is a sub-command of kubectl. When you run kubectl get nodes, it instructs kubectl to
retrieve and display information about the nodes in the cluster.

### Step 10:

#### Command for verify the status of Minikube

#### Command:

```
minikube status
```
```
root@brijesh-Inspiron-5567:/home/brijesh# minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured

root@brijesh-Inspiron-5567:/home/brijesh# 

```
* The minikube status command is used to check the status of a Minikube cluster. When you run this command, it provides information about whether the Minikube cluster is running or stopped.

### Step 11:

#### Command for list all addons in minikube.
#### Command:
```
minikube addons list
```
```
root@brijesh-Inspiron-5567:/home/brijesh# minikube addons list
|-----------------------------|----------|--------------|--------------------------------|
|         ADDON NAME          | PROFILE  |    STATUS    |           MAINTAINER           |
|-----------------------------|----------|--------------|--------------------------------|
| ambassador                  | minikube | disabled     | 3rd party (Ambassador)         |
| auto-pause                  | minikube | disabled     | minikube                       |
| cloud-spanner               | minikube | disabled     | Google                         |
| csi-hostpath-driver         | minikube | disabled     | Kubernetes                     |
| dashboard                   | minikube | enabled ✅   | Kubernetes                     |
| default-storageclass        | minikube | enabled ✅   | Kubernetes                     |
| efk                         | minikube | disabled     | 3rd party (Elastic)            |
| freshpod                    | minikube | disabled     | Google                         |
| gcp-auth                    | minikube | disabled     | Google                         |
| gvisor                      | minikube | disabled     | minikube                       |
| headlamp                    | minikube | disabled     | 3rd party (kinvolk.io)         |
| helm-tiller                 | minikube | disabled     | 3rd party (Helm)               |
| inaccel                     | minikube | disabled     | 3rd party (InAccel             |
|                             |          |              | [info@inaccel.com])            |
| ingress                     | minikube | disabled     | Kubernetes                     |
| ingress-dns                 | minikube | disabled     | minikube                       |
| inspektor-gadget            | minikube | disabled     | 3rd party                      |
|                             |          |              | (inspektor-gadget.io)          |
| istio                       | minikube | disabled     | 3rd party (Istio)              |
| istio-provisioner           | minikube | disabled     | 3rd party (Istio)              |
| kong                        | minikube | disabled     | 3rd party (Kong HQ)            |
| kubeflow                    | minikube | disabled     | 3rd party                      |
| kubevirt                    | minikube | disabled     | 3rd party (KubeVirt)           |
| logviewer                   | minikube | disabled     | 3rd party (unknown)            |
| metallb                     | minikube | disabled     | 3rd party (MetalLB)            |
| metrics-server              | minikube | disabled     | Kubernetes                     |
| nvidia-device-plugin        | minikube | disabled     | 3rd party (NVIDIA)             |
| nvidia-driver-installer     | minikube | disabled     | 3rd party (Nvidia)             |
| nvidia-gpu-device-plugin    | minikube | disabled     | 3rd party (Nvidia)             |
| olm                         | minikube | disabled     | 3rd party (Operator Framework) |
| pod-security-policy         | minikube | disabled     | 3rd party (unknown)            |
| portainer                   | minikube | disabled     | 3rd party (Portainer.io)       |
| registry                    | minikube | disabled     | minikube                       |
| registry-aliases            | minikube | disabled     | 3rd party (unknown)            |
| registry-creds              | minikube | disabled     | 3rd party (UPMC Enterprises)   |
| storage-provisioner         | minikube | enabled ✅   | minikube                       |
| storage-provisioner-gluster | minikube | disabled     | 3rd party (Gluster)            |
| storage-provisioner-rancher | minikube | disabled     | 3rd party (Rancher)            |
| volumesnapshots             | minikube | disabled     | Kubernetes                     |
|-----------------------------|----------|--------------|--------------------------------|
root@brijesh-Inspiron-5567:/home/brijesh# 


```

* **minikube:** This is the Minikube command-line tool used for managing local Kubernetes clusters.

* **addons:** This sub-command is used to interact with Minikube add-ons.

* **list:** This sub-command is used to list the available and enabled add-ons in the Minikube cluster.

### Step 11:

#### Command list all the container image running in the cluster
#### Command:
```
kubectl get pods --all-namespaces
```
```
root@brijesh-Inspiron-5567:/home/brijesh# kubectl get pods --all-namespaces
NAMESPACE              NAME                                         READY   STATUS    RESTARTS        AGE
kube-system            coredns-5dd5756b68-xj4lt                     1/1     Running   1 (9d ago)      9d
kube-system            etcd-minikube                                1/1     Running   1 (9d ago)      9d
kube-system            kube-apiserver-minikube                      1/1     Running   1 (4m55s ago)   9d
kube-system            kube-controller-manager-minikube             1/1     Running   1 (9d ago)      9d
kube-system            kube-proxy-vp5lh                             1/1     Running   1 (9d ago)      9d
kube-system            kube-scheduler-minikube                      1/1     Running   1 (9d ago)      9d
kube-system            storage-provisioner                          1/1     Running   3 (3m58s ago)   9d
kubernetes-dashboard   dashboard-metrics-scraper-7fd5cb4ddc-w5p7n   1/1     Running   1 (9d ago)      9d
kubernetes-dashboard   kubernetes-dashboard-8694d4445c-qxwbm        1/1     Running   2 (3m57s ago)   9d
metallb-system         controller-8b577655b-t2cq4                   1/1     Running   2 (3m57s ago)   9d
metallb-system         speaker-r52kp                                4/4     Running   4 (9d ago)      9d
root@brijesh-Inspiron-5567:/home/brijesh# 

```
* **kubectl:** This is the Kubernetes command-line tool used for interacting with Kubernetes clusters.

* **get pods:** This sub-command is used to retrieve information about pods.

* **--all-namespaces:** This flag indicates that the command should operate across all namespaces in the Kubernetes cluster, not just the default namespace.

### Step 12:
#### Enable the Kubernetes dashboard and get the URL
#### Command:
```
minikube dashboard --url
```
```
root@brijesh-Inspiron-5567:/home/brijesh# minikube dashboard --url
🤔  Verifying dashboard health ...
🚀  Launching proxy ...
🤔  Verifying proxy health ...
http://127.0.0.1:42063/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/

```

* **minikube:** This is the Minikube command-line tool used for managing local Kubernetes clusters.

* **dashboard:** This sub-command is used to open the Kubernetes Dashboard in a web browser.

* **--url:** This flag is used to print the URL of the Kubernetes Dashboard to the console without actually opening it in the default web browser.

### Step 13:
##### We need to pass the url on the browser to open the dashboard

### Output:
![Alt text](<Screenshot from 2024-01-03 15-40-24.png>)

# Installation of the MetalLB

### Step 1:

#### Command:

```
sudo kubectl apply -f
https://raw.githubusercontent.com/metallb/metallb/v0.13.12/config/manifests
/metallb-native.yaml
```
```
brijesh@brijesh-Inspiron-5567:~$ sudo kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.12/config/manifests/metallb-native.yaml
namespace/metallb-system unchanged
customresourcedefinition.apiextensions.k8s.io/addresspools.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/bfdprofiles.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/bgpadvertisements.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/bgppeers.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/communities.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/ipaddresspools.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/l2advertisements.metallb.io configured
serviceaccount/controller unchanged
serviceaccount/speaker unchanged
role.rbac.authorization.k8s.io/controller unchanged
role.rbac.authorization.k8s.io/pod-lister unchanged
clusterrole.rbac.authorization.k8s.io/metallb-system:controller unchanged
clusterrole.rbac.authorization.k8s.io/metallb-system:speaker unchanged
rolebinding.rbac.authorization.k8s.io/controller unchanged
rolebinding.rbac.authorization.k8s.io/pod-lister unchanged
clusterrolebinding.rbac.authorization.k8s.io/metallb-system:controller unchanged
clusterrolebinding.rbac.authorization.k8s.io/metallb-system:speaker unchanged
configmap/metallb-excludel2 unchanged
secret/webhook-server-cert unchanged
service/webhook-service unchanged
deployment.apps/controller configured
daemonset.apps/speaker configured
validatingwebhookconfiguration.admissionregistration.k8s.io/metallb-webhook-configuration configured

```

* **sudo:** It's a command to execute the following command with elevated privileges. It might prompt you to enter your password.

* **kubectl apply:** This kubectl sub-command is used to apply configuration changes to a Kubernetes cluster.

* **-f:** This flag specifies that the next argument is a filename or a URL containing the manifest.

* **https://raw.githubusercontent.com/metallb/metallb/v0.13.12/config/manifests/metallb-native.yaml:** This is the URL pointing to the YAML manifest file for MetalLB. The specified version is v0.13.12 in this case, and it might change based on the latest release.

#### Command:
```
sudo kubectl apply -f
https://raw.githubusercontent.com/metallb/metallb/v0.13.12/config/manifests
/metallb-frr.yaml
```  
```
brijesh@brijesh-Inspiron-5567:~$ sudo kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.12/config/manifests/metallb-frr.yaml
namespace/metallb-system unchanged
customresourcedefinition.apiextensions.k8s.io/addresspools.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/bfdprofiles.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/bgpadvertisements.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/bgppeers.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/communities.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/ipaddresspools.metallb.io configured
customresourcedefinition.apiextensions.k8s.io/l2advertisements.metallb.io configured
serviceaccount/controller unchanged
serviceaccount/speaker unchanged
role.rbac.authorization.k8s.io/controller unchanged
role.rbac.authorization.k8s.io/pod-lister unchanged
clusterrole.rbac.authorization.k8s.io/metallb-system:controller unchanged
clusterrole.rbac.authorization.k8s.io/metallb-system:speaker unchanged
rolebinding.rbac.authorization.k8s.io/controller unchanged
rolebinding.rbac.authorization.k8s.io/pod-lister unchanged
clusterrolebinding.rbac.authorization.k8s.io/metallb-system:controller unchanged
clusterrolebinding.rbac.authorization.k8s.io/metallb-system:speaker unchanged
configmap/frr-startup unchanged
configmap/metallb-excludel2 unchanged
secret/webhook-server-cert unchanged
service/webhook-service unchanged
deployment.apps/controller configured
daemonset.apps/speaker configured
validatingwebhookconfiguration.admissionregistration.k8s.io/metallb-webhook-configuration configured

```
* **sudo:** This is a command to execute the following command with elevated privileges. It might prompt you to enter your password.

* **kubectl apply:** This kubectl sub-command is used to apply configuration changes to a Kubernetes cluster.

* **-f:** This flag specifies that the next argument is a filename or a URL containing the manifest.

* **https://raw.githubusercontent.com/metallb/metallb/v0.13.12/config/manifests/metallb-frr.yaml:** This is the URL pointing to the YAML manifest file for MetalLB with FRR support. The specified version is v0.13.12 in this case.
  
  ### Problem 1:
  When I enter command given below error occures that no profile found.

  #### Command:
  ```
  minikube profile list
  ```

  ### Solution :

  Now restart the minikube by typing command

  ```
  minikube start
  ```


Now Check again for minikube profile list 
#### Command:
  ```
  minikube profile list
  ```
```
brijesh@brijesh-Inspiron-5567:~$ minikube profile list
|----------|-----------|---------|---------------|------|---------|---------|-------|--------|
| Profile  | VM Driver | Runtime |      IP       | Port | Version | Status  | Nodes | Active |
|----------|-----------|---------|---------------|------|---------|---------|-------|--------|
| minikube | kvm2      | docker  | 192.168.39.14 | 8443 | v1.28.3 | Stopped |     1 | *      |
|----------|-----------|---------|---------------|------|---------|---------|-------|--------|
brijesh@brijesh-Inspiron-5567:~$ 

```

  #### Step 2:
   Verify that metallb is listed on the available add-ons for minikube.

  #### Command:
  ```
  Minikube addons list
  ```
```
brijesh@brijesh-Inspiron-5567:~$ minikube addons list
|-----------------------------|----------|--------------|--------------------------------|
|         ADDON NAME          | PROFILE  |    STATUS    |           MAINTAINER           |
|-----------------------------|----------|--------------|--------------------------------|
| ambassador                  | minikube | disabled     | 3rd party (Ambassador)         |
| auto-pause                  | minikube | disabled     | minikube                       |
| cloud-spanner               | minikube | disabled     | Google                         |
| csi-hostpath-driver         | minikube | disabled     | Kubernetes                     |
| dashboard                   | minikube | disabled     | Kubernetes                     |
| default-storageclass        | minikube | enabled ✅   | Kubernetes                     |
| efk                         | minikube | disabled     | 3rd party (Elastic)            |
| freshpod                    | minikube | disabled     | Google                         |
| gcp-auth                    | minikube | disabled     | Google                         |
| gvisor                      | minikube | disabled     | minikube                       |
| headlamp                    | minikube | disabled     | 3rd party (kinvolk.io)         |
| helm-tiller                 | minikube | disabled     | 3rd party (Helm)               |
| inaccel                     | minikube | disabled     | 3rd party (InAccel             |
|                             |          |              | [info@inaccel.com])            |
| ingress                     | minikube | disabled     | Kubernetes                     |
| ingress-dns                 | minikube | disabled     | minikube                       |
| inspektor-gadget            | minikube | disabled     | 3rd party                      |
|                             |          |              | (inspektor-gadget.io)          |
| istio                       | minikube | disabled     | 3rd party (Istio)              |
| istio-provisioner           | minikube | disabled     | 3rd party (Istio)              |
| kong                        | minikube | disabled     | 3rd party (Kong HQ)            |
| kubeflow                    | minikube | disabled     | 3rd party                      |
| kubevirt                    | minikube | disabled     | 3rd party (KubeVirt)           |
| logviewer                   | minikube | disabled     | 3rd party (unknown)            |
| metallb                     | minikube | enabled ✅   | 3rd party (MetalLB)            |
| metrics-server              | minikube | disabled     | Kubernetes                     |
| nvidia-device-plugin        | minikube | disabled     | 3rd party (NVIDIA)             |
| nvidia-driver-installer     | minikube | disabled     | 3rd party (Nvidia)             |
| nvidia-gpu-device-plugin    | minikube | disabled     | 3rd party (Nvidia)             |
| olm                         | minikube | disabled     | 3rd party (Operator Framework) |
| pod-security-policy         | minikube | disabled     | 3rd party (unknown)            |
| portainer                   | minikube | disabled     | 3rd party (Portainer.io)       |
| registry                    | minikube | disabled     | minikube                       |
| registry-aliases            | minikube | disabled     | 3rd party (unknown)            |
| registry-creds              | minikube | disabled     | 3rd party (UPMC Enterprises)   |
| storage-provisioner         | minikube | enabled ✅   | minikube                       |
| storage-provisioner-gluster | minikube | disabled     | 3rd party (Gluster)            |
| storage-provisioner-rancher | minikube | disabled     | 3rd party (Rancher)            |
| volumesnapshots             | minikube | disabled     | Kubernetes                     |
|-----------------------------|----------|--------------|----------------
```

 #### Step 3: 
 
 Enable the MetalLB minikube add-on.

  #### Command:
  ```
  minikube addons enable metallb
  ```
```
brijesh@brijesh-Inspiron-5567:~$ minikube addons enable metallb
❗  metallb is a 3rd party addon and is not maintained or verified by minikube maintainers, enable at your own risk.
❗  metallb does not currently have an associated maintainer.
    ▪ Using image quay.io/metallb/controller:v0.9.6
    ▪ Using image quay.io/metallb/speaker:v0.9.6
🌟  The 'metallb' addon is enabled

```
 
 
 #### Step 4:
Conﬁgure the IP addresses that can be used by MetalLB for the LoadBalancer services.

#### Command:
```
minikube addons configure metallb
```
```
brijesh@brijesh-Inspiron-5567:~$ minikube addons configure metallb
-- Enter Load Balancer Start IP: 192.168.39.01
--Invalid input, please enter a value:-- Enter Load Balancer Start IP: 192.168.39.14
-- Enter Load Balancer End IP: 192.168.39.80
    ▪ Using image quay.io/metallb/speaker:v0.9.6
    ▪ Using image quay.io/metallb/controller:v0.9.6
✅  metallb was successfully configured
brijesh@brijesh-Inspiron-5567:~$ 


```

#### Step 5:
 Review the applied settings.
#### Command:
```
kubectl get configmap/config -n metallb-system -o yaml
```
```
brijesh@brijesh-Inspiron-5567:~$ kubectl get configmap/config -n metallb-system -o yaml
apiVersion: v1
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - 192.168.39.14-192.168.39.80
kind: ConfigMap
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","data":{"config":"address-pools:\n- name: default\n  protocol: layer2\n  addresses:\n  - 192.168.39.14-192.168.39.80\n"},"kind":"ConfigMap","metadata":{"annotations":{},"name":"config","namespace":"metallb-system"}}
  creationTimestamp: "2024-01-03T10:37:19Z"
  name: config
  namespace: metallb-system
  resourceVersion: "18734"
  uid: 1a6c4839-057e-4535-8ba4-db10f7769c20
brijesh@brijesh-Inspiron-5567:~$ 


```

* **kubectl:** This is the Kubernetes command-line tool used for interacting with Kubernetes clusters.

* **get:** This sub-command is used to retrieve information about Kubernetes resources.

* **configmap/config:** This specifies the type and name of the resource to retrieve. In this case, it's a ConfigMap with the name "config."

* **-n metallb-system:** This flag specifies the namespace where the ConfigMap is located. In this example, it's in the "metallb-system" namespace.

* **-o yaml:** This flag specifies the output format. It requests the output in YAML format.
  
 #### Step 6:

  # Create a deployment with a sample application.

  #### Command:

  ```
  kubectl create deployment nginx \
--image quay.io/redhattraining/nginx:1.21 --port 80
  ```
```
brijesh@brijesh-Inspiron-5567:~$ kubectl create deployment nginx \
--image quay.io/redhattraining/nginx:1.21 --port 80
error: failed to create deployment: deployments.apps "nginx" already exists
brijesh@brijesh-Inspiron-5567:~$ 


```
* **create deployment nginx:** This part creates a new Kubernetes deployment named "nginx."

* **--image quay.io/redhattraining/nginx:1.21:** This specifies the container image for the deployment. In this case, it's using the NGINX image from the Quay.io registry with the tag version 1.21.

* **--port 80:** This sets the container port to 80, indicating that the NGINX container listens on port 80.

### Step 7:
 Verify that the deployment and pod are ready.
 #### Command:
 ```
 kubectl get deployments,pods -l app=nginx
 ```
```
brijesh@brijesh-Inspiron-5567:~$ kubectl get deployments,pods -l app=nginx
NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx   1/1     1            1           9d

NAME                        READY   STATUS    RESTARTS        AGE
pod/nginx-8bc664746-j7d4p   1/1     Running   2 (7d21h ago)   9d
brijesh@brijesh-Inspiron-5567:~$ 


```
 * **kubectl get:** The command to retrieve information about Kubernetes resources.
* **deployments,pods:** Specifies the types of resources to retrieve information about. In this case, it's deployments and pods.
* **-l app=nginx:** Uses a label selector to filter the resources based on the label "app" with the value "nginx". This means it will only show deployments and pods that have this specific label.

### Step 8: 
Expose the deployment to create a load balancer service

#### Command:

```
kubectl expose deployment nginx\ --type LoadBalancer --port 80 --target-port 80
```
```
brijesh@brijesh-Inspiron-5567:~$ kubectl create deployment nginx \
--image quay.io/redhattraining/nginx:1.21 --port 80
service/nginx exposed

```
* **kubectl expose deployment nginx:** This part of the command specifies that you want to expose the deployment named "nginx."

* **--type LoadBalancer:** This option specifies the type of service to create. In this case, it's a LoadBalancer service. A LoadBalancer service provides external access to the services by creating a cloud provider load balancer.

* **--port 80:** This option specifies the port on which the service will be exposed.

* **--target-port 80:** This option specifies the target port to which the traffic will be forwarded inside the pods.

### Step 9:
 Get the external IP address for the load balancer service.

 #### Command:
 ```
 kubectl get services -l app=nginx
 ```
```
brijesh@brijesh-Inspiron-5567:~$ kubectl get services -l app=nginx
NAME    TYPE           CLUSTER-IP      EXTERNAL-IP      PORT(S)        AGE
nginx   LoadBalancer   10.103.130.46   192.168.122.10   80:32311/TCP   9d
brijesh@brijesh-Inspiron-5567:~$ 


```

 * **kubectl get services:** This command retrieves information about services in the Kubernetes cluster.

* **-l app=nginx:** This is a label selector that filters the services based on the label "app" with the value "nginx." It will only show services that have this specific label.

### Step 10:
Verify that the service responds with curl

#### Command:
```
curl http://192.168.122.10
```
```
brijesh@brijesh-Inspiron-5567:~$ curl http://192.168.122.10
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
brijesh@brijesh-Inspiron-5567:~$ 


```
* **curl:** This is a command-line tool for making HTTP requests. It can be used to interact with web services, download files, and perform various other HTTP-related tasks.

* **http://192.168.122.10:** This is the URL or IP address to which the HTTP request is being made. In this case, the IP address is 192.168.122.10.

### Step 11: 
Verify that the service responds with browser.
#### Command:
```
http://192.168.122.10
```
![Alt text](<Screenshot from 2024-01-03 16-26-31.png>)

