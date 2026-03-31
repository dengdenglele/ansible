# ansible

## Learn Linux TV tutorial
- YouTube [playlist](https://www.youtube.com/playlist?list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70)

### Workstation for running Ansible playbooks
- Any PC with ansible installed
- Git for version control

### Setup VMs (via cloud image) on proxmox
- Use template creation on proxmox according to LLTV [tutorial](https://www.youtube.com/watch?v=MJgIm03Jxdo)
- 2 * Ubuntu 24.04 LTS
  - Naming: `ubuntu-1` and `ubuntu-2`
  - Get cloudimg [here](https://cloud-images.ubuntu.com/minimal/releases/noble/release/)
  - Copy link for `ubuntu-24.04-minimal-cloudimg-amd64.img`
  - Do not forget to install `qemu-guest-agent` package, and rboot &rarr; makes `IPs` in `Summary` section visible
- 1 * Fedora Cloud 43
  - Get cloudimg [here](https://fedoraproject.org/cloud/download)
  - Copy link for `Fedora Cloud Base 43 QEMU qcow2`
- 1 * Rocky Linux machine
- Login to proxox as root via ssh
    ```
    # Download cloud images
    wget <url link to image>
    # Enable VGA console in proxmox as root with (needed for Ubuntu 22.04 and older)
    qm set <VM-ID> --serial0 socket --vga serial0
    # Rezise cloud images to 32G
    qemu-img resize <image-name>.<img/qcow2> 32G
    # Import disks
    qm importdisk <VM-ID> <image-name>.<img/qcow2> local-<storage-name>
    ```
- In Proxmox do not forget ot activate `Discard` and `SSD emulation`
- Adjust boot order, put disk after cdrom
- Assign static IPs
