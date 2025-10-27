# Backlight brightness
```bash
# Use DPCD for backlight
# Add configuration for kernel module i915
sudo echo 'options i915 enable_dpcd_backlight=1' >> /etc/modprobe.d/i915.conf

# # Update initramfs
sudo dracut -f
```

# Keyboard
```bash
# copy keyboard mappings db
sudo cp 61-eve-* /usr/lib/udev/hwdb.d/

# copy backlight rules
sudo cp 99-pixelbook-backlights.rules /usr/lib/udev/rules.d/

# Run commands
sudo systemd-hwdb update
sudo udevadm control --reload-rules
sudo udevadm trigger
```
