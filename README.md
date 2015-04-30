archiso
=======
This is the archiso testing build for the new OB CLI version of Evo/Lution.



**USAGE INSTRUCTIONS:**

**Switching between 32 and 64 bit ISO creation**

NOTE: There is no UEFI support for 32bit ISOs.

1. Clear out the pacman cache (prevents mixing of 32 and 64 bit versions of the same packages)
   ```
   pacman -Scc
   ```

2. Edit `/syslinux/archiso_sys_both_inc.cfg`
   * Unhash the desired system build, and hash the undesired one.

   _The example below is for 64bit:_
      ```
      INCLUDE boot/syslinux/archiso_sys64.cfg
      #INCLUDE boot/syslinux/archiso_sys32.cfg
      ```

   _This is for 32 bit:_
      ```
      #INCLUDE boot/syslinux/archiso_sys64.cfg
      INCLUDE boot/syslinux/archiso_sys32.cfg
      ```

3. Edit the `packages.*` files
   * Hash all packages in one file and unhash them in the other.

4. Run `./build.sh` for _64 bit_, or `./build-32.sh` for _32 bit_.
