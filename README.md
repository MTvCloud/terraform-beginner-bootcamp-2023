# Terraform Beginner Bootcamp 2023

## Semantic versioning :mage: _ :mage:

This project is going to utilize Semantic Versioning for its tagging.
[semver.org](https://semver.org/)
Given a version number **MAJOR.MINOR.PATCH**, increment the:

The general format:

**MAJOR.MINOR.PATCH**, e.g `1.0.1`

-.**MAJOR** version when you make incompatible API changes
- **MINOR** version when you add functionality in a backward compatible manner
PATCH version when you make backward compatible bug fixes

https://www.gitpod.io/docs/ides-and-editors/vscode#connecting-to-vs-code-desktop-ssh

## install terraform cli.

### Considerations with terraform CLI changes 
The terraform CLI installation instruction have changed due to gpd 
keyring changes. So we needed to refer to the latest insall cli
instructions via terraform Documentation and changes the scripting
for install.

[Install Terraform Cli](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

### Consideration for Linux Distribution

This project is built aginst Ubuntu.
Please consider checking your Linux Distribution and change according
to distribution needs.

[How to check Linux version in Linux](
https://www.cyberciti.biz/faq/
https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/)

Example of checking os version
```
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```
### Refactoring into Bash Scripts

while fixing the terraform CLI gpg deprecation issue, we notice that bash 
scripts steps were a considerable amount more code.so we decided to create 
a bash script to install the terraform CLI.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli.sh)

- This will keep the Gitpod Task File ([gitpod.yml]().gitpod.yml))tidy.
- This allows us an easier to debug and excute manually terraform CLI install.
- This will allow better portablity for other projects that need to install Terraform CLI.

#### Shebang Considerations

A shebang (pronunce sha-bang) tells the bash script what program that will interpret the script.

https://en.wikipedia.org/wiki/Shebang_(Unix) eg. `#!/bin/bash`

ChatGPT recommended this format for bash: `#!/usr/bin/env bash`

- for porability for differnt OS distribution
- Will serach the user's PATH for the bash executable

https://en.wikipedia.org/wiki/Shebang_(Unix)

## Execuation Considerations
When executing the bash scripts we can use the `./` shorthand notation to execute the bash script.

eg. `./bin/install_terraform_cli`

Id we are using a script in gitpod.yml, we need to point the script to a program to interpret it.

eg. ` source ./bin/install_terraform_cli`



#### Linux Permission Consideration

we need to make our bash scripts executable we need to change linux permission for fix to be executable at the user mode

```sh
chmod u+x ./bin/install_terrafom_cli
```
alternatively:

```sh
chmod 744 ./bin/install_terrafom_cli


### Github Lifecycle (before, Init, Command)

we need to be careful when using the Init becuase it will not return if we restart an existing workspace.

https://www.gitpod.io/docs/configure/workspaces/tasks
