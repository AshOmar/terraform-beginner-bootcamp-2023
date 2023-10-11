# Terraform Beginner Bootcamp 2023 - Week0


- [Semantic Versioning](Week0.md#semantic-versioning-mage)
- [Install the Terraform CLI](#install-the-terraform-cli)
  * [Considerations with the Terraform CLI changes](#considerations-with-the-terraform-cli-changes)
  * [Considerations for Linux Distribution](#considerations-for-linux-distribution)
  * [Refactoring into Bash Scripts](#refactoring-into-bash-scripts)
    + [Shebang Considerations](#shebang-considerations)
    + [Execution Considerations](#execution-considerations)
    + [Linux Permissions Considerations](#linux-permissions-considerations)
- [Gitpod Lifecycle](#gitpod-lifecycle)


## Semantic Versioning :mage:

We are going to use semantic versioning for tagging in this project

[Semver.org](https://semver.org/)

The format will be as below:

**MAJOR.MINOR.PATCH** e.g. `1.0.0`

Given a version number **MAJOR.MINOR.PATCH**, increment the:

**MAJOR** version when you make incompatible API changes
**MINOR** version when you add functionality in a backward-compatible manner
**PATCH** version when you make backward-compatible bug fixes
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Install the Terraform CLI

### Considerations with the Terraform CLI changes

The Terraform CLI installation instructions have been changed due to gpg keyring changes. So we need to refer to the latest install CLI instructions via Terraform Documentation below:

[Install Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)


### Considerations for Linux Distribution

We have to check our Linux Distribution to consider this while building our scripts and changes as some considerations may be needed for different distributions.

This project is built against Ubuntu.

[How To Check OS Version in Linux](
https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/)

Example of checking OS Version:

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

We decided to create a bash script to install the Terraform CLI to keep ([.gitpod.yml](.gitpod.yml)) file cleaned and tidy and will be better for portability to have one script to install Terraform CLI.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli)

#### Shebang Considerations

A Shebang (pronounced Sha-bang) tells the bash script what program will interpret the script. eg. `#!/bin/bash`

ChatGPT and below WiKi URL recommend this format for bash and others like python: 

`#!/usr/bin/env bash`
`#!/usr/bin/env python3`

- for portability for different OS distributions. 
-  will search the user's PATH for the executable like bash/python3 mentioned in the previous example.

[Shebang WiKi](https://en.wikipedia.org/wiki/Shebang_(Unix))

#### Execution Considerations

When executing the bash script we can use the `./` shorthand notation to execute the bash script.

eg. `./bin/install_terraform_cli`

If we are using a script in ([.gitpod.yml](.gitpod.yml)) we need to point the script to a program to interpret it.

eg. `source ./bin/install_terraform_cli`

#### Linux Permissions Considerations

In order to make our bash scripts executable we need to change linux permission for the fix to be executable at the user mode.

```sh
chmod u+x ./bin/install_terraform_cli
```

alternatively:

```sh
chmod 744 ./bin/install_terraform_cli
```

[chmod WiKi](https://en.wikipedia.org/wiki/Chmod)

## Gitpod Lifecycle

Below you can find life cycle for New WorkSpace, Restart WorkSpace and Start Snapshot:



![New WorkSpace](assets/Gitpod-execution-order-New.jpeg)

![Restart WorkSpace](../assets/Gitpdod-execution-order-Restart.png)

![Start Snapshot](../assets/Gitpdod-execution-order-StartSnapshot.png)


[](https://www.gitpod.io/docs/configure/workspaces/tasks)
[](https://www.gitpod.io/guides/gitpodify)

