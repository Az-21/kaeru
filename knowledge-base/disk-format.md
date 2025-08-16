# MBR FAT32

> [!TIP]
> Useful when flashing firmware on _dumb_ devices.

## Start Diskpart Utility
```cmd
::# PowerShell or CMD
diskpart
```

```cmd
:: Get all connected disks
list disk
```

```r
# Output should look like

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          953 GB  1024 KB        *
  Disk 1    Online           14 GB      0 B
```

> [!TIP]
> If you don't see a `*` against your USB device (flashdrive/pendrive) under "Gpt" column, it is most likey already using MBR partition. You can use this again to verify if the formatting was successful.

## Convert to MBR Partition and Format as FAT32

> [!CAUTION]
> Double check the disk you're working on.
> 
> **You will brick your device if you select the disk where OS is installed.**

```cmd
:: Select disk to work on
select disk 999
::          ^ Replace this with your flashdrive's Disk ID
:: Again, you will brick your device if you select the disk where OS is installed
```

```cmd
clean
```

```cmd
convert mbr
```

```cmd
create partition primary
```

```cmd
select partition 1
```

```cmd
active
```

```cmd
format fs=fat32 label=FLASHDRIVE quick
```

```cmd
exit
```
