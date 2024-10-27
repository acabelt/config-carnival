clear
sudo apt update && sudo apt upgrade -y

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