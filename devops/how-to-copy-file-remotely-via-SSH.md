# How to copy file remotely via SSH

The command `scp` can be used to copy a file from a remove server to a local machine.

```bash
$ scp remoteuser@remoteserver:/remote/folder/myfile.txt  myfile.txt
```

where:
- *remoteuser* is the user used to login in the remote machine;
- *remoteserver* is the remove machine ip address.
