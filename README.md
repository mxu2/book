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
    cd src <br>
    ./setup.sh <br>
  
### VSB and VIP creation

VSB and VIP could be created in workbench UI environment as well as command line with vxprj tool. Here just list how to create them using vxprj tool, and take itl_quark BSP as an example.

* VSB create:
        vxprj vsb create -force -bsp itl_quark vsb_PENTIUM_32_up -S
        cd vsb_PENTIUM_32_up
        vxprj vsb add IBM_BLUEMIX
        make -j

* VIP create:
        vxprj create -force -vsb vsb_PENTIUM_32_up itl_quark gnu vip_quark_kernel -profile PROFILE_STANDALONE_DEVELOPMENT
        cd vip_quark_kernel
        vxprj component add DRV_VXBEND_QRK_GMAC
        vxprj component add INCLUDE_SHELL INCLUDE_NETWORK INCLUDE_IFCONFIG INCLUDE_PING
        vxprj component add INCLUDE_IBM_BLUEMIX
        vxprj parameter set DNSC_PRIMARY_NAME_SERVER "\"128.224.160.11\""
        vxprj parameter set DNSC_SECONDARY_NAME_SERVER "\"147.11.57.128\""
        
A sample iotfclient test sample is provided in cfg/usrBluemixDemo.c and bluemix/src directory, it can be used to connect the device to Bluemix cloud, publish events to the cloud and subscribe commands from Bluemix cloud. To enable this demo, you need to add INCLUDE_BLUEMIX_DEMO component as below:
        vxprj component add INCLUDE_BLUEMIX_DEMO


