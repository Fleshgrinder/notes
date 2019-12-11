# Windows Subsystem for Linux (WSL)

The Windows Subsystem for Linux (WSL 1) allows to use different Linux distros directly from your Windows 10 machine.

## Enable WSL

Run in PowerShell:

```shell
Enable-WindowsOptionalFeature -Online -FeatureName "Microsoft-Windows-Subsystem-Linux"
```

## See your distros and their WSL versions

Run in PowerShell:

```shell
# Windows version < 2004
wsl --list -all
# Windows version >= 2004
wsl --list -v
```

## Manage multiple distributions

Install [LxRunOffline](https://github.com/DDoSolitary/LxRunOffline) with:

```shell
choco install lxrunoffline
```

This allows, among other things, to install, uninstall, move, duplicate a distribution.

Type `lxrunoffline` to see the list of supported actions.


## Windows Subsystem for Linux 2 (WSL 2)

Windows Subsystem for Linux 2 (WSL 2) was announced at the Microsoft Build 2019 conference and is shipped with the Windows 10 Insider Preview Build 18917. WSL 2 architecture is drastically changed and brings increased file system performance and full system call compatibility, uses virtualization technology (based on Hyper-V) and uses a lightweight utility VM on a real Linux kernel.

- [Release blog](https://devblogs.microsoft.com/commandline/wsl-2-is-now-available-in-windows-insiders/)

- [Microsoft WSL 2 Docs](https://docs.microsoft.com/en-us/windows/wsl/wsl2-index)

### Install WSL 2

#### Prerequisites

1. [Telemetry data must be enabled](https://github.com/Disassembler0/Win10-Initial-Setup-Script/blob/317c49038941ccea1c74c6838bc1d383a1078341/Win10.psm1#L59-L79)

1. You must join the [Windows Insider Program](https://insider.windows.com/en-us/) and select the 'Fast' ring

#####  Windows Insider Program troubleshooting

- if you are having an issue with Docker asking for a password, follow [these instructions](https://github.com/docker/for-win/issues/616#issuecomment-528390516) to fix it.

- if your computer get stuck at booting, disable the secure boot in the BIOS

#### Installation Instructions

- [Microsoft Docs / Install WSL 2](https://docs.microsoft.com/en-us/windows/wsl/wsl2-install)

### Switch WSL version

```shell
wsl --set-version <distro> <version>
```

### Known issues

As of build 19037:

- tunneling `127.0.0.1` [works only in the `Windows->WSL` direction](https://devblogs.microsoft.com/commandline/whats-new-for-wsl-in-insiders-preview-build-18945/), but not in the `WSL->Windows` one. Subscribe to [this issue](https://github.com/microsoft/WSL/issues/4619) to know when access to windows services via localhost:port will be implemented in WSL 2.

- **WSL 2 with NTFS is unusably slow**, but with EXT4 is very close to native Linux performance ([source](https://vxlabs.com/2019/12/06/wsl2-io-measurements/))

