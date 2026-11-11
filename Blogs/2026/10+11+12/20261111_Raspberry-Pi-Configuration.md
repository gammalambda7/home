# Configure the Raspberry Pi, especially the Desktop OS
20261111-WED-0758 // V1

## Purpose
Many configurations are missing GUI, though the Raspberry Pi Desktop OS supporting the x86_64 is nice to have and fun to play with.

## Material

Hardware:

____Thinkpad T15

Software:

____Raspberry Pi OS <br>
____|---- Release date	13 Oct 2026 <br>
____|---- System	64-bit <br>
____|---- Kernel version	6.12 <br>
____|---- Debian version	13 (trixie) <br>

## Method

### Touchpad configuration

Note: No GUI configuration exists for the following settings, as of the date of update.

Note: Adjusting the bare-minimal mouse config through the GUI ("Control Centre", command: rpcc) disrupts the following procedure, which will have to be redone afterwards.

- Open the configuration file in the terminal:

~~~bash
# Create the Directory and Copy the Template, if rc.xml does not exist in ~/.config/labwc/
# This is optional but recommended

mkdir -p ~/.config/labwc
cp /etc/xdg/labwc/rc.xml ~/.config/labwc/rc.xml

# Open the configuration

nano ~/.config/labwc/rc.xml
~~~

- Update the <libinput> Section (choose one set of settings)

~~~xml
  <libinput>
    <device category="default">
      <clickMethod>clickfinger</clickMethod>
      <tap>no</tap>
      <scrollMethod>edge</scrollMethod>
    </device>
  </libinput>
~~~

OR

~~~xml
  <libinput>
    <device category="default">
      <clickMethod>buttonAreas</clickMethod>
      <tap>yes</tap>
      <scrollMethod>twofinger</scrollMethod>
    </device>
  </libinput>
~~~

Note: <br>
____clickMethod: <br>
____|----"clickfinter": Right click by two-finger click of the touchpad<br>
____|----"buttonAreas": Right click by click the lower right corner of the touchpad<br>

Note: If there are already other settings, just copy the `<setting>value</setting>` block inside the `<libinput><device category="default">...</device></libinput>` section

- Apply Changes (after saving the `rc.xml`, of course)

~~~bash
labwc --reconfigure
~~~


### Put system to sleep (suspend)

I cannot make it work to press the power button or close the lid to suspend.

The workaround (or not at all) is just using the following command in the terminal:

~~~bash
systemctl suspend
~~~
