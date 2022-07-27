https://medium.com/smartmechatronics/embedded-linux-boot-time-reduction-eda5f5b4c014

![[Pasted image 20220412093814.png]]

# Strategie 
## User-space of the device 
- In modern embedded Linux systems **SystemD** is used as first process afterthe kernel. 
	- Starts system applications and services in a common, default order

### Optimizations
- Reordering of application's startup  
	- Starting applications in an eralier boot-target
	- SystemD need all deps needed for that app 
- Starting GUI-Applications before Init-Application

## Kernel
- Responsible for setting up the interfaces, laoding drivers and passing control to the init process 

### Optimizations
- Removing not needed periphery
- Moving the loading of later needed kernel modules to application space 
- Removing not needed kernel-modules 
- Removing console output 

- Get boot.log
 - Optain graphical representations of boot.log

## Bootloader
- Das U-Boot (common for embedded systems)

### Optimizations
- Removing bootdelay (U-Boot has a default of 2 sec)
- Creating custom startscript 
	- Start script tests which hardware is available, wheter it can load kernel and device tree from it and uses the first workign one 
	- But I think we now which hardware we use and can remove unused drivers (network, usb)
- Removing not needed functions and hardware support 
- Reducing size of kernel and device tree

- Reducing kernel size (complex)


# Thesis 
- Analyse verschiedener Boot time reduction techniques in Embedded-Linux

# Fragen 
- Um welche embedded systems handelt es sich? 
	- Gibt es auch welche mit GUI?
- Wurde beres an der boot-time reduction gearbeitet? 
- Ist das Ziel die guideline oder gibt es auch ein Reduktionszeil in sek?


- Wie sieht ein typischer Arbeitstag aus 
- Welcher standort 
- 