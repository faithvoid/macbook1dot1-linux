# macbook1dot1-linux
Guide and files to help install modern Xubuntu on a Macbook1,1 (CoreDuo). Not finished yet.

## Installation:
- Download Xubuntu 18.04.5-desktop-i386.iso
- Download EFI.zip
- Using a partition manager of your choice, create a 256MB FAT32 partition on your USB and copy the contents of "EFI.zip" to the root of that partition.
- Copy the Xubuntu ISO to the secondary partition of your via USB using dd or a similar utility
- Use either "Try Xubuntu" or "Install Xubuntu" and proceed as normal. If using encryption, you may get a "EFI partition doesn't exist" error, but this doesn't seem to affect anything, as my Macbook boots directly into Xubuntu just fine.
- Once installed, run "sudo apt update && sudo apt upgrade", followed by "sudo apt update && sudo apt dist-upgrade"
- Reboot, and you should be all set, with an up-to-date

## Post-Install Tweaks:
- TBA

## Theming to look more like macOS
- Copy the contents of "Catalina.zip" to the root of your home folder
- Once copied, go into "Appearance" and set your appearance to Catalina or Catalina Dark, and your icons to OS Catalina or OS Catalina Night
- Install and run "Plank" as your default dock bar to replicate the macOS style dock, and once in Plank, alt+click the bar, select Preferences, and select the "Catalina Night" theme.
