# [Evolution of Docker from Linux Containers](https://www.baeldung.com/linux/docker-containers-evolution) 
#docker #baeldung

# 3. Early Evolution of Containers
The main concept of containers is to **provide isolation to multiple processes running on the same host**.

The tool _chroot_, introduced in 1979, made it possible to change the root directory of a process and its children to a new location in the filesystem.

# 4. Understanding Linux Containers
[Linux Containers](https://linuxcontainers.org/), often referred to as LXC, was perhaps the first implementation of a complete container manager. It’s **operating-system-level virtualization that offers a mechanism to limit and prioritize resources** like CPU and memory between multiple applications. Moreover, it allows complete isolation of the application’s process tree, networking, and file systems.

## 4.1. Introducing Control Groups (cgroups)
The _cgroups_ feature was started by Google under the name _process containers_ way back in 2007 and was merged into the Linux kernel mainline soon after.

Basically, _cgroups_ provide a unified interface for process isolation in the Linux kernel.

## 4.2. Introducing Namespaces
Another Linux kernel feature that is critical for LXC to provide process isolation is [namespaces](https://man7.org/linux/man-pages/man7/namespaces.7.html)

it **allows us to partition kernel resources such that one set of processes is able to see resources that aren’t visible to other processes**. These resources include process trees, hostnames, user mounts, and file names, among others.

This is in fact an evolution from _chroot_, which allows us to assign any directory as the root of the system for a process. However, there were issues with _chroot_, and applications in different _namespaces_ could still interfere. Linux _namespaces_ provide more secure isolation for different resources and hence came to be the foundation of the Linux container.

# 5. Arrival of Docker
Although LXC provides a neat and powerful interface at the userspace level, it’s still not that easy to use, and it didn’t generate mass appeal. This is where [Docker](https://www.docker.com/) changes the game. While abstracting most of the complexities of dealing with kernel features, it **provides a simple format for bundling an application and its dependencies into containers**.
