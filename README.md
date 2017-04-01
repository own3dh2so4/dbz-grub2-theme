# Dragon Ball Grub Theme
My own dragon ball grub2 theme

## Installation

First clone the git repository, then copy the folder dbz-grub into /boot/grub/themes folder

```
# git clone https://github.com/own3dh2so4/dbz-grub2-theme.git
# cp -r dbz-grub2-theme/dbz-grub /boot/grub/themes/
```

Active the theme and swap the resolution, I choose use vi, but you can use other text editor

```
# vi /etc/default/grub
```
Search the following line: GRUB_THEME
```
#GRUB_THEME="/path/to/gfxtheme"
```
and change for this:
```
GRUB_THEME="/boot/grub/themes/dbz-grub/theme.txt"
```
Now change the resolution, searching this "variable" in the same file
```
GRUB_GFXMODE=auto
```
Edit the value to
```
GRUB_GFXMODE=1024x768
```

Finally you only need update grub configuration
```
# grub-mkconfig -o /boot/grub/grub.cfg
```

<a href="https://github.com/own3dh2so4/dbz-grub2-theme/blob/master/images/dbz-grub.jpg"><img height=300 src="https://github.com/own3dh2so4/dbz-grub2-theme/blob/master/images/dbz-grub.jpg?raw=true"></a>

## F.A.Q.

### Distribution icon
Find your distribution/OS class
```
# grep 'menuentry' '--class' /boot/grub/grub.cfg
```

E.g.: The class for ArchLinux is arch
```
menuentry 'Arch Linux' --class arch --class gnu-linux --class gnu --class os
```
Rename the image to the class name (arch.png)
Resize the image to 32x32, and copy it to /boot/grub/themes/THEME/icons/
(Images must be in PNG)

### Distribution name
Find your distribution/OS class
```
# grep 'menuentry' /boot/grub/grub.cfg
```

E.g:
```
menuentry 'Windows Boot Manager (en /dev/sdaX)' --class windows --class os $menuentry_id_option 'osprober-efi-046F-A13A' {
	...
}
```
In my case I prefer the name "Windows 10", then:
```
menuentry 'Windows 10' --class windows --class os $menuentry_id_option 'osprober-efi-046F-A13A' {
	...
}
```

### Remove distributions entries:
Find your distribution/OS class
```
# grep 'menuentry' /boot/grub/grub.cfg
```
E.g:
```
menuentry 'Arch (en /dev/sdbX)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-6b9b2672-7807-44fd-83d6-3234df201002' {
	...
}
submenu 'Opciones avanzadas para Arch (en /dev/sdbX)' $menuentry_id_option 'osprober-gnulinux-advanced-6b9b2672-7807-44fd-83d6-3234df201002' {
	...
}
```

Just remove it
```
menuentry 'Arch' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-6b9b2672-7807-44fd-83d6-3234df201002' {
	...
}
```

### References
[GNU GRUB Manual 1.99](http://www.gnu.org/software/grub/manual/grub.html#Theme-file-format)  
[GRUB Graphical Menus Project](http://grub.gibibit.com/Theme_format)  
[The Definitive Guide To Theming GRUB 2 v1.99](https://docs.google.com/open?id=0B82343FTJphIbElHUGVac1hBZnc) 