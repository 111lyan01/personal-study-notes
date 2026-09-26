# Personal Study Notes
My personal study notes for everything I'm learning from 10th grade and beyond.
>[!WARNING]
> Notes are constantly updating! I'm not sure whether to set releases so just about every day new content is being added!

## To View As Intended
### Download ZIP
1. Press the `<> Code ▾` button and download ZIP.
2. Extract the zip file into a folder.
For Git Users:
```bash
git clone https://github.com/111lyan01/personal-study-notes.git
```
### Download Obsidian
#### Windows
Download [Windows executable](https://github.com/obsidianmd/obsidian-releases/releases/download/v1.13.7/Obsidian-1.13.7.exe)
#### MacOS
Download [Apple Disk Image](https://github.com/obsidianmd/obsidian-releases/releases/download/v1.13.7/Obsidian-1.13.7.dmg)
#### Linux
##### Universal Formats
Download [AppImage](https://github.com/obsidianmd/obsidian-releases/releases/download/v1.13.7/Obsidian-1.13.7.AppImage)

Download [AppImage for ARM computers](https://github.com/obsidianmd/obsidian-releases/releases/download/v1.13.7/Obsidian-1.13.7-arm64.AppImage)

Download flatpak:
```bash
flatpak install flathub md.obsidian.Obsidian
```
##### Official Package Distributions
Arch Linux:
```bash
sudo pacman -S obsidian
```
NixOS:
```nix
{
  nixpkgs.config.allowUnfree = true;

  environment.systemPackages = with pkgs; [
    obsidian
  ];
}
```
### In Obsidian
Choose **Open folder as vault** and select the folder to open.