MAC OS
======

comnnect usb drivve

Identify the device path with the diskutil list command. The device path has the format of /dev/disknumber, where number is the number of the disk. 

`$ diskutil list
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.3 GB   disk0
   1:                        EFI EFI                     314.6 MB   disk0s1
   2:                 Apple_APFS Container disk1         499.8 GB   disk0s2

/dev/disk1 (synthesized):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      APFS Container Scheme -                      +499.8 GB   disk1
                                 Physical Store disk0s2
   1:                APFS Volume MacOS - Data            382.4 GB   disk1s1
   2:                APFS Volume Macintosh HD            11.1 GB    disk1s2
   3:                APFS Volume Preboot                 1.9 GB     disk1s3
   4:                APFS Volume Recovery                1.6 GB     disk1s4
   5:                APFS Volume VM                      5.4 GB     disk1s5
   6:                APFS Volume MacOS Catalina          8.8 GB     disk1s6
   7:              APFS Snapshot com.apple.os.update-... 8.8 GB     disk1s6s1

/dev/disk2 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                            OEMDRV                 *2.0 GB     disk2`

Use the diskutil unmountDisk command to unmount the flash drive’s filesystem
`$ diskutil unmount /dev/disk2
Volume OEMDRV on disk2 unmounted`

Use dd to write to the disk
`╰─$ sudo dd if=./dd-megaraid_sas-07.719.03.00-1.el8_6.elrepo.iso of=/dev/disk2 status=progress

1368+0 records in
1368+0 records out
700416 bytes transferred in 0.671665 secs (1042806 bytes/sec)`



