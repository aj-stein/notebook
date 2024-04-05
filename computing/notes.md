# Notes for Development on NIST Workstations

## Programming Languages and Development Tools

### Golang

#### `go mod`: could not read Username for 'https://github.com'

This was a frustrating one reported by colleages that I had not seen before.

```sh
$ cd $GOPATH
$ go get github.com/examplesite/myprivaterepo
$ git clone https://github.com/examplesite/myrepo
Cloning into '/path/to/gopath/src/github.com/examplesite/mepo'...
fatal: could not read Username for 'https://github.com': terminal prompts disabled
package github.com/examplesite/myprivaterepo: exit status 128
```

Solution is fixing evolving defaults for `git` to prefer `SSH` over HTTPS unless specified.

```sh
git config --global --add url."git@github.com:".insteadOf "https://github.com/"
```

Source: [StackOverflow](https://stackoverflow.com/a/44247040)

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

#### WSL Ubuntu Defaults for `git` and `core.fileMode`

It seems using the Ubuntu 20.04 distro via WSL and with git installed via (`sudo apt install git`) leads to a default configuration with core.fileMode set to `false`. When developing shell scripts where the executable bit needs to be sit, `git status`, `git diff`, and other important commands will ignore file mode changes and make it difficult to detect any change (or lack thereof).

Source: [StackOverflow](https://stackoverflow.com/a/1580644).

#### Firefox and NTLM Passthrough Authentication on Windows

By default, Firefox (as tested on Windows 10) does not allow automatic single sign-on with NTLM and/or Kerberos environments, either via local Active Directory or Azure's ADFS.

To use Single Sign-on with Firefox, you must enable the Windows Sign-on Settings and enable the relevant trusted authentication URIs. You can go to the `about:config` menu to set these manually _or_ you can update the following settings in your Firefox profile `prefs.js` configuration file. This works with Windows 10 and Firefox 95.x releases at the time of this writing.

```js
// If this file was empty before you made these modifications, it must start with a comment.
user_pref("network.http.windows-sso.enabled", true);
user_pref("network.automatic-ntlm-auth.trusted-uris", "auth.nist.gov,sts.nist.gov,sts2.nist.gov");
user_pref("network.negotiate-auth.trusted-uris", "auth.nist.gov,sts.nist.gov,sts2.nist.gov");
```

## Linux/Unix

### Miscellania for All Distros

#### Language Runtime and Package Management

I recommend using [`asdf`](https://asdf-vm.com/guide/getting-started.html#_3-install-asdf) and the following plugins for language runtime management. I do this instead of installing one unique tool per runtime (`nvm` for `node`, `rvm` for `ruby`, et cetera).

- [asdf-cf](https://github.com/mattysweeps/asdf-cf)
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

#### Enforce Connection Timeouts with SSH Clients

If you need to test timeouts, the OpenSSH `ssh` client takes a long time. You can enforce shorter timeouts for testing.

```sh
ssh -vv -o ConnectTimeout=10 -o BatchMode=yes -T git@github.com # Exit with error if not connected in 10 seconds
```

Source: [StackOverflow](https://stackoverflow.com/a/11283798)

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

#### Ubuntu's Default Java JDK/JRE Installation Path and `JAVA_HOME`

Ubuntu installs the `default-jdk` and `default-jre` at the path `/usr/lib/jvm/default-java` and provides a symlink.

```sh
$ ls -l /usr/lib/jvm/default-java
lrwxrwxrwx 1 root root 25 Jul 17  2019 /usr/lib/jvm/default-java -> java-1.11.0-openjdk-amd64
```

Source: [StackOverflow](https://askubuntu.com/a/175547)

# Cloud Developer (AWS, Azure, GCP)

## AWS

### Managed Blockchain

#### Deleting Networks

You do not delete a network, you delete all the member nodes, and then the network
comprised by these nodes will delete itself.

## Azure

## GCP

## Tools

### Ansible

#### Testing on Running Instance

I have trouble with the `-l`/`--limit` argument working, so this is how I do this.

To use with `packer`, I set up the `playbook.yml` file like so. The `packer` provision for `ansible` (local or default remote) will [always run it with a host inventory target of `default` unless you override it](https://github.com/hashicorp/packer-plugin-ansible/blob/6cf787294c5745e87cc57e489c6b472c34871ffd/provisioner/ansible/provisioner.go#L117-L120).

```yaml
---
- hosts: "{{ ansible_limit | default('default') }}"
  gather_facts: true
  become: yes
  roles:
    - {
        role: my-role-name,
        my-role-name-arg1: yes
      }
```

- Set up an `inventory` file in the code (if a `git` repository, add to `.gitignore` and check this works immediately)
- Modify the inventory to look below, adding relevant IP address and service FQDN entries

```ini
[default]
1.2.3.4 1.2.3.5 service.hostname.tld
```

- Run the playbook interactively like so.

```sh
# ec2-user if the target(s) are in AWS, change to remote host user accordingly.
ANSIBLE_ENABLE_TASK_DEBUGGER=True ansible-playbook \
    --extra-vars "ansible_ssh_user=ec2-user" \
    -i inventory playbook.yml
```

#### Encoding JSON for Storage with `aws`, `bash`, and `jq`

The need for this first occurred for me with taking inputs from the `aws` CLI, transforming it with a JMESPath query directly, potentially also transforming it with `jq`, using `jq` to escape all the `"` characters to turn the JSON value into a string form that can be saved in something AWS SSM Parameter store. I prefer note to Base64 encode the data as it is not transparent or easy for developers to spot check.

There are alternative solutions with a variety of tools, but many of them are not ideal.

So, here is an example.

```sh
$ aws ec2 describe-instances \
  --query \
  'Reservations[].Instances[?contains([`ec2-server-name`], Tags[?Key==`Name`].Value[] | [0])][].{ InstanceId: InstanceId PrivateIpAddress: PrivateIpAddress}' \
  | jq -c # make output compact on one line
[{"InstanceId":"i-0123456789012","PrivateIpAddress":"10.1.2.3"}]
```

So what happens when you want to set this result as a variable and more safely pass it, in stringified form, to bind it to a `bash` variable and use in further API queries and responses that require str in some casesings and do so without potential encoding errors from missing escaped control characters? If you have JSON with spaces between keys and values, `{"name":"value"}` will work but `{ "name" : "value" }` will throw errors.

```sh
$ HOST=$(aws ec2 describe-instances \
  --query \
  'Reservations[].Instances[?contains([`ec2-server-name`], Tags[?Key==`Name`].Value[] | [0])][].{ InstanceId: InstanceId PrivateIpAddress: PrivateIpAddress}')
$ echo $HOST
[ { "InstanceId": "i-0123456789012", "PrivateIpAddress": "10.1.2.3" } ]
```
For the sake of argument, let us try to use this data and and bind it to the value of a AWS SSM Parameter. This service in AWS allows the secure and permissioned storage of values, but only offers `String`, `StringList`, and `SecureString` storage. You cannot save JSON directly or other complex objects, you must encode them as a string. To do this safely, you can use `jq`'s [`fromjson` and `tojson` methods](https://stedolan.github.io/jq/manual/#example70) to do this.

The above value will cause an error.

```sh
$ aws ssm put-parameter --name "/path/to/key" --overwrite --value $HOST
Unknown options: "InstanceId":, "i-0123456789012",, "PrivateIpAddress":, "10.1.2.3", }, ], {

$ # What if we don't use the variable and do it inline?

$ aws ssm put-parameter --name "/path/to/key" --overwrite --value $(aws ec2 describe-instances --query 'Reservations[].Instances[?contains([`ec2-server-name`], Tags[?Key==`Name`].Value[] | [0])][].{ InstanceId: InstanceId PrivateIpAddress: PrivateIpAddress}')
Unknown options: "InstanceId":, "i-0123456789012",, "PrivateIpAddress":, "10.1.2.3", }, ], {

$ # Weird still the same odd error, how can this be!?
```

So we need to encode the argument as a string to safely pass and not worrry about quotation marks, control characters, and unforseen spaces in output that will lead to encoding errors.


```sh
$ aws ssm put-parameter --name "/path/to/key" --overwrite --value --overwrite --value $(aws ec2 describe-instances --query 'Reservations[].Instances[?contains([`ec2-server-name`], Tags[?Key==`Name`].Value[] | [0])][].{ InstanceId: InstanceId PrivateIpAddress: PrivateIpAddress}' | jq -c '. | tojson')


$ aws ssm get-parameter --name /path/to/key --with-decryption
{
    "Parameter": {
        "Name": "/path/to/key",
        "Type": "SecureString",
        "Value": "\"[{\\\"InstanceId\\\":\\\"i-0123456789012\\\",\\\"PrivateIpAddress\\\":\\\"10.1.2.3\\\"}]\"",
        "Version": 10,
        "LastModifiedDate": 1641402406.47,
        "ARN": "arn:aws:ssm:us-east-1:0123456789012:parameter/path/to/key",
        "DataType": "text"
    }
}

$ aws ssm get-parameter --name /path/to/key --with-decryption | jq -r '.Parameter?.Value? | fromjson' | jq -r .[].InstanceId?

i-00219c313f1b09394
```


Source: [The GitHub project for `jq`, specifically issue #1918](https://github.com/stedolan/jq/issues/1918#issuecomment-498968907)
#### Cloudwatch Log Analysis with `cw`

The `cw` tool is wonderful for quickly analyzing AWS CloudWatch logs in the console.

```sh
$ export CW_VERSION=v.4.1.1
$ export CW_DL_DIR=/tmp
$ pushd "${CW_DL_DIR}"
$ curl -L -O https://github.com/lucagrulla/cw/releases/download/${CW_VERSION}/cw_amd64.deb
$ apt-cache show "${CW_DL_DIR}/cw_amd64.deb" # Manually review metadata before installation
$ apt install "${CW_DL_DIR}/cw_amd64.deb"
$ $(which cw) --version
4.1.1
$ export AWS_PROFILE=profilename
$ export AWS_DEFAULT_REGION=us-east-1
$ cw tail --follow /aws/path/to/group/stream-name
```

#### Conditional Assignment of Task Attributes with `omit` Doesn't Work

And that's by design, folks! Well, at least it as of `ansible [core 2.12.1]`. There is [an issue that covers this](https://github.com/ansible/ansible/issues/14130), and `ansible` devs make it clear, to paraphrase "the tool works just the way it is intended not how reporters expect." I wasted a day on this, so here you go!

```yaml
- hosts: localhost
  vars:
    role_become: yes
    role_become_user: whomever
    role_delegate_to: localhost
  tasks:
    - name: conditionally run on local workstation with ansible installed or remote target (broken)
      delegate_to: "{{ role_delegate_to if role_delegate_to is defined else omit }}"
      become: "{{ role_become is defined | ternary('yes', 'no') }}"
      become_user: "{{ role_become_user if role_delegate_to is defined else omit }}"
      shell: whoami
```

This code will bomd out with an exception every time and not conditionally remove (`omit`) task parameters (`become`, `become_to`, `delegate`, `environment`, et cetera). So you have the fun of just doubling the code twice with a `when` block, or however many times you need it. Code reuse is not happening with this pattern unfortunately.

```yaml
- hosts: localhost
  vars:
    role_become: yes
    role_become_user: whomever
    role_delegate_to: localhost
  tasks:
    - name: conditionally run on local workstation with ansible installed
      delegate_to: "{{ role_delegate_to }}"
      become: yes
      become_user: "{{ role_become_user }}"
      shell: whoami
      when: role_delegate_to is defined # var is defined above, to default to local exec

    - name: conditionally run on remote target
      become: no
      shell: whoami
      when: role_delegate_to is undefined # when is commented out above, run remote
```

### Packer

#### Error Validating Regions Missing Endpoints Error

If you are using the `amazon-ebs` provider with current versions of `packer` (1.7.8) of this writing, and you have a packer configuration and pass in the AWS region with a parameterized variable like so you will get an error.

```sh
cat << EOF > example.json
{
    "variables": {
        "aws_profile": "",
        "aws_region": "",
        "prefix": "",
        "gold_image_id": "",
        "instance_type": "",
        "kms_key_id": "alias/aws/ebs",
        "ssh_username": "ec2-user",
        "target_vpc_id": "",
        "packer_subnet_id": "",
        "packer_security_group_id": ""
    },
    "builders": [
        {
            "type": "amazon-ebs",
            "profile": "{{user `aws_profile`}}",
            "region": "{{user `aws_region`}}",
            "source_ami": "{{user `gold_image_id`}}",
            "instance_type": "{{user `instance_type`}}",
            "ssh_username": "{{user `ssh_username`}}",
            "ami_name": "{{user `prefix`}}-peer-node-{{timestamp}}",
        }
    ],
    "provisioners": [
        {
            "type": "shell",
            "inline": ["sleep 10"]
        }
    ]
}
EOF
packer build -var 'aws_region="us-east-1"' example.json
```

The error will be similar to below.

> ==> Some builds didn't complete successfully and had errors:
> --> amazon-ebs: error validating regions: MissingEndpoint: 'Endpoint' configuration is required for this service

This is because you specifically quoted the region name `"us-east-1"` and packer interprets that as the name of the region literally.

You will want to ensure it is set as `-var "aws_region=us-east-1"` (observe no quoting after the equal sign) or you will receive this cryptic error.

### Terraform

#### Lockfile Troubleshooting with Failures of Terraform 1.x and `terraform init`

There appears to be some history around plugin resolution in "mirror directories" and cache directories, depending on how you configure your system. See [terraform/#29696](https://github.com/hashicorp/terraform/issues/29696) for current context on the issue.