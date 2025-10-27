# Display brightness

https://github.com/jmontleon/pixelbook-fedora?tab=readme-ov-file#brightness

```bash
# Use DPCD for backlight
# Add configuration for kernel module i915
sudo echo 'options i915 enable_dpcd_backlight=1' >> /etc/modprobe.d/i915.conf

# # Update initramfs
sudo dracut -f
```

# Keyboard

https://github.com/grimaldello/pixelbook-eve-2017-Debian/tree/master/udev

```bash
git clone https://github.com/grimaldello/pixelbook-eve-2017-Debian
cd pixelbook-eve-2017-Debian/audio

# copy keyboard mappings db
sudo cp 61-eve-* /usr/lib/udev/hwdb.d/

# copy backlight rules
sudo cp 99-pixelbook-backlights.rules /usr/lib/udev/rules.d/

# Run commands
sudo systemd-hwdb update
sudo udevadm control --reload-rules
sudo udevadm trigger
```

# Audio

https://github.com/WeirdTreeThing/chromebook-linux-audio

```bash
git clone https://github.com/WeirdTreeThing/chromebook-linux-audio
cd chromebook-linux-audio
./setup-audio
```

# Touchpad gestures in Chrome

https://medium.com/@apedik.dev/enabling-swipe-gestures-in-chrome-and-firefox-on-linux-with-wayland-93d2ab7eff51

```bash
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications/
vim ~/.local/share/applications/google-chrome.desktop
```

Edit the .desktop entry and add `TouchpadOverscrollHistoryNavigation` to `--enable-features`:
```
Exec=/usr/bin/google-chrome-stable %U --enable-features=UseOzonePlatform,TouchpadOverscrollHistoryNavigation --ozone-platform=wayland
```
