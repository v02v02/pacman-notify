# pacman-notify
**Gives notifications to the user about the update status of Arch Linux's package manager Pacman via the use of Dunst.**
![image](https://github.com/user-attachments/assets/54e80229-faa8-4982-8a53-9d04cf621222)
## Intended Usage
This script is targeted to users who don't use a display manager and only use a tty to login and start the X display server via the startx command. Before you run the script, you must manually go in and edit certain variables in the script to get icons and sounds to render with the notifications for the time being (see Todo section). The lines of script that need to be edited are appended with the comment _"#Change this line to have this variable contain your desired path."_. You will also need to remove the safeguard one liner that exits the script before anything is executed after you given the proper values to the path variables (see below). 
![image](https://github.com/user-attachments/assets/c1f105aa-fcab-4017-a711-1470e78d56af)
## Todo
- **Find a way to get Pulseaudio's `paplay` to work as root instead of using the currently used Alsa `aplay`.**

When paplay is ran as root, it will give the following error that a simple `sudo -u $NON_ROOT_USER paplay` will not remediate.
```
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
```

- **Create some sort of optional wizard to automate the setup of some prerequisites for this script.**

This wizard would create default values for the aforementioned path variables that you must maually configure, along with commands that create a directory tree that hold the actual sounds and icons for the notifications. Some default icons and sounds would also be provided and get automatically linked to the script. I would also like the wizard to download dependencies that the script needs to function.

- **Get script to work well with display managers and test out other Arch Linux environments.**

There is a section of script that waits until the X server starts to execute the notifications. However, I would assume that wouldn't work with display servers that already start up the X server before you are offically in your DE/WM. Since this script is intented to work with a crontab @reboot, the first notification would execute before the user could login. I'm intending to also test out this script in other desktop environments to check for functionality. For reference, all the testing for this script as been done in DWM with no display manager.
