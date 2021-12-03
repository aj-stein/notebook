# Notes for Development on NIST Workstations

## Windows

### Windows Subsystem for Linux

#### DNS Resolution Problems

On a brand new WSL2 Ubuntu-20.04 install, I was unable to even `apt-get update` without this. With current WSL2 installations, there is a problem with the automatic generation of the DNS configuration in `/etc/resolv.conf` and how that is or is not managed by `/etc/wsl.conf`. Below is the current fix that worked for me.

```sh
sudo rm /etc/resolv.conf
sudo bash -c 'echo "nameserver 1.1.1.1" > /etc/resolv.conf'
sudo bash -c 'echo "[network]" > /etc/wsl.conf'
sudo bash -c 'echo "generateResolvConf = false" >> /etc/wsl.conf'
sudo chattr +i /etc/resolv.conf
```

Source: [GitHub issue microsoft/WSL#5420](https://github.com/microsoft/WSL/issues/5420#issuecomment-646479747)

#### Copy-Pasting to Clipboard

To copy-paste back and forth from the Windows command prompt, Powershell, and WSL back and forth:

```sh
# From WSL terminal to Windows clipboard (the `.exe` is important):
echo "aaa"|clip.exe

# From WSL terminal to Windows clipboard with non-ASCII i18n data:
# NOTE: In Windows, this is almost always UTF-16LE, not UTF-8
echo 'αβψδεφγ' | iconv -f utf-8 -t utf-16le | clip.exe

# from Windows Powershell and clipboard to WSL terminal.
powershell.exe -command "Get-Clipboard"
```

Source: [StackOverflow](https://stackoverflow.com/a/43408226)

#### Mapping Caps Lock key to Ctrl

How often am I going to need all caps anyway?

```sh
$hexified = "00,00,00,00,00,00,00,00,02,00,00,00,1d,00,3a,00,00,00,00,00".Split(',') | % { "0x$_"};

$kbLayout = 'HKLM:\System\CurrentControlSet\Control\Keyboard Layout';

New-ItemProperty -Path $kbLayout -Name "Scancode Map" -PropertyType Binary -Value ([byte[]]$hexified);
```

Source: [StackOverflow](https://superuser.com/a/997448)