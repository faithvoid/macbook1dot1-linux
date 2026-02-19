# macbook1dot1-linux
Guide and files to help install modern Debian (12.13) with XFCE on a Macbook1,1 (CoreDuo), and theme it to look like macOS Catalina, a version of macOS that came out 10 years after the last compatible version of macOS, Snow Leopard. 

Not finished yet. 

Using an SSD and having 3GB of RAM is HIGHLY recommended to make up for the system's CPU/GPU bottlenecks. 

## Why?
These first-generation Macbooks are still usable for certain day-to-day tasks (multimedia playback, word processing, light web browsing, even DJing with Mixxx) and super fun to play around with in 2026, it's just that the information about doing anything modern with them is far and few between compared to their 64-bit cousins that came out the year after.

## Installation:
- **Unlike other Macbooks, you HAVE to use a 32-bit distro here, the entire system (including EFI) is 32-bit. If you have a 64-bit system but a 32-bit EFI, you're using Macbook2,2, which is visually identical but can actually run 64-bit systems with 32-bit bootloader patches!**
- Download debian-12.13.0-i386-netinst.iso. 
- Download EFI.zip
- Using a partition manager of your choice, create a small 10MB FAT32 partition on your USB and copy the contents of "EFI.zip" to the root of that partition. (ie; copy "boot" folder to the root of your new partition)
- Copy the Debian ISO to the secondary partition of your via USB using dd or a similar utility, or copy it to a seperate USB using Etcher or similar utility.
- Use "Graphical Install" and proceed as normal, making sure to select "XFCE" when asked to select a window manager. Note that your mouse may not work during installation and you'll either have to install entirely via keyboard or insert a USB mouse. This will also take forever (took about an hour and a half for me on an SSD), so maybe watch a movie in the background as soon as Debian's graphical installer starts setting up it's new partitions, as that's the longest part.
- Once installed, run "su", then type "nano /etc/sudoers" and under "ROOT = ALL(ALL:ALL)", copy the exact same text but replace "ROOT" in the new copy with your current username.
- Once you've added your user to sudoers, run "sudo apt update && sudo apt upgrade", followed by "sudo apt update && sudo apt dist-upgrade" to completely upgrade your system.
- Reboot, and you should be all set, with an up-to-date installation of Debian 12.13 on a 6.x kernel! (The last version to properly support 32-bit systems).
- (Optional) If you want to use rEFInd to dual-boot, mount your EFI partition (if no EFI folder is found in /boot/efi, run ``` sudo mkdir /mnt/efi ``` then ``` sudo mount /dev/sda1 /mnt/efi ```, then go to /mnt/efi and copy the contents from the "efi" folder on USB stick you made into /mnt/efi!

## Post-Install Tweaks:
- Install "tlp" via "sudo apt install tlp" for better battery life / fan performance.
- Use Chromium or a similar browser instead of Firefox, modern Firefox will hammer the CPU before you've even made it to a website, whereas Chromium is mostly usable on non-video sites.
- Don't expect to watch YouTube in the browser here at any resolution, the CPU will start crying. The best way to watch YouTube videos is to download SMPlayer and yt-dlp, then copy the URL into "File -> URL", which will load the YouTube video in SMPlayer instead, using a lot less system resources. 480p content is ideal here, 720p CAN run via SMPlayer, but will drop frames.
- For iMessage-style support and OS-wide phone integration, consider installing "KDE Connect" on your Macbook and your phone! You can easily share files wirelessly between devices, as well as send/receive SMS messages!
- For iCloud-style storage, look into setting up GVFS mounts with Google Drive or Dropbox! A bit of work, but once it's done, should make cloud storage feel as seamless as iCloud.
- More coming soon!

## Theming to look more like macOS
- Copy the contents of "Catalina.zip" to the root of your home folder
- Once copied, go into "Appearance" and set your appearance to Catalina or Catalina Dark, and your icons to OS Catalina or OS Catalina Night
- Remove "Plank 2" (dock bar) in XFCE panel settings if available, and change the Enter/Leave opacity in the appearance settings of Panel 1 to ~75%.
- Install and run "Plank" as your default dock bar to replicate the macOS style dock, and once in Plank, alt+click the bar, select Preferences, and select the "Catalina Night" theme.
- Install and run "ulauncher" (```sudo add-apt-repository ppa:agornostal/ulauncher -y && sudo apt update && sudo apt install ulauncher```) to replicate Spotlight functionality by pressing ctrl+space.
- Run "Session & Startup" and add "plank" and "ulauncher" as new commands to run on startup!

## (Personal) Best macOS Software Equivalents
- Safari - Chromium
- Mail - Thunderbird
- Facetime - Dino, or a chat client like Zoom / Discord in browser (this will probably be really laggy).
- iMessage - KDE Connect SMS, Signal
- iMovie - Kdenlive (can't imagine why you would put yourself through video editing on this, though)
- Spotlight - uLauncher
- iTunes - Strawberry
- Apple Music - Cider (paid, AM client), Spotube (free, overall music player)
- Quicktime - MPV (SMPlayer if you want a full-featured MPV GUI)
- Photos - digiKam for viewing/editing camera photos, Ristretto for all photos, and Immich for a self-hosted Google Photos style interface.
- Photo Booth - Cheese
- iCloud - GVFS mounts of Google Drive or Dropbox, SMB network shares, or self-hosted software like Immich / Nextcloud. 

## Credits:
- rEFInd team - EFI bootloader
- matomatical - "Grey Apple" rEFInd theme
- b00merang - "macOS Catalina" theme
- zayronxio - "OS Catalina" icons
