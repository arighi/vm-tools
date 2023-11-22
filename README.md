#                  arighi's VM helper scripts

A collection of small helper scripts to automate VM deployment for testing
using Ubuntu cloud images.

## Requirements

 $ sudo apt install uvtool-libvirt libvirt-client qemu-system-x86

## Tools

 - vm-deploy: deploy a new VM

 - vm-setup: setup a new VM to be used as test box

 - vm-push: copy a file to a VM deployed via vm-deploy

 - vm-shell: ssh into a deployed VM

 - vm-destroy: delete a previously deployed VM

### Example (typical testing workflow)

```
 # Deploy a new VM based on Ubuntu Noble 24.04 (or start a deployed VM):
 $ vm-deploy noble
 (press "CTRL ]" to exit from virsh console)

 # List deployed VMs
 $ vm-ls

 # Initialize the deployed instance with some basic development tools
 $ vm-setup noble

 # Copy a FILE into the deployed instance
 $ vm-push noble FILE

 # ssh into the deployed instance
 $ vm-shell noble

 # Destroy the deployed instance
 $ vm-destroy noble
```
