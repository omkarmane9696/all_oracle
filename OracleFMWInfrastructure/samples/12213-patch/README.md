Example How to Patch a FMW Infrastructure Image
===============================================
This Dockerfile extends the Oracle FMW Infrastructure image and applies a patch.

**NOTE**: Oracle strongly recommends using the [WebLogic Image Tool](https://oracle.github.io/weblogic-image-tool/userguide/tools/create-image/) (WIT) with the `--recommendedPatches` option, which automatically downloads and applies all the required PSUs, bundle patches, and one-off patches to your 12.2.1.3, and 12.2.1.4 images and updates OPatch. Note that the WebLogic CPU images in OCR already have these patches applied.

## How to build and run
First make sure you have built `oracle/fmw-infrastructure:12.2.1.3`.

Download from My Oracle Support the file [p27117282_122130_Generic.zip](http://support.oracle.com) and place it in the same directory as this README.

To build, run:

        $ docker build --force-rm=true --no-cache=true -t oracle/fmw-infra:12213-p27117282 .

## Verify that the Patch has been applied correctly
Run a container from the image

        $ docker run --name verify_patch oracle/fmw-infra:12213-p27117282

Go into the image

        $ docker exec -it verify_patch /bin/bash

cd OPatch and run:

        ./opatch lspatches

The patch will show in the inventory of applied patches.

# Copyright
Copyright (c) 2019 Oracle and/or its affiliates. All rights reserved.
