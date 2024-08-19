## DOWNLOADS AND INSTALLATION

- Download UTM
- Download ISO image for CentOS: CentOS-Stream-9-latest-aarch64-dvd1 (check architecture: ARM64 for Apple M1)
- Create VM with Apple Virtualization (64gb / 4 núcleos) browsing ISO image
- Install
  - Change keyboard config
  - Chose installation disk
  - Stablish password por root user
  - Create a User an enable root permissions

## CONFIGURE VM

- Add shared folder with UTM
- In VM, add a path for creating a shared folder: `sudo mkdir /mnt/shared`

  **(!)** If logged user hasn't got permissions:

  - `$ su -` >> log into root user
  - `$ sudo usermod -aG wheel hgarcia` >> give permissions to user: The wheel group is a special group traditionally used in Unix and Linux systems to control access to superuser privileges.
  - `$ su - hgarcia`
  - `$ ls /mnt`
  - `$ sudo mount -t virtiofs share /mnt/shared` >> this config won't be available after rebooting the VM. To mount it permanently:
    - `$ sudo gedit /etc/fstab ` >> and paste this in the editor:
    - `share	/mnt/shared	virtiofs	rw,nofail	0 0` >> save + exit
