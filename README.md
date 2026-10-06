# winpwnage-autorun

A standalone Windows executable that automatically triggers a
[WinPwnage](https://github.com/rootm0s/WinPwnage) UAC bypass when launched —
no command-line arguments, no Python installation, no dependencies.

Built for **red team engagements, penetration testing, and security research**
where a single-click payload is more useful than a script.

## What it does
On execution, the binary behaves exactly as if you had run:

`python main.py --use uac --id 13 --payload c:\windows\system32\cmd.exe`

Why method 13? Because it actually works and doesn't even trigger Windows defender (Windows 11).

## Download
You can download the pre-compiled executable from the [Releases](../../releases) page. 
No Python installation is required to run the compiled executable.

## Build from Source
If you prefer to build it yourself, follow the instructions in the Build section below.
