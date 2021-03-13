# Personal Windows Setup
I developed a habit of reinstalling windows every 3-6 months or so. It seems like that's the only way of keeping my systems stable without crashing and annoyances....

## User File Configuration Locations
* Windows Terminal (terminal) `C:\Users\user\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState`
* Windows System for Linux (wsl2) `%APPDATA%\.wslconfig`
  * [Move Your Linux Disk Image](https://www.sitepoint.com/wsl2/#moveyourlinuxdiskimage:~:text=Move%20Your%20Linux%20Disk%20Image)
* Vistual Studio Code (vscode) `%APPDATA%\Code\User\settings.json`
* Git (gitconfig) `%APPDATA%\.gitconfig`

Edge `C:\Users\user\AppData\Local\Microsoft\Edge\User Data`
Chrome `C:\Users\user\AppData\Local\Google\Chrome\User Data`

## Windows Location Reference
* [Recognized Environment Variables](https://docs.microsoft.com/en-us/windows/deployment/usmt/usmt-recognized-environment-variables)
* [%UserProfile%](https://docs.microsoft.com/en-us/windows/deployment/usmt/usmt-recognized-environment-variables#bkmk-2:~:text=Same%20as%20CSIDL_PROFILE.)
* [Windows Icon Locations](https://www.digitalcitizen.life/where-find-most-windows-10s-native-icons/)
* startup items `shell:startup`

## Windows Login Settings
* Autologin to user after startup
  * `start netplwiz`
  * [How to Turn On or Off Require Sign-in on Wakeup in Windows 10](https://www.majorgeeks.com/content/page/how_to_turn_on_or_off_require_sign_in_on_wakeup_in_windows_10.html#:~:text=1%3A%20Sign%2Din%20Options&text=Click%20Start%20%3E%20Settings%20%3E%20Accounts%20%3E,box%20and%20change%20to%20Never.)
* admin_uac_password.reg
