https://askubuntu.com/questions/60161/change-the-default-downloads-directory
#linux #ubuntu #nautilus #software

---
Nautilus-the-file-browser is smart enough to notice that you're renaming a "special" folder ("Downloads" in your case) and adjust its settings to use the new name.

`$HOME/.config/user-dirs.dirs`



The settings are stored in the file - you can either edit this or just do some trickery with renaming your current Downloads2 back to Downloads via Nautilus.

Then you can move the contents from there to a separate partition and then mounting that partition as $HOME/Downloads.

See this question for more details.

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```