# wiscochuwi
chuwi lark box running windows 10

## ssh server

install using built-in `Add Features` and select `OpenSSH Server`

after install is completed, you need to configure the service to `Automatic`

### default shell

create a string entry named `DefaultShell` at `HKLM\SOFTWARE\OpenSSH` with a value of `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

```pwsh
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```

<https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_server_configuration>

## powershell

### windows update

install necessary modules:

```pwsh
Install-Module PSWindowsUpdate
```

>it may prompt you to install additional modules, allow it

to perform a windows update it's a two-step process:

```pwsh
Get-WindowsUpdate
Install-WindowsUpdate
```

you can also use this to download, install and reboot in one command:

```pwsh
Get-WindowsUpdate -AcceptAll -Install -AutoReboot
```
