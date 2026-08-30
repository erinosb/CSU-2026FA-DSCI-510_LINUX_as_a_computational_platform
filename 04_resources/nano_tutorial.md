# Nano: command line text editor

<p align="center">
<img width="410" alt="nano screen shot" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/nano_screen_shot.png">
</p>

Here are some facts about the command line text editor [nano](https://www.nano-editor.org/) 

- A lightweight text editor for Linux and Mac OS X
- Based on Pico (University of Washington)
- GNU General Public License
- Popular with System Administrators
- Not a Word Processor

### Do I have nano?

See if it's installed: 

```
$ which nano

/usr/bin/nano
```

Or just try to run it:

```
$ nano
```

If it's there, you will see your screen change to the editor, otherwise, you will see

```
-bash: nano: command not found
```

### Introduction to the interface

If you just type `nano` and hit return, you open the interface.

```
$ nano
```

<p align="center">
<img width="410" alt="nano interface x key" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/nano_interface_x_key.png">
</p>

### Saving

#### To quit without saving 

If you have unsaved changes (it says `Modified` in the upper right), and you pressed the CONTROL key and `x` (yes, lowercase) at the same time, you will see:

<p align="center">
<img width="410" alt="nano interface ctrl x" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/nano_interface_ctrl_x.png">
</p>

Type `N` or `n` and nano will quit without saving. You will be returned to the prompt.

Alternatively, pressing **CONTROL** and `c` at the same time will **cancel your exit**, allowing you to keep editing.

If you do wish to save, read on.

#### To save and quit

As above, if you have unsaved changed, and you pressed the CONTROL key and `x` at the same time, AND you typed `Y` or `y` to save changes, you will be prompted for the filename to save.

<p align="center">
<img width="410" alt="nano save buffer crop" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/nano_save_buffer_crop.png">
</p>

If this is a new file, the prompt is blank. Type here to name the new file. Press ENTER to save and quit.

If you are editing a preexisting file, its name will appear here. If you wish to save as a different filename, change the text here. Otherwise, just hit ENTER to keep the name and save and quit.

<p align="center">
<img width="410" alt="nano save quit preexisting crop" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/nano_save_quit_preexisting_crop.png">
</p>

After hitting ENTER you will return to the prompt.

```
$
```

Back to [Making and Removing](../Modules/Week2/2-1_Making_and_Removing.md)
