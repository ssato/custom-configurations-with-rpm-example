About
=======

This is a collection of files to make a RPM does advanced customizations to RPM
based systems with that RPM.

The result RPMs will be used by installing into customized system images
composed using Image Builder aka composer (lorax-composer) for example.

The %install section in the RPM SPEC, package.spec.in, may show you some
concrete examples doing advanced customization cannot done using Image Builder.

Build
==========

You can make a SRPM as follows.

#. mkdir build
#. cd build
#. cmake ..
#. make srpm

License
=========

MIT

Author
=========

Satoru SATOH <satoru.satoh @ gmail.com>
