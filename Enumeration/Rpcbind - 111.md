Since that we have verified that an NFS service is running (2049/TCP open NFS), we can deepen and see what else we can obtain.

### Basic Commands
```bash
showmount -e 10.10.25.33
sudo mount 10.10.25.33:/users /mnt/users
sudo mount -t nfs 10.10.25.33:/users /mnt/users

```