# Ly - a TUI display manager
# Purple_matrix_Fork

Ly is a lightweight TUI (ncurses-like) display manager for Linux and BSD.

![purplelymatrix](https://github.com/user-attachments/assets/3e04dcbc-517f-4d12-a371-29287359d30c)


## Dependencies
- Compile-time:
  - zig 0.14.0
  - libc
  - pam
  - xcb (optional, required by default; needed for X11 support)
- Runtime (with default config):
  - xorg
  - xorg-xauth
  - shutdown
 
### Archlinux/-based
use this [PKGBUILD](https://github.com/killajoe/ly/blob/main/PKGBUILD)



## Cloning and Compiling
Clone the repository
```
$ git clone https://github.com/killajoe/ly.git
```
``` 
cd ly
makepkg -si
``` 

Enable the service
```
# systemctl enable ly.service
```

If you need to switch between ttys after Ly's start you also have to
disable getty on Ly's tty to prevent "login" from spawning on top of it

```
# systemctl disable getty@tty2.service
``` 



## Configuration
You can find all the configuration in `/etc/ly/config.ini`.
The file is commented, and includes the default values.

to get matrix used you need to set config.ini option:

``` 
# The active animation
# none     -> Nothing
# doom     -> PSX DOOM fire
# matrix   -> CMatrix
# colormix -> Color mixing shader
animation = matrix
``` 
## Controls
Use the up and down arrow keys to change the current field, and the
left and right arrow keys to change the target desktop environment
while on the desktop field (above the login field).

## .xinitrc
If your .xinitrc doesn't work make sure it is executable and includes a shebang.
This file is supposed to be a shell script! Quoting from xinit's man page:

> If no specific client program is given on the command line, xinit will look for a file in the user's home directory called .xinitrc to run as a shell script to start up client programs.

On Arch Linux, the example .xinitrc (/etc/X11/xinit/xinitrc) starts like this:
```
#!/bin/sh
```

## Tips
- The numlock and capslock state is printed in the top-right corner.
- Use the F1 and F2 keys to respectively shutdown and reboot.
- Take a look at your .xsession if X doesn't start, as it can interfere
  (this file is launched with X to configure the display properly).

## Supported Wayland Environments
 - budgie
 - cosmic
 - deepin
 - enlightenment
 - gnome
 - hyprland
 - kde
 - labwc
 - niri
 - pantheon
 - sway
 - weston

## Supported X11 Environments
 - awesome
 - bspwm
 - budgie
 - cinnamon
 - enlightenment
 - kde
 - leftwm
 - lxde
 - mate
 - maxx
 - pantheon
 - qwm
 - spectrwm
 - windowmaker
 - xfce
 - xmonad


## Additional Information
The name "Ly" is a tribute to the fairy from the game Rayman.
Ly was tested by oxodao, who is some seriously awesome dude.
