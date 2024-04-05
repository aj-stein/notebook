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

#### SSH Agent Socket Forwarding from WSL to Windows with Keeagent

Install `npiperelay.exe` and `wsl-ssh-agent-gui.exe` per [this forked guide](https://gist.github.com/aj-stein-nist/9218062c0a1a2b717a8800f92a8de245).

Source: [Original guide from strasis](https://gist.github.com/strarsis/e533f4bca5ae158481bbe53185848d49#file-howto-md)

## Linux/Unix

### Miscellania for All Distros

#### Language Runtime and Package Management

I recommend using [`asdf`](https://asdf-vm.com/guide/getting-started.html#_3-install-asdf) and the following plugins for language runtime management. I do this instead of installing one unique tool per runtime (`nvm` for `node`, `rvm` for `ruby`, et cetera).

- [asdf-golang](https://github.com/kennyp/asdf-golang)
- [asdf-nodejs](https://github.com/asdf-vm/asdf-nodejs)
- [asdf-hashicorp](https://github.com/Banno/asdf-hashicorp.git) for `terraform`

You can vet and install the right plugin, but then follow the same workflow across tools.

```sh
source $HOME/.asdf/asdf.sh
asdf plugin-add langname https://github.com/org/asdf-langname.git
asdf install langname latest
asdf global langname latest
```

#### OpenSSL Decode Certificate

```
openssl x509 -noout -text -in /home/ec2-user/cert.pem
```

#### OpenSSL Decode Certificate Signing Request (CSR)

```
openssl req -noout -text -in /tmp/test.csr
```

### Debian/Ubuntu

#### Listing Files in .deb packages

```
dpkg --contents /var/cache/apt/archives/package_name1.2.3-maintainer_sysarch.deb
```

# Cloud Developer (AWS, Azure, GCP)

## AWS

### Managed Blockchain

#### Deleting Networks

You do not delete a network, you delete all the member nodes, and then the network
comprised by these nodes will delete itself.

## Azure

## GCP
