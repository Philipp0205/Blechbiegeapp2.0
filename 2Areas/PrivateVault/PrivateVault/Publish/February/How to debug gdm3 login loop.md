
# How to debug gdm3 login loop (Ubuntu)
#ubuntu #linux #guide

From time to time I find myself in a login loop when I start my PC. 
That mean the login screen of Ubuntu (managed by gdm3) will accept my password but instead of continuing to the desktop present me an empty login screen again.

There are multiple possible reasons for that behavior. Here are the the reasons and fixes I already ran into.

# Nvidia drivers 
- Wrong Nivida drivers installed 
- Nvidia drivers broke for some reason (for example plugin in an extern egpu or similar) 

## The Fix: 
Delete the drivers and install them again. 
```bash
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current
```

# Xorg config
- I tinkered around in the xorg config and something broke
- This basically can be anything so we need a way to debug the problem 

## The Fix: 
1. Press Ctrl+F2 from the login screen to launch a terminal (tty2) 
2. Login with username, password
3. Run `startx`
4. Now Xorg should log what the problem is. 

## More debug options with grub
Should the logs from startx not be enough another source of error might be the grub bootloader. 
To get more information on that:

1. Edit the the grub config 

```bash
sudo vim /etc/default/grub
```

2. Edit the value of "GRUB_CMDLINE_LINUX_DEFAULT"
The default value should be `quiet splash` . 

> The option quiet prevents Linux from giving shell output of your boot process, and the splash option show the boot screen. If you remove both you will get an output. 

[Source](https://askubuntu.com/questions/1039707/what-is-quiet-splash-in-the-grub-file-for)

3. `sudo update-grub`




