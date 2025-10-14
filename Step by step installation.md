
# 🚀 Docker Installation Guide

Docker Engine can be installed in various ways depending on your environment and needs. Below is a step-by-step guide to get Docker running on your machine, complete with different installation methods.

## 🛠️ Installation Methods

| **Method**                      | **Description**                                                                                            |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| 💻 **Docker Desktop for Linux** | Docker Desktop bundles the Docker Engine, ideal for developers. The easiest and quickest setup.            |
| 📦 **Apt Repository**           | Install Docker from the official Docker apt repository (recommended for production environments).          |
| 🛠️ **Manual Installation**     | Install Docker manually and manage upgrades yourself (for advanced users).                                 |
| 🧪 **Convenience Script**       | Use Docker's script for quick setup in test or development environments. (Not recommended for production). |

---

## 📦 Install Docker Using the Apt Repository (Recommended for most cases)

Before installing Docker Engine for the first time, you need to set up the Docker apt repository. After that, you can install and update Docker directly from the repository.

### Step 1: Set Up Docker's Apt Repository

1. **Add Docker's official GPG key**:

   ```bash
   sudo apt-get update
   sudo apt-get install ca-certificates curl
   sudo install -m 0755 -d /etc/apt/keyrings
   sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   sudo chmod a+r /etc/apt/keyrings/docker.asc
   ```

2. **Add the Docker repository to Apt sources**:

   ```bash
   echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
     $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   sudo apt-get update
   ```

---

### Step 2: Install Docker Packages

To install the latest version of Docker, run the following command:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

🔔 **Note**: Docker service will start automatically after installation. If not, you can start it manually.

---

### Step 3: Enable Docker to Start on Boot

To ensure Docker starts automatically when the system boots, use the following command:

```bash
sudo systemctl enable docker
```

This will create the necessary symlinks to enable Docker to start automatically on boot.

---

### Step 4: Verify Installation

1. **Check Docker status**:

   ```bash
   sudo systemctl status docker
   ```

2. If the service is not running, start Docker manually:

   ```bash
   sudo systemctl start docker
   ```

3. **Run the Hello-World container** to verify Docker is working:

   ```bash
   sudo docker run hello-world
   ```

   If successful, you should see the following message:

   ```
   Hello from Docker!
   This message shows that your installation appears to be working correctly.

   To generate this message, Docker took the following steps:
     1. The Docker client contacted the Docker daemon.
     2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
     3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
     4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

   To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

   Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

   For more examples and ideas, visit:
    https://docs.docker.com/get-started/
   ```

   🎉 You've successfully installed Docker! 🚀

---

### Step 5: Check Running Containers with `docker ps`

To list all running containers on your system, use the following command:

```bash
sudo docker ps
```

This will show a list of containers that are currently running, including container IDs, image names, and status.

---

## 🔍 Gather System Details with `docker info`

The `docker info` command provides detailed information about your Docker setup, including details on the system, storage driver, network, and more.

### Run the Command

To get a summary of the Docker system, execute:

```bash
sudo docker info
```

### Example Output

The output from `docker info` can look like this:

```
Client:
 Context:    default
 Debug Mode: false

Server:
 Containers: 1
  Running: 1
  Paused: 0
  Stopped: 0
 Images: 3
 Server Version: 20.10.7
 Storage Driver: overlay2
  Backing Filesystem: ext4
  Supports d_type: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Plugins:
  Volume: local
  Network: bridge host macvlan null overlay
  Log: awslogs fluentd gcplogs journald json-file logentries syslog
 Swarm: inactive
 Runtimes: runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1.4.6
 runc version: 1.0.0-rc93
 init version: 0.18.0
 Kernel Version: 5.8.0-53-generic
 Operating System: Ubuntu 20.04 LTS
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 7.738GiB
 Name: my-docker-machine
 ID: OXJX:HRRS:4O7D:V4RC:NN0N:5XY3:AZVZ:G6ML:AEYB:XEYT:KOCX
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: <none>
 HTTPS Proxy: <none>
 No Proxy: <none>
 Registry: https://index.docker.io/v1/
 Labels:
  provider=generic
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false
```

### Key Information from `docker info`

Here’s a breakdown of the most important details you can find from `docker info`:

1. **Containers**:

   * `Running`: Number of containers currently running.
   * `Stopped`: Number of containers stopped.
   * `Paused`: Number of paused containers.

2. **Images**:

   * Number of images stored in your Docker installation.

3. **Storage Driver**:

   * The storage driver in use (e.g., `overlay2`, `aufs`, `btrfs`).

4. **Cgroup Driver**:

   * The driver used for controlling resources (e.g., `cgroupfs`).

5. **System Info**:

   * **Kernel Version**: The kernel version of the operating system.
   * **Operating System**: The version of your OS (e.g., `Ubuntu 20.04 LTS`).
   * **Total Memory**: The total system memory available to Docker.
   * **CPUs**: The number of CPU cores available to Docker.

6. **Networking**:

   * Details on the active network drivers and configurations.

---

## 🎉 Congratulations! You’ve Successfully Installed Docker.

You now have Docker up and running on your system. 🐳

---
