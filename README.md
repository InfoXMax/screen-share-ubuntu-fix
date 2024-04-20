# Screen Sharing Fix for Ubuntu 22.04

If you're experiencing issues with screen sharing on Ubuntu 22.04 across various applications such as Discord (in my case) Zoom, Teams, Google Meet, AnyDesk, and others, it's likely due to Ubuntu 22.04's default display server, Wayland, which doesn't fully support screen sharing in some applications. This guide will help you fix the problem by switching from Wayland to Xorg.

## Checking Your Display System

Before proceeding with the fix, let's verify which display system your Ubuntu installation is currently using. Open a terminal and enter the following command:

```bash
echo $XDG_SESSION_TYPE
```

If the output is `wayland`, your system is currently using Wayland.

## Fixing Screen Sharing

To enable screen sharing in various applications, including Discord, Zoom, Teams, Google Meet, AnyDesk, etc., follow these steps:

1. Open the `custom.conf` file using a text editor with superuser privileges. You can use nano in the terminal:

```bash
sudo nano /etc/gdm3/custom.conf
```

2. Uncomment the line `WaylandEnable=false`. This action disables Wayland and enables Xorg.

3. Save the file and exit the text editor.

4. Reboot your system to apply the changes:

```bash
sudo reboot
```

5. After rebooting, open a terminal again and check if the display system has switched to X11 by running:

```bash
echo $XDG_SESSION_TYPE
```

The output should now be `x11`.

6. If the output is still `wayland`, you may need to restart the display manager. Run the following command:

```bash
sudo systemctl restart gdm
```

After following these steps, screen sharing should now work in various applications on Ubuntu 22.04, including Discord, Zoom, Teams, Google Meet, AnyDesk, and others. You can confirm this by testing screen sharing within your desired application.
