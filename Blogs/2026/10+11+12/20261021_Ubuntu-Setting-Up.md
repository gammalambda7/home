# Setting Up Ubuntu-based OS After Fresh Installation

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

### Snapd

~~~bash
sudo apt install snapd
sudo snap install core
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

`Battery time` by pomoke // Show battery remaining time in the Quick Settings menu, replacing the battery percentage (duplicated with the percentage already on the top bar)

## Setting the default app

### Default browser

~~~bash
# Using Thorium-Shell browser as an example:

xdg-settings set default-web-browser thorium-shell.desktop
~~~

Additional commands for reference:

~~~bash
# Check to verify the default browser:

xdg-settings get default-web-browser
~~~

~~~bash
# Search for the .desktop file name
# (replace 'keyword' with the actual search entry, e.g., 'thorium',
# or, 'chrome|firefox|brave|edge|opera|vivaldi|chromium|tor|waterfox|librewolf|browser')

ls /usr/share/applications \
 /var/lib/snapd/desktop/applications \
 /var/lib/flatpak/exports/share/applications \
 ~/.local/share/applications 2>/dev/null | grep -iE 'keyword'
~~~

## Setting up additional input method

Choose between `IBus` (simple, easy; native to GNOME; recommended) or `Fcitx5` (advanced, esp. for CJK; native to KDE Plasma)

### IBus

~~~bash
sudo apt install ibus-libpinyin

# Log out and log back in before going to
# `Settings` > `Keyboard` > `Add Input Source` > `...` > `other` > `Inteligent Pinyin`
# Double pinyin available in input setting
# `Super + Space` for input switch
~~~

### Fcitx5

~~~bash
sudo apt install fcitx5 fcitx5-config-qt fcitx5-chinese-addons

# Set Fcitx5 as the default input system:
im-config -n fcitx5

# Need to log out and then back in

# Open the configuration tool
fcitx5-configtool

# `Ctrl + Space` for input switch
~~~

### Quick comparison

> (Credit: Gemini, 202611131753)

| Feature               | IBus (`ibus-libpinyin`)                           | Fcitx5 (`fcitx5-chinese-addons`)                                                |
| --------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------- |
|  |
| Default Status        | Pre-installed on standard Ubuntu (GNOME).         | Requires manual installation and setup.                                         |
| Desktop Integration   | Native GNOME top bar and lock screen support.     | Native to KDE Plasma; requires extensions on GNOME.                             |
| Wayland Support       | Seamless out-of-the-box support.                  | Good support, though sometimes requires extra environment flags.                |
| Typing & Dictionaries | Basic local dictionary and word prediction.       | Supports custom dictionaries (`.dict`), cloud Pinyin, and better phrase memory. |
| Customization         | Minimal UI options; follows system theme.         | Highly customizable skins, font sizes, and candidate window layouts.            |
| App Compatibility     | Works reliably across GTK, Qt, and Electron apps. | Works well everywhere, though occasionally needs env variables for older apps.  |

## Setting up individual apps

### Snipaste

The AppImage version of Snipaste does not seem to consistently monitor keyboard shortcuts.

To use Snipate with keyboard shortcuts,

Set a custom shortcut in Settings:

|---- Command: `/path/to/program/Snipaste.AppImage snip`

|---- Name: `Snipaste` (as an example)

|---- Shortcut: `Shift + Ctrl + Alt + S` (suggested)

