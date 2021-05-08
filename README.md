# Linux for MPU/FPGA Module (MFM)
Embedded Linux board support for the **MFM** and its associated example applications.

# Board Profiles

This primarily consists of "board profiles", which are scripts and configuration files which create a simple recipe for creating *example* Bootstrap+U-Boot+Kernel+RootFS for the MFM and whatever attached options/peripherals for a given application.

Currently, the following board application profiles are implemented:

| Board Profile | {brd}   | Comments                                                     |
| ------------- | ------- | ------------------------------------------------------------ |
| MFM Basic     | `basic` | MFM alone, with no front-end attached, nor any base board assumed.  Other Board Profiles will likely refer to this profile, primarily via symbolic links. |
| Oscilloscope  | `scope` | [TBD] MFM attached to Instrument base board + LCD + Arrow beScope (or compatible).  This is the OS support base for a 2-channel oscilloscope. |
|               |         |                                                              |



# Build Environment

The cross-build environment is expected to be desktop Linux.  Testing has only been performed on **Ubuntu 20.10** (x86_64).  This distribution/environment is assumed for the remainder of this document, and will be referred to as the "Host".

These board profiles rely on the following repositories (and their associated dependencies):

- linux4sam Buildroot:  [https://github.com/linux4sam/buildroot-at91](https://github.com/linux4sam/buildroot-at91)

Note the following Host applications are required:

* `build-essential git ncurses-base libncurses5 libncurses5-dev libssl-dev libz-dev`
* Other packages may be required; it is recommend to run buildroot `make`, and respond appropriately to any missing-application error messages



# Build Process

## Setup

A shell script is provided to simplify the setup process, given the Board Profile **{brd}**:

```setup_bp {brd}```

The process is as follows:

1. Clone `buildroot_at91` repository, checking out the currently supported version
2. Apply the buildroot configuration from the {brd} directory

The script completed, follow the instructions to start the actual build.



## Output

After buildroot `make` runs to completion, the following directories/files of note are created:



