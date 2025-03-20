# Trapped in Plain Sight 2

flag.txt is literally readable by nothing but root

```
ls -la flag.txt
```
Turns out flag.txt has a + at the end of file perms, this means there are more access control 
list settings

Kind of like this:
```sh
-rw-rw----+ 1 root  root   0 Jan  9 16:33 examplefile
```

Used:
```sh
getfacl flag.txt
```

secretuser can read flag.txt, but you are "trapped" user

read /etc/passwd, user secretuser has hunter2 as the group

### Login to secretuser
This refers to an old linux meme where a user posted his password in an IRC after being told it would be auto censored to asterisks

```
su secretuser
```
Enter pass "hunter2"

**Read flag.txt**

## Meme Referenced

The meme chat they referred to is below:

```
<Cthon98> hey, if you type in your pw, it will show as stars
<Cthon98> ********* see!
<AzureDiamond> hunter2
<AzureDiamond> doesnt look like stars to me
<Cthon98> <AzureDiamond> *******
<Cthon98> thats what I see
<AzureDiamond> oh, really?
<Cthon98> Absolutely
<AzureDiamond> you can go hunter2 my hunter2-ing hunter2
<AzureDiamond> haha, does that look funny to you?
<Cthon98> lol, yes. See, when YOU type hunter2, it shows to us as *******
<AzureDiamond> thats neat, I didnt know IRC did that
<Cthon98> yep, no matter how many times you type hunter2, it will show to us as *******
<AzureDiamond> awesome!
<AzureDiamond> wait, how do you know my pw?
<Cthon98> er, I just copy pasted YOUR ******'s and it appears to YOU as hunter2 cause its your pw
<AzureDiamond> oh, ok.
```
