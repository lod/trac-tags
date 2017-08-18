# Debian package for trac-tags-0.10dev

trac-tags lives at http://trac-hacks.org/wiki/TagsPlugin

The current Debian package is 0.7+svn12392-1, this is incompatible
with the current Debian track package 1.2+dfsg-1

The code here packages up the latest trac-tags version which is compatible.

Upgrade need has been flagged in the Debian bug tracker at https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=865967


## Build instructions

I recommend build a source package, then using that to build the binary.

### Build source package

From the repository directory

  $ make -f debian/rules get-orig-source
  $ tar xzf trac-tags_0.10dev+svn16296.orig.tar.gz 
  $ mv trac-tags_0.10dev+svn16296.orig.tar.gz ../
  $ dpkg-source -i'.git|README.md' -b .

This will generate three files in the parent directory:

  * trac-tags_0.10dev+svn16296-1.dsc
  * trac-tags_0.10dev+svn16296-1.debian.tar.xz
  * trac-tags_0.10dev+svn16296.orig.tar.gz

### Build binary package    

From the parent directory

  $ dpkg-source -x trac-tags_0.10dev+svn16296-1.dsc
  $ cd trac-tags-0.10dev+svn16296/
  $ debuild -us -uc

This will generate the following files in the parent directory:

  * trac-tags_0.10dev+svn16296-1_all.deb
  * trac-tags_0.10dev+svn16296-1_amd64.build
  * trac-tags_0.10dev+svn16296-1_amd64.buildinfo
  * trac-tags_0.10dev+svn16296-1_amd64.changes

### Install the binary package

From the parent directory

  $ sudo dpkg -i trac-tags_0.10dev+svn16296-1_all.deb

### Clean the repository directory

From the repository directory

  $ git clean -d -f
