# Crosstool-for-Beaglebone-Black
Installing crosstool for Beaglebone black

If the released version is not recent enough for your purposes, you can try to build using the currently developed version. To do that, clone the Git repository:

git clone https://github.com/crosstool-ng/crosstool-ng

You’ll need to run the bootstrap script before running configure:

./bootstrap

Install method

First unpack the tarball and cd into the crosstool-ng-VERSION directory.

Then follow the classical configure recipe: ./configure way:

./configure --prefix=/some/place
make
make install
export PATH="${PATH}:/some/place/bin"

Now, do not remove crosstool-NG sources. They are needed to run crosstool-NG! Stay in the directory holding the sources, and run:

./ct-ng help

