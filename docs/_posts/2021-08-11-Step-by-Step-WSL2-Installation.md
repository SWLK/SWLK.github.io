---
layout: post
title: Installing WSL2 on my Windows 10 laptop
---
Since I wanted to use Jekyll for my github.io pages, and I wanted to be able to write and test my webpages on my Windows machine, I checked out the WSL manual installation steps.

Below are the steps I took to install Windows Subsystem for Linux.

Open powershell as administrator and run:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

which provides the following output:

```powershell
Deployment Image Servicing and Management tool
Version: 10.0.19041.844

Image Version: 10.0.19042.1110

Enabling feature(s)
[==========================100.0%==========================]
The operation completed successfully.
```

I then checked my windows version to check my build version.

```powershell
winver
```

After confirming my Windows 10 version could run the programs needed, I enabled Virtual Machine Platform:

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

which gave the following output:

```powershell
Deployment Image Servicing and Management tool
Version: 10.0.19041.844

Image Version: 10.0.19042.1110

Enabling feature(s)
[==========================100.0%==========================]
The operation completed successfully.
```

I then checked my system type with:

```powershell
systeminfo | find "System Type"
```

Next step requires the download of the Linux kernel update package that could be found on `https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi`. This requires a restart to complete the previous steps and to run the installation.

After the restart and the installation, I had to set `WSL 2` as my default version.

```powershell
wsl --set-default-version 2
```

Then proceed to Microsoft store to choose a Linux Distribution to install.

Done!
