# kvm-passthrough-backup

Some related files for KVM PCI passthrough that I actively use.

## Files Explanation

### find-dgpu.sh

Print PCI devices grouped by IOMMU groups.

### load_nvidia

Rebinds the GPU to the host `nvidia` driver. Used to restore GPU access to the host after the VM shuts down.

### load_vfio

Isolate the GPU from the host by binding it to the `vfio-pci` driver. This will not work without [Loading vfio-pci early](https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF#Loading_vfio-pci_early) configured.

### modifications

A simple description of my setup process.

### qemu

A hook script handling machine prepare, started, and release stages. It will hide specified partition and launch [Scream](https://github.com/duncanthrax/scream) when machine boots. This file must be placed in `/etc/libvirt/hooks/` and made executable.

### win10-vfio.xml

Libvirt XML with PCI passthrough enabled.
