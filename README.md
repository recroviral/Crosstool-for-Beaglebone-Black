# Crosstool-for-Beaglebone-Black

## Inroduction

Crosstool-NG aims at building toolchains. Toolchains are an essential component in a software development project. It will compile, assemble and link the code that is being developed.

## Installing crosstool for Beaglebone black

Before installing crosstool-NG, you may need to install additional packages on the host OS. Specific Drivers required to install crosstool:

    $ sudo apt-get install gperf bison flex texinfo
    $ sudo apt-get install help2man
    $ sudo apt-get install gawk
    $ sudo apt-get install libtool-bin
    $ sudo apt-get install ncurses-dev



There two ways how you can obtain the crosstool-NG sources:
•	by downloading a released tarball;
•	or by cloning the current development repository.

We’ll install crosstool by cloning the current development repository

## Step1:	First, Make new directory to install crosstool-ng and cd into that directory

    $ mkdir crosstool
    $ cd crosstool

## Step2: Cloning a repository

If the released version is not recent enough for your purposes, you can try to build using the currently developed version. To do that, clone the Git repository:

    git clone https://github.com/crosstool-ng/crosstool-ng

## Step3: Now, cd into the crosstool-ng directory. You’ll need to run the bootstrap script before running configure:

    ./bootstrap


## Step4: Then follow the classic configure recipe:./configure 

    $ ./configure --prefix=/home/usr/crosstool/crosstool-ng
    $ make
    $ make install
    $ export PATH="${PATH}:/home/usr/crosstool/crosstool-ng /bin"

## Step5: Now we must configure crosstool-ng for beaglebone black arm-A8 processor

    $ ct-ng show-arm-cortex_a8-linux-gnueabi
    $ ct-ng arm-cortex_a8-linux-gnueabi

## Step6: To Open configuration follow the below command:

    $ ct-ng menuconfig
    
Now you’ll see the window link this. Change the below configuration

version of linix --> 4.4.127
version of binutils --> 2.26.1
version of glibc --> 2.12.1
version of gcc --> 4.9.4
version of gdb --> lower

## Step7: Now, build the configuration using below command

    $ ct-ng build
    
It will take sever minute.

## Step8: Then connect the BBB and write the below command to transfer the file.

first cd into direcory where the file is

    $ sftp debian@192.168.6.2

It will ask for password. Enter the default password:temppwd and transfer the any c file using below command

    sftp>put helloworld.cpp
    sftp>bye

## Step9: Now login to BBB SSH using below command

    $ ssh Debian@192.162.6.2

Write the command ls -l will show you the file which we transfer through sftp.
