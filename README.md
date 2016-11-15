# Dorian 3.14
Dorian is a full-featured deep dark theme for GTK+ 3.14 by [killhellokitty](http://killhellokitty.deviantart.com/).

[![Dorian screenshot](https://github.com/dllud/Dorian-3.14/raw/master/screenshots/dorian-screenshot-small.png)](https://github.com/dllud/Dorian-3.14/raw/master/screenshots/dorian-screenshot.png)

It is my theme of choice for distros with GTK+ 3.14 up to 3.18 (e.g. Debian jessie, Ubuntu 15.10 and 16.04). Subsequent themes by killhellokitty such as [Dorian Flat 3.16](http://killhellokitty.deviantart.com/art/Dorian-Flat-3-16-revision-5-537693271) and [DeLorean Dark 3.18](http://killhellokitty.deviantart.com/art/DeLorean-Dark-3-18-15-01242015-569072551) are a bit more light coloured, which makes them less suitable for long hours at the screen. However, if you already run GTK+ 3.20, you should ditch Dorian and use the Darkest variant of [Candra-Themes-3.20](https://github.com/dllud/Candra-Themes-3.20) or [Cloak-3.20-dark-blue](https://github.com/dllud/Cloak-3.20-dark-blue).

On this repo I publish some small tweaks I made to Dorian. You can check the modifications list (changelog) by looking at [Git commits](https://github.com/dllud/Dorian-3.14/commits/master).

If you use Dorian or some other dark theme, you might want to take a look at my [Tips for an all dark desktop interface](https://gist.github.com/dllud/e2751ab00ce0e40cc4997b89008fc08a).

## Included themes
- Gtk3 & Gtk2
- Metacity
- Gnome-Shell
- Cinnamon Shell with Nemo
- Xfwm4
- Xfce-Notify
- Openbox-3
- Google Chrome / Chromium
- Firefox
- Thunderbird
- Unity
- Ubuntu Software-Center
- MATE

## Requirements
- GTK+ 3 >= 3.14
- GTK+ 2 >= 2.24
- gnome-themes-standard >= 3.14
- pixbuf-engine or the gtk(2)-engines package gtk-engine-murrine

		sudo apt install gnome-themes-standard gtk2-engines-pixbuf gtk2-engines-murrine

## Installation
Download the zip package for this repo. Unzip the archive, and copy the Dorian folder to `/usr/share/themes/` for system-wide installation, or to `~/.themes/` for individual user installation.

### Firefox and Thunderbird
This theme contains a set of patches to make Mozilla Firefox and Mozilla Thunderbird work better with dark themes. You can install them through a symlink on your profile folders.

	cd ~/.mozilla/firefox/<your profile>
	rm -r chrome ; ln -s /usr/share/themes/Dorian-3.14/firefox/chrome
	
	cd .thunderbird/<your profile>
	rm -r chrome ; ln -s /usr/share/themes/Dorian-3.14/thunderbird/chrome
	
### Chromium
Drag and drop `dorian-chromium.crx` onto Chromium browser and choose to apply theme.

### Ubuntu
1. Open `Dorian-3.14/gtk3.0/gtk-contained.css`
2. Scroll down to the bottom of the document and check that `unity.css` and `ubuntu_styles.css` are uncommented.
3. Use Unity Tweak Tool to choose Dorian theme.

### Ubuntu Software Center
1. **Backup** the original folder and name it `software-center.backup`.

		sudo cp -a /usr/share/software-center /usr/share/software-center.backup

2. **Install**. This assumes the Dorian-3.14 theme is installed to `/usr/share/themes`.

		sudo cp /usr/share/themes/Dorian-3.14/ubuntu-software-center/softwarecenter.css /usr/share/software-center/ui/gtk3/css/softwarecenter.css && sudo cp /usr/share/themes/Dorian-3.14/ubuntu-software-center/stipple.png /usr/share/software-center/ui/gtk3/art/stipple.png

3. **Start/Restart** software-center.
4. To revert changes.

		sudo rm -r /usr/share/software-center && sudo mv /usr/share/software-center.backup /usr/share/software-center
	
### Qt 5 integration
If you run Qt 5 software you can make it use Dorian theme.

1. Install [qt5ct](https://sourceforge.net/projects/qt5ct/)

	1.1 On Ubuntu you can use [hda-me PPA](https://launchpad.net/~hda-me/+archive/ubuntu/qt5ct).
	
		sudo add-apt-repository ppa:hda-me/qt5ct
		sudo apt update && sudo apt install qt5ct
	
	1.2 On Debian you can compile it from [mati75/qt5ct repo](https://github.com/mati75/qt5ct/releases).

2. Add `export QT_QPA_PLATFORMTHEME=qt5ct` as a new line into `~/.profile`.\*

3. Symlink qt5ct configuration:

		cd ~/.config
		ln -s /usr/share/themes/Dorian-3.14/qt5ct
		
4. Restart X server. For instance, logout and login.

\* In LXDE there is a [hardcoded assignment in lxsession](https://sourceforge.net/p/lxde/bugs/824/) that prevents you from setting `QT_QPA_PLATFORMTHEME`. The only workaround for now is to delete the assignment in lxsession code and recompile it. On Debian and derivatives (e.g. Ubuntu) you can do the following:

	sudo apt install build-essential fakeroot devscripts equivs lintian
	apt-get source lxsession
	sudo mk-build-deps -i -r lxsession
	cd lxsession-0.5.2
Edit `lxsession/environement.vala`. Go to the end of the file and delete the line `Environment.set_variable("QT_QPA_PLATFORMTHEME", "lxqt", true);`

	fakeroot debian/rules binary
	sudo dpkg -i ../lxsession_0.5.2-0ubuntu3_<your arch>.deb

## License and authorship
Dorian 3.14 theme licensed under [GNU GPL v3](/LICENSE) by [killhellokitty](http://killhellokitty.deviantart.com/). Some tweaks by [dllud](https://github.com/dllud).

## Donations
Please buy killhellokitty a beer. He accepts [donations through PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=VQBDVXRFDHPPS&lc=US&item_name=killhellokitty&item_number=SiouXsie&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donate_LG%2egif%3aNonHosted).
