# Setting up Docker

Before we start, it might be useful to be aware of what Docker _is_. This is what its Wikipedia article says:

> Docker is a software technology providing operating-system-level virtualization also known as containers, promoted by the company Docker, Inc. Docker provides an additional layer of abstraction and automation of operating-system-level virtualization on Windows and Linux.

Whoa, that's... a lot of complicated words. To make it more simple, Docker is a software that lets you run little separate operating systems under your main operating system. It does a bunch of clever things so that these mini operating systems don't take up that much disk space and RAM, meaning you can run a lot of them at the same time! Why is this useful? Because different applications have different software requirements, and this is a way to effectively isolate different applications into completely different spaces. They can still interact with each other through local networking, and using a software called __Docker Compose__, we can make it even easier to coordinate these applications.

Right, now that we have a bit of clarity as to what Docker is, let's see how to get it onto our computer:

### Windows

Download and install Docker CE from the [Docker Store](https://store.docker.com/editions/community/docker-ce-desktop-windows). The `docker` command and all other Docker-related commands will be available in any Terminal, such as PowerShell.

### MacOS

Same as Windows, download and install it from the [Docker Store](https://store.docker.com/editions/community/docker-ce-desktop-mac).

### Linux

There's some distributions from which it's best to also install Docker from the [Store](https://store.docker.com/search?type=edition&offering=community), such as Ubuntu or Fedora. If it's not available for your distro there, try searching your distribution's package manager for `docker`.

To see if Docker is installed correctly on your system, run the following in a Terminal:

```sh
docker run hello-world
```

It should download a bit of stuff and then display `Hello from Docker!`. Congrats, you installed Docker!

## Cloning the Repositories

Next up, we need to get you set up with the application repositories. For this you'll need Git, which should be preinstalled on MacOS and most Linux distributions. If you're on Windows, just download and install it from the [website](http://git-scm.com). Then, open a terminal and type:

```sh
mkdir data-mining
cd data-mining
git clone https://github.com/data-mining-code/compose
git clone https://github.com/data-mining-code/frontend
git clone https://github.com/data-mining-code/broker
```

This will set up all of the local components you need to run the Docker Compose network. Now, move into the directory and start the network:

```sh
cd compose
docker-compose up -d
```

The `-d` flag ensures that the network keeps running in the background, not blocking your command line. If you want to stop or restart the network, you can use these commands:

```sh
# For restarting:
docker-compose restart
# You can also restart a single component
docker-compose restart broker
# Same goes for stopping:
docker-compose stop
# Or:
docker-compose stop broker
```

The frontend will now be available in your browser under the URL http://localhost:8080. Happy hacking!
