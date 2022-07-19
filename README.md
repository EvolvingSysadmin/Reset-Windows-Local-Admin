# Reset Windows 10 Local Admin Password
This repository has documentation for basic methods of resetting a forgotten local administrative password.

## Windows Method
- Create Bootable Windows 10 Installation Media
- Change BIOS boot order to boot from installation media
- Press `Shift + F10` on the Windows Setup screen to open a command prompt
- Use DISKPART to locate the Windows drive/volume 
- Navigate to the `Windows\System32` directory on the Windows volume
- Replace `sethc.exe` (Sticky Keys executables) with `cmd.exe` (command prompt executable):
  ```
  copy sethc.exe ..
  copy cmd.exe sethc.exe
  ```
- Shutdown PC, remove the Windows 10 Installation Media, then power on PC
- Hold `Shift` and Press Restart on the Windows Login screen to reboot the computer to display Safe Mode options
- Go to Troubleshoot -> Advanced Options -> Startup Settings -> Restart on the Safe Mode settings page
- Select 4 to Enable Safe Mode on the startup settings page
- Hit the `Shift` key five times quickly after rebooting into Safe Mode to generate an Administrative Command Prompt
- Change the password using command, replace username and password with the respective administrative username and password (use `net user` to find the administrative account)
  ```
  net user username password
  ``` 
- To add a user to the local Administrators group, if not already an admin, replace username with the username:
  ```
  net localgroup Administrators username /add
  ```
- Reboot the computer, login with the administrative account and change back the shortcut to sethc.exe (Sticky Keys):
  ```
  Robocopy C:\Windows C:\Windows\System32 sethc.exe /B
  ```

## Linux Method
- Use Linux installation media to boot the computer into Linux
- Mount the drive/volume running windows
- Install and use the chntpw utility to change the local password

## Resources
- [https://www.makeuseof.com/tag/3-ways-to-reset-the-forgotten-windows-administrator-password/](https://www.makeuseof.com/tag/3-ways-to-reset-the-forgotten-windows-administrator-password/)