# Pipe cmd Output to Clipboard

Windows provides a way to redirect output of command line to the Windows clipboard by using `clip` on the cmd. The output can be pasted into other programs. There are 2 ways to use clip:

Copy the output of the given command into the clipboard

```cmd
dir | clip
```

Copy the content of a file into the clipboard

```cmd
clip < README.md
```