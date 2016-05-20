# ##########################################################
#
# VxWorks-7 Bluemix SDK User Guide
#
# ##########################################################

### Overview

This Readme file provide a quick summary of building and running IBM Bluemix SDK residing on the
device. The IBM Bluemix SDK means the IoT embedded C client library for interacting with the IBM
Watson Internet of Things Platform. The embedded C client library is not provided in VxWorks-7
RPM packages or DVDs by default. Need to install this library on VxWorks-7.

### Installation

Before using this SDK in VxWorks-7, first you must fetch SDK source codes from maintainer web site 'https://github.com/ibm-messaging/iotf-embeddedc.git'. And must apply a patch with some tiny changes in order to make Bluemix SDK compatible for VxWorks-7. Some unnecessary files are removed from SDK directory. All these steps are executed by running a script setup.sh in bluemix/src directory.


