# Install local Kubernetes with minikube on AWS Cloud9 environment


## 1. Install minikube


### 1. Download and install minikube

1. Download the latest minikube stable release on x86-64 Linux

    ```console
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
    ```
    
    ```console
    mspuser::~/environment/app (master) $ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
    % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                   Dload  Upload   Total   Spent    Left  Speed
    100 23.2M  100 23.2M    0     0  22.4M      0  0:00:01  0:00:01 --:--:-- 22.4M
    mspuser::~/environment/app (master) $
    ```

2. Install Downloaded file using Debian package

    ```console
    sudo dpkg -i minikube_latest_amd64.deb
    ```
    
    ```console
    mspuser::~/environment/app (master) $ sudo dpkg -i minikube_latest_amd64.deb
    Selecting previously unselected package minikube.
    (Reading database ... 77268 files and directories currently installed.)
    Preparing to unpack minikube_latest_amd64.deb ...
    Unpacking minikube (1.25.2-0) ...
    Setting up minikube (1.25.2-0) ...
    mspuser::~/environment/app (master) $
    ```


### 2. Start Kubernetes cluster

1. Check minikube requirements

    | Parts   | Requirements            | Command |
    | ---     | ---                     | ---     |
    | CPU     | 2 CPUs or more          | nproc   |
    | MEMORY  | 2GB of free memory      | free -h |
    | DISK    | 20GB of free disk space | df -h   |

    ```console
    nproc
    free -h
    df -h
    ```

    ```console
    mspuser::~/environment $ nproc
    4
    mspuser::~/environment $ free -h
                  total        used        free      shared  buff/cache   available
    Mem:            15G        1.1G        9.4G         11M        5.0G         14G
    Swap:          488M          0B        488M
    mspuser:~/environment $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    udev            473M     0  473M   0% /dev
    tmpfs            98M  812K   97M   1% /run
    /dev/xvda1      9.7G  7.9G  1.8G  82% /
    tmpfs           488M     0  488M   0% /dev/shm
    tmpfs           5.0M     0  5.0M   0% /run/lock
    tmpfs           488M     0  488M   0% /sys/fs/cgroup
    /dev/loop0       26M   26M     0 100% /snap/amazon-ssm-agent/5656
    /dev/loop1       45M   45M     0 100% /snap/snapd/15904
    /dev/loop2       56M   56M     0 100% /snap/core18/2409
    tmpfs            98M     0   98M   0% /run/user/1000
    /dev/loop3       47M   47M     0 100% /snap/snapd/16010
    mspuser:~/environment $
    ```

2. Start minikube cluster

    ```console
    minikube start
    ```
    
    ```console
    mspmanager:~/environment $ minikube start
    * minikube v1.25.2 on Ubuntu 18.04
    * Automatically selected the docker driver. Other choices: none, ssh
    * Starting control plane node minikube in cluster minikube
    * Pulling base image ...
    * Downloading Kubernetes v1.23.3 preload ...
        > preloaded-images-k8s-v17-v1...: 505.68 MiB / 505.68 MiB  100.00% 159.83 M
        > gcr.io/k8s-minikube/kicbase: 379.06 MiB / 379.06 MiB  100.00% 36.51 MiB p
    * Creating docker container (CPUs=2, Memory=3900MB) ...
    * Preparing Kubernetes v1.23.3 on Docker 20.10.12 ...
      - kubelet.housekeeping-interval=5m
      - Generating certificates and keys ...
      - Booting up control plane ...
      - Configuring RBAC rules ...
    * Verifying Kubernetes components...
      - Using image gcr.io/k8s-minikube/storage-provisioner:v5
    * Enabled addons: default-storageclass, storage-provisioner
    * kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
    * Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
    mspmanager:~/environment $ 
    ```
