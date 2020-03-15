# tolenv

![tolenv_banner](docs/tolenv_banner.png)

A tolset that supports various environments using Docker.

It is compatible at the source level of C and assembly with the contents of "In 30 days! OS self-made introduction" written by Hidemi Kawai, but the Makefile needs to be partially rewritten. We will create a document on how to rewrite.

Harib27f on the last day, rewritten to match this tolenv[HariboteOS/harib27f](https://github.com/HariboteOS/harib27f)Please refer to this as it is open to the public.

## preparation

The following must be installed:

- [Docker](https://www.docker.com/get-started)
- [QEMU](https://www.qemu.org)
  - No installation required if emulation function is not required
  
## Environmental check

It is OK if the version information comes out when you execute the command as follows (the output below is from a verified environment, it may be slightly different).

```
$ docker --version
Docker version 19.03.5, build 633a0ea
```
## Download and unpack

Clone this repository or download and extract it as a zip file. The hierarchy where this document (`README.md`) is located is described below as the project root.

- / Project root
  - Makefile
  - README.md
  - harib27f/
  - z_tools/
  - z_tools_linux/
  
## Get Docker image
Get the Docker image needed to run the development tools. This step only needs to be done once after cloning or downloading the repository. There is no harm in running it many times.

* Open a terminal and `cd` to the project root
* `make pull`

The sample of the execution result looks like this.

```
$ make pull
Using default tag: latest
latest: Pulling from hikalium/ubuntu-with-libc-i386
423ae2b273f4: Already exists 
de83a2304fa1: Already exists 
f9a83bce3af0: Already exists 
b6b53be908de: Already exists 
5b278adba46d: Pull complete 
e3c3960e082b: Pull complete 
Digest: sha256:100dffd9bbf940f1ed9e413927ee12ebfa096bcec00148e94d2ac9b0cf4e0d7a
Status: Downloaded newer image for hikalium/ubuntu-with-libc-i386:latest
docker.io/hikalium/ubuntu-with-libc-i386:latest
```

If the image has already been pulled, you will get the following output:

```
$ make pull
Using default tag: latest
latest: Pulling from hikalium/ubuntu-with-libc-i386
Digest: sha256:100dffd9bbf940f1ed9e413927ee12ebfa096bcec00148e94d2ac9b0cf4e0d7a
Status: Image is up to date for hikalium/ubuntu-with-libc-i386:latest
docker.io/hikalium/ubuntu-with-libc-i386:latest
```

## Launch development environment

You need to do this not only the first time, but every time you make down or restart your computer. (Launch the docker container used for the build.)

* Open a terminal and `cd` to the project root
* `make up`

The sample of the execution result looks like this.

```
$ make up
b4d30d8e4c788a2f046eadf5417eec607f130504f4da512b3cc12dc5e068a869
OK!
```

If it has already been up, the following response will be returned.

```
$ make up
Already up
```

## development

Create an OS folder (ex: `harib27f`) in the same hierarchy as 'z_tools /', and develop there as usual. Although it is compatible at the source level of C and assembly with the contents described in the book of Hidemi Kawai's "You can do it in 30 days! Introduction to OS self-made", Makefile needs to be partially rewritten. We will create a document on how to rewrite.

## Termination development environment

If you want to stop the docker container after work is completed, perform the following procedure.

* Open a terminal and `cd` to the project root
* `make down`

The sample of the execution result looks like this.

```
$ make down
tolenv
tolenv
tolenv container deleted
```

If it has already been down, the following response will be returned.

```
$ make down
Error response from daemon: No such container: tolenv
Already down
```

# thank
About the icon of the project, the one downloaded from hideyosi's [KaOS material collection] (http://osask.hideyosi.com/kaos/kaos.html) is modified and used under the KL-01 license. You.

# license
MIT License
