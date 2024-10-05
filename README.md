# Compiler-In-Python

## Convert icon in Unix
```
convert img.png img.ico
```

## Install pyinstaller

https://pyinstaller.org/en/stable/

```shell
pip install pyinstaller
```

## Compile with PyInstaller 

```
pyinstaller --onefile --icon=your_icon.ico main.py
```

**Options**

- "--onfile": to generate one executable
- "--icon=PATH": to attach icon

## How to prevent to close Terminal

```pyhton
## Add this funciton to end file
def keep_terminal_open():
	if sys.platform.startswith('win'):
		input("Press Enter to exit...")
	else:
		try:
			input("Press Enter to exit...")
		except EOFError:
			pass
```

## How to prevent errors with dependencies

1 - Locate or Generate the Spec File: If you haven't already generated the .spec file, you can do so by running:

```pyinstaller --name your_program_name --onefile run.py```

2 - Modify the Spec File: Open the .spec file that was generated, and find the Analysis section. You will need to add each of the ```hl7apy / OR another package``` version directories as data files so they are included in the final executable.

Here’s how your Analysis section should look with all the version directories included:

```sh
a = Analysis(
    ['run.py'], # Init name
    pathex=['C:\\path\\to\\your\\script'],  # Modify this with your actual script path
    binaries=[],
    datas=[
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_1', 'hl7apy\\v2_1'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_2', 'hl7apy\\v2_2'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_3', 'hl7apy\\v2_3'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_3_1', 'hl7apy\\v2_3_1'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_4', 'hl7apy\\v2_4'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_5', 'hl7apy\\v2_5'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_5_1', 'hl7apy\\v2_5_1'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_6', 'hl7apy\\v2_6'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_7', 'hl7apy\\v2_7'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_8', 'hl7apy\\v2_8'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_8_1', 'hl7apy\\v2_8_1'),
        ('C:\\PROGRAM DIRECTORY NAME\\Lib\\site-packages\\hl7apy\\v2_8_2', 'hl7apy\\v2_8_2')
    ],
    hiddenimports=[],
    hookspath=[],
    runtime_hooks=[],
    excludes=[],
    win_no_prefer_redirects=False,
    win_private_assemblies=False,
    cipher=None,
    noarchive=False,
)
```
3 - Rebuild the Executable: After saving your changes to the .spec file, rebuild the executable with:

```pyinstaller your_program_name.spec```

