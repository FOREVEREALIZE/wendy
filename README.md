# Wendy
Wendy is my simplistic approach to running Windows-only apps on Linux-based OSes without using Wine, which sometimes doesn't quite work as intended.

## How?
Wendy uses Vagrant-managed VirtualBox VMs inside of Docker containers. This may seem counterintuitive at first, but it makes a lot of sense. Let's see why:

### Scenario 1: Just using Docker containers
Just using Docker containers is not good enough as you cannot run Windows-based images on Linux-based OSes and as such cannot run the Windows-only app inside of a Windows container.

### Scenario 2: Just using Vagrant-managed VirtualBox VMs
Just using Vagrant-managed VirtualBox VMs would be fine if it was not because a bare Windows install weighs a whopping **15GB** which, if you run 4 programs, already equates to **60GB** of your hard drive yeeted off of your control. This is, of course, not ideal.

### Scenario 3: Using Vagrant-managed VirtualBox VMs inside Docker containers
Using Vagrant-managed VirtualBox VMs inside Docker containers may seem like it does not solve the problem until you look at how Docker handles hard drives. You see, in Docker there are two types of storage: The image, which is a read-only file (or set of files) containing the base OS, and the volume, a read-write layer which stores all of the changes the container has made to the image. When you look at that, you see why Vagrant-managed VirtualBox VMs inside Docker containers make sense. It is because, as the base Windows install is part of the Docker image, we will only store the apps and changes they make to the volume, but will not waste tens of gigabytes of data in storing countless copies of Windows.
