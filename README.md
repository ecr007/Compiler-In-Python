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
