# Framework Arch Linux Tools
Personal scripts for framework 13 on Arch Linux, mostly FN key stuff.

## Screen Brightness

https://wiki.archlinux.org/title/backlight#ACPI

1. Let non-root w/ `video` group write to the brightness file
2. Give your user a `video` group

```bash
# /etc/udev/rules.d/backlight.rules

ACTION=="add", SUBSYSTEM=="backlight", RUN+="/bin/chgrp video $sys$devpath/brightness", RUN+="/bin/chmod g+w $sys$devpath/brightness"

---

sudo usermod -aG video USERNAME
```

### sxhkd config:

```
# framework brightness
XF86MonBrightnessUp
    python ~/00/framework_tools/brightness.py +
XF86MonBrightnessDown
    python ~/00/framework_tools/brightness.py -
```

---

## TODO

- Rewrite in rust
- Monitor settings
- Desktop background setter (feh wrapper)
- Volume script for sxkhd
- Add something to the FN+12, maybe a settings launcher
