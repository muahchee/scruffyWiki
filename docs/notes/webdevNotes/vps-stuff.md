VPS stuff
========================

## Get ip address

`hostname -I`

## setting up ssh keys

[https://linuxize.com/post/how-to-set-up-ssh-keys-on-debian-10/](https://linuxize.com/post/how-to-set-up-ssh-keys-on-debian-10/)

- so i don't need to use a password

### Problem

Not needing a password is great and all, but after I did this, my SFTP setup in FileZilla stopped working. It connected to the cloudpanel site with the site user and a password.

The error message is `No supported authentication methods available (server sent: publickey)`

### solution:
- in FileZilla, continue using the same site user for the username field
- locate the private and public (`.pub`). key pairs  They're usually in the .ssh folder. It might be hidden so make sure you enable viewing hidden folders.
- Copy the contents of the public key file.
- in cloudpanel, go to the site's file manager and look for the `authorized_keys` file. Paste the copied public key.
- in FileZilla, change the Logon Type in the Site Manager Settings to "Key File". Link your private key file in the Key File field. You might have to change the displayed file types from "PPK files" to "All Files" if nothing shows up.
- it should work now


## syncing folders between users

[source](https://unix.stackexchange.com/questions/203846/how-to-sync-two-folders-with-command-line-tools)

you need to do this from root

`rsync -avu --delete "/home/user/A/" "/home/user/B"`

A is the source

you can set up a [cron job](PostgreSQL.md#cron%20job%20backups) to automate this