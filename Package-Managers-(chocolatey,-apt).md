## Chocolatey
### [Installation](https://chocolatey.org/install)
`Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`
### Installing packages
chocolatery supports installing packages by name or from a `*.config` file. no clue what the specifications for this file are because the links refering to the specification lead to chocolatey's readme page

## Apt
### searching for packages
no clue how to find highly "ranked" packages.
### Add repositories.
Docker, Google Cloud and more need their repositories added in order to download their software, they're not bundled with ubuntu