---
anchor: what-is-the-account-and-password-used-to-log-in-to-the-command-line
weight: 980
lang: en
---
In the FydeOS for PC version, you can use the username `chronos` to log in to the system's command line (shell) environment. The account does not set a password by default. In addition, the account can also use the `sudo` command to escalate rights.

In FydeOS VM for VMWare, the password of the `chronos` account is `test0000`. Please note that the `chronos` account contains a public, insecure public key for debugging in the FydeOS VM for VMWare. Please do not use FydeOS VM for VMWare as a tool in a production environment.

For security reasons, we recommend that you change the password as soon as possible.

For how to change the password of FydeOS, please refer to [this knowledge base document](/en/recipes/chronos-password/).
