# Packer Templates

My collection of packer templates I use for VirtualBox and KVM images


## Building

Assuming you have all the necessary software installed the following command can be used to have packer build a qcow2 file

```console
foo@bar:~$ packer build -only <builder-name> -var-file vars.json <template-name>.json
```

The resulting image will be spat out within the appropriate `output/<builder-name>` directory.


### Supported formats

Builders included in each template produce any of the following image formats

* OVA
* QCOW2


### SSH

The created VM will be bootstrapped with the provided authorized keys file. This can be found in each sub-directory's `provision` folder.
For easy access to the created machine simply drop your SSH public key in that file.

If you want to configure the SSH port to something non-standard each template has a `custom_ssh_port` variable which can be used.


### Default passwords

Images are created with the below set of default users and passwords. Be sure to change them after deployment!

| User | password |
| ---- | -------- |
| `packer` | `packer` |
| `root` | `CHANGEME` |


## Prerequisites

The following packages must be present on your system for this project to be usable

* [Packer](https://www.packer.io/)
* [VirtualBox](https://www.virtualbox.org/)
* [QEMU](https://www.qemu.org/)


## TODO

* Support multiple preseed / kickstart configs for things like
    * More complicated partitioning schemes
    * luks
* Consolidate duplicate files
