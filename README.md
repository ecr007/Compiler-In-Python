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
