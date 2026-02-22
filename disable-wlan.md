### To fully disable a wifi interface (in progress)

Disconnecting and disabling auto-connect in KDE's NetworkManager is not enough to stop the journalctl spam.

Disabling wpa_supplicant.service does not work either.

`ip link set wlan0 down` does not do much.

This [entry from the Arch wiki](https://wiki.archlinux.org/title/NetworkManager#Ignore_specific_devices) seems to do it:

In `/etc/NetworkManager/conf.d/unmanaged.conf`,
```
[keyfile]
unmanaged-devices=interface-name:wlan0
```

That solves most of the log spam. But plasma (either plasmashell or systemsettings) keeps writing "Wireless scan on "wlan0" failed: "Scanning not allowed while unavailable"". Deleting wlan0 from the System Settings > Networking interface does nothing. Deleting ~/.chache/systemsettings fixes the issue (solution found on this [old bug report](https://github.com/NixOS/nixpkgs/issues/125545#issuecomment-906809973)).

### TODO
- See on next reboot
- If that still works, undo all previously attempted changes; and see if that still works
- If it does implement an automatized solution ("unignore" wlan0 on eth unplug, "reignore" on plug)
- Check: was deleting wlan0 from the System Settings necessary? (that makes seamlessly ignoring/unignoring it more difficult)
