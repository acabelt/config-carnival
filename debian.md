clear
sudo apt update && sudo apt upgrade -y


# xbacklight
# not working
# bindsym XF86MonBrightnessUp exec xbacklight -inc 10  # increase screen brightness
# bindsym XF86MonBrightnessDown exec xbacklight -dec 10  # decrease screen brightness

Check your /sys/class/backlight folder. If you can see an intel_backlight folder there and still you are getting the above error then creating a /etc/X11/xorg.conf file with the below configuration should work for you. It worked for me.

Section "Device"
    Identifier  "Intel Graphics" 
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"
EndSection

Also, remember to logout and login again for the changes to take effect.

echo "### CLEAN UP"
sudo apt remove gnome-games evolution libreoffice*
sudo apt autoremove -y

echo "### INSTALL BASE DEBIAN"
sudo apt install aptitude arandr bash-completion build-essential ca-certificates curl dmenu dunst filezilla flameshot flatpak gnome-shell-extension-manager gnome-tweaks gnome-software-plugin-flatpak ksnip gdu git gnupg imwheel kbdd kitty libfuse2 mpv nitrogen pcmanfm pipx ripgrep rofi stow sxhkd i3 i3blocks i3status thunderbird wget xdotool xorg -y

echo "### INSTALL FLATPAK"
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

echo "### INSTALL PIPX"

pipx install gnome-extensions-cli --system-site-packages

gext install tilingshell@ferrarodomenico.com
gext install dash-to-dock@micxgx.gmail.com
gext install caffeine@patapon.info
gext install space-bar@luchrioh
gext install AlphabeticalAppGrid@stuarthayhurst

echo "## FLATPAK"

flatpak install flathub it.mijorus.gearlever org.nickvision.tubeconverter flathub fr.romainvigier.MetadataCleaner -y