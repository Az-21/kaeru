# Hyper-V

## Tips

Set these individually for each VM during initialization or after creation

- Disable secure boot
- Disable snapshots
- Unmount ISO (after installation)
- Enable **Guest services** in **Integration Services**

## Custom Resolution on KDE Wayland

```sh
# :: Windows Host :: PowerShell Admin
Set-VMVideo -VMName "VirtualMachineName" -HorizontalResolution 3840 -VerticalResolution 2160 -ResolutionType Single
```

```sh
# :: VM :: bash/zsh/nushell
kscreen-doctor output.1.addCustomMode.3840.2160.60020.full
```

!!! note

    Making assumption that Hyper-V passes monitor named `1`. To double check the output of `kscreen-doctor --outputs`.

!!! tip

    The `60020` value depends on the display's clock rate. It is more of a trial and error to get this to 60Hz flat. Try `+/-10` (more if needed) to hit that flat 60Hz.

!!! warning

    Refresh rate higher than 60Hz are not recommened right now. I've tried 240Hz, but it is verry laggy.
