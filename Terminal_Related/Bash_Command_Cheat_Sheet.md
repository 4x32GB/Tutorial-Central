<h1 style="text-align:center;color:#FF8C00"> Bash Cheat Sheet</h1>

## Need Help?

Using the man Command 

```bash
man <commandname> ex: man touch
```

Using the --help Argument

```bash
touch --help
```

## Files & Directories

Deleting a Non-Empty Directory (All Sub-Directories and Children)

```Bash
rm -rf <directoryname>
```

Deleting an Empty Directory

```bash
rmdir <directoryname>
```

Creating a File in the Current Directory

```bash
touch <filename> <directoryname>
```

Creating a File in Another Directory (although a bit long of a command I feel it's bulletproof)

```bash
touch <filename> && mv <directoryname>
```

## Check Hard-Disk 