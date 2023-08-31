  # Animated Boot Screen Shell Script

This is a template built off of Eonix's animated cat plymouth theme. I modified some of jcklpe's scripts and added a new Plymouth theme for my laptop.  

![Linux-Laptop-Bootscreen](/images-for-repo/animated-laptop-bootloader.gif)


## Instructions 

1. Install Plymouth themes:

`sudo apt install plymouth-themes`

2. Go to the plymouth themes folder

`
cd /usr/share/plymouth/themes
`

3. Create new theme folder

`
sudo mkdir ./{{ThemeNameHere}}
`

4. Move into your new theme folder.

`
cd {{ThemeNameHere}}
`

5. Clone this repo contents into the folder.

`
sudo git clone https://github.com/MarcusHoltz/Animated-Boot-Screen-Creator-for-Linux.git .
`
The dot at the end will clone the contents of the template folder into your new theme folder. 

### Installation
1. Install the theme by creating a symbolic linking from your new theme to the default.python file, be sure to replace the template variables used:

```
 sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/{{ThemeName}}/{{ThemeName}}.plymouth 100
```
In my case it looks like this:
```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/laptop/laptop.plymouth 100
```

2. Select the default theme.
`sudo update-alternatives --config default.plymouth`
If nothing appears, you're done. 

But if you see a list of themes, select the number for your theme. 
Be sure to adjust the priority in the command above (100) to something larger than the other themes so auto can take over. Or not, whatever. 


2.5 Double check that theme install.

If you need to search the list of themes, just to be sure, before you commit... use:
`
plymouth-set-default-theme -l
`

To set the actual theme and automagically re-create the initramfs:
`
plymouth-set-default-theme laptop -R
`

