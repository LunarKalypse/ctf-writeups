# Trapped in Plain Sight 1:
```sh
ssh -p 4302 trapped@challenge.utctf.live
```

### Poking around:

flag.txt is not readable and owned by the account "noaccess"

sudo was not a command, so can't do sudo -l to see sudoable binaries

### Solution:
```sh
find / -perm -u=s -type f 2>/dev/null
```

Used this command to find suid binaries

I noticed that xxd command had suid bit set.
**Eureka!**

```sh
xxd flag.txt
```

Flag output in format utflag{}

This works because the **suid bit** allows whoever is executing the file (in this case xxd) to execute it as the owner, in this case iirc root.

So, it executed xxd as root which read the file.
