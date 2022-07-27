[[rangerman]]
#ranger #filemanager #software #linux #commandline
---

# Config
rc.conf
commands.py (plugins)

/home/philipp/pCloudDrive/3_Resources/dotfiles/ranger

# Drang and drop 
https://github.com/ranger/ranger/wiki/Drag-and-Drop

```
git clone https://github.com/mwh/dragon
cd dragon 
make install 
```

If GTK is not installed: 
`sudo apt-get install libgtk-3-dev`

rc.conf
`map <C-d> shell dragon -a -x %p --and-exit`

rifle.conf
`has dragon, X, flag f = dragon -a -x "$@"`

If not done create rifle conf 
`ranger --copy-config=rifle`

