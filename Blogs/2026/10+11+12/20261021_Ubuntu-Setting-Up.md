# Setting Up Ubuntu After Fresh Installation

20261021-Wed-1120 // V1

## Installing Software Package Management Tools

A redundant reminder of common sense: Do `sudo apt update` before installation session.

### FUSE
// FUSE support for running AppImage

~~~bash
sudo apt install libfuse2t64
~~~

Note: libfuse2t64 is for Ubuntu 24.04 and newer.

### Flatpak

~~~bash
sudo apt install flatpak
~~~

~~~bash
# Install the GNOME Software plugin
# (optional, if you want a graphical app store integration)

sudo apt install gnome-software-plugin-flatpak
~~~

~~~bash
# Add the Flathub repository
# (the main source for Flatpak applications)

flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
~~~

~~~bash
# Restart the computer to complete the setup and
# make apps visible in your system menu

reboot
~~~

### Synaptic

~~~bash
sudo add-apt-repository universe
sudo apt update # Do these two lines only when the "Universe" repo is missing. This is not common.

sudo apt install synaptic
~~~


## Installing GNOME extensions (for GNOME DE only)

~~~bash
sudo apt install gnome-shell-extension-manager

OR

sudo apt install gnome-shell-extensions ## Comes with some pre-packaged bundle of extensions
~~~

### Name of Extensions

`Top Bar Organizer` by June OR `Top Bar Organizer Plus` by ShibasishPaul // Move items on the top bar

`Apps Menu` by fmuellner // Adds a categorized program menu on the top bar

`Places Status Indicator` by fmuellner // Adds a places (location) menu on the top bar

`System Monitor` by fmuellner // Monitor CPU, RAM, SWAP, netspeed from the top bar

`Command Menu 2` by goldentree1 // Adds highly-customizable menus on the top bar

