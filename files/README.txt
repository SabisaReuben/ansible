# all you need to know on ansible mount module

# The module controls active and configured mount poins in /etc/fstab
# Attributes:
      backup (yes| no (default)) -> Creates a backup and the timestamp so that you can get the original file
                                   back if you somehow clobbared it incorrectly
      boot (boolean)  yes/no -> file should be mounted on boot. Default is yes.
      
      dump -> Note that if set to null and state set to present, it will cease to work and duplicate entries will be made with subsequent runs.
               Has no effect on Solaris systems. Default: “0”
      fstab (string) -> File to use instead of /etc/fstab. 
                       You should not use this option unless you really know what you are doing.  This might be useful if you need to configure 
		       mountpoints in a chroot environment. OpenBSD does not allow specifying alternate fstab files with mount so do not use this
		       on OpenBSD with any state that operates on the live filesystem.
                       This parameter defaults to /etc/fstab or /etc/vfstab on Solaris.
      stype (string) ->  Filesystem type. Required when state is present or mounted.

      passno (string) -> Passno (see fstab(5)). Note that if set to null and state set to present, it will cease to work and duplicate entries will
                        be made with subsequent runs. Deprecated on Solaris systems. Default: “0”
      src (path)-> Device (or NFS volume, or something else) to be mounted on path.
		   Required when state set to present or mounted.


      State (string / required) ->If mounted, the device will be actively mounted and appropriately configured in fstab.
                          If the mount point is not present, the mount point will be created.
                          If unmounted, the device will be unmounted without changing fstab.
                          present only specifies that the device is to be configured in fstab and does not trigger or require a mount.
                          absent specifies that the device mount’s entry will be removed from fstab and will also unmount the device and remove the mount point.
			  remounted specifies that the device will be remounted for when you want to force a refresh on the mount itself (added in 2.9).
			  This will always return changed=true. If opts is set, the options will be applied to the remount, but will not change fstab.
			  Additionally, if opts is set, and the remount command fails, the module will error to prevent unexpected mount changes.
			  Try using mounted instead to work around this issue.

			  Choices:
			  -------
			  absent
			  mounted
			  present
			  unmounted
			  remounted
