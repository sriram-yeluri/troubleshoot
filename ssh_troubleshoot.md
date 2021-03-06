## SSH Connection Failure

* The server might not be configured to accept public key authentication. Make sure /etc/ssh/sshd_config on the server contains PubkeyAuthentication yes. Remember to restart the sshd process on the server.
* If trying to login as root, the server might not be configured to allow root logins. Make sure /etc/sshd_config includes PermitRootLogin yes, PermitRootLogin prohibit-password, or without-password. If it is set to forced-commands-only, the key must be manually configured to use a forced command (see command= option in ~/.ssh/authorized_keys.
* Make sure the client allows public key authentication. Check that /etc/ssh/config includes PubkeyAuthentication yes.
Try adding -v option to the ssh command used for the test. Read the output to see what it says about whether the key is tried and what authentication methods the server is willing to accept.
* OpenSSH only allows a maximum of five keys to be tried authomatically. If you have more keys, you must specify which key to use using the -i option to ssh.
