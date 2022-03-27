# How to change forgotten user password on Linux Machine

### (Use it for Education Purpose Only, and I will not be responsible for your illegal activities!)

If you happen to forget your Linux distro password, and you tried multiple times to access your machine, but you were unable to access it. Then there is a way to recover your username password on your Linux machine. We will try to get into the root shell during boot time in recovery mode and override the old password with a new one on root access.


#####  STEPS:

1. Start or restart the computer and press ```ESC``` or ```F2```depending on your machine to get to the grub shell menu
2. Once you are on the grub menu. Click on ```Advanced Ubuntu Settings``` in the menu.
3. In the Advanced Settings Menu, you will see a lot of options. Click on ```recovery mode``` option
4. Again, click on the one that says ```Root shell access```
5. Find a list of usernames you want to change the password by typing ```ls /home```
6. To change password type ```passwd usernameXXX```
7. Once it says password changed successfully, then ```reboot``` to restart the machine.
8. Now you can access usernameXXX with the new password you changed.


