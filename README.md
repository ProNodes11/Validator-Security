## Uptime Control

Since the uptime of the validator is very important, we use two ways to monitor it. The first is Tenderduty, and the second is our own Telegram bot, which notifies us about problems with the validator. If we are notified of something wrong, we immediately check the validator server for problems.

We always make a backup copy of the validator key and store it outside the server with the validator. If the validator stops working and we cannot restore it quickly, we move the keys to the node used for snapshots until the problems with the validator are resolved. When porting, we carefully monitor the process so that we do not accidentally get slashed for a double sign. We stop the validator, then transfer the keys to another node, and only after double-checking that the main node is powered down do we restart the backup node.

## Server Security

Since keys and wallets are stored on the server, to reduce their security risks, we configured the server as follows. We use ssh keys with a password to access the server and a custom port for ssh connections. If a third party gets the key, he will only be able to access the server with the password, and vice versa. The probability of a key and password being stolen simultaneously is very low since they are stored in different places. Even if this were to happen, an attacker would not be able to gain full access to the server because we do not use the root user but only create admin accounts that also require a password. This gives us time to react if the server's security is compromised.

To protect against other server attacks, we use Firewalls and Fail2ban to reduce their potential damage.

## Validator Security

After creating the validator, in order to maintain access to it even if the server is physically destroyed, we make backups of all necessary files, encrypt them on the server, and upload them to an external storage location. This way, the keys are not unprotected when transferred to another place.
