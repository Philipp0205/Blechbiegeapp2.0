# PaperWM
[[!Linux]] [[terminal]] [[window-manager]]

---
- https://github.com/paperwm/PaperWM/

## Change default windows sizes 
- https://github.com/paperwm/PaperWM/issues/316
- You can change the step widths like this (using screen width ratios):
	- `dconf write /org/gnome/shell/extensions/paperwm/cycle-width-steps "[0.1, 0.3, 0.5]"`
- You can also specify static widths, but the ratios and exacts can't be mixed at the moment:
	- `dconf write /org/gnome/shell/extensions/paperwm/cycle-width-steps "[300, 500, 700]"`
- There's also <Super>+/- which increases/decreases the window width 10% (IIRC). 