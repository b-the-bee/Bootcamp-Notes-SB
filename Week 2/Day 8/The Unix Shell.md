#data-science #data-engineering 

## What, why?
Shells have been around almost since the dawn of computing

![[Pasted image 20240516113732.png]]
Reasons to use shell:
**Installed everywhere**: Desktops, servers, RPis, GUI environments are not
**Lightweight**: HUI environem

![[Pasted image 20240516113841.png]]

![[Pasted image 20240516114205.png]]

/mnt/c/ is where the c drive is mounted on windows, each drive letter has its own "folder" within /mnt/

![[Pasted image 20240516121114.png]]

## ls:

```sh
$ ls -a -l /home/dennis/code
# Can be abbreviated as
$ ls -al /home/dennis/code
```

Lists the contents of the home/dennis/code directory with details (-l) including hidden files -a

## man:
manual, shows the manual page for each function:

```sh
$ man ls
```

This prints out the manual page for ls

## multiple flags:

For example, multiple flags can be done:
```sh
$ ls -SUX
```

Although certain things might not have a shortened version