# Sublime Terminal
[![Latest Release](https://img.shields.io/github/tag/CodeByZach/sublime_terminal.svg?label=version)](https://github.com/CodeByZach/sublime_terminal/releases)

Shortcuts and menu entries for opening a terminal at the current file, or any directory in [Sublime Text](http://sublimetext.com/).

## Installation

Download [Package Control](https://packagecontrol.io/) and use the *Package Control: Install Package* command from the command palette. Using Package Control ensures Terminal will stay up to date automatically.

## Usage

- **Open Terminal at File**
    Press *alt+shift+t* on Windows, Linux, or macOS.
- **Open Terminal at Project Folder**
    Press *ctrl+alt+shift+t* on Windows, Linux, or macOS.

In addition to the key bindings, terminals can also be opened via the editor context menu and the sidebar context menus.

## Package Settings

The settings can be viewed and edited by accessing the *Preferences > Package Settings > Terminal > Settings* menu entry. 

- **terminal**
    - The terminal to execute, will default to the OS default if blank.
    - Default: `""`
- **parameters**
    - The parameters to pass to the terminal. These parameters will be used if no [custom parameters](#custom-parameters) are passed.
    - Default: `[]`
- **env**
    - The environment variables changeset. Default environment variables used when invoking the terminal are inherited from Sublime Text.
    - The changeset may be used to overwrite/unset environment variables. Use `null` to indicate that the environment variable should be unset.
    - Default: `{}`

## Custom Parameters

By passing parameters argument to the `open_terminal` or `open_terminal_project_folder` commands, it is possible to construct custom terminal environments. You can do so by creating custom [key bindings](https://www.sublimetext.com/docs/key_bindings.html) that call these commands with the arguments you want, as we'll document here, or by adding custom [command palette](https://docs.sublimetext.io/reference/command_palette.html) or [menu entries](https://docs.sublimetext.io/reference/menus.html). 

The following is an example, of passing the parameters `-T 'Custom Window Title'` to an XFCE terminal.

```json
{
    "keys": ["ctrl+alt+t"],
    "command": "open_terminal",
    "args": {
        "parameters": ["-T", "Custom Window Title"]
    }
}
```

A parameter may also contain the *%CWD%* placeholder, which will be substituted with the current working directory the terminal was opened to.

```json
{
    "keys": ["ctrl+alt+t"],
    "command": "open_terminal",
    "args": {
        "parameters": ["-T", "Working in directory %CWD%"]
    }
}
```

## Example configurations

Here are some example configurations calling different terminals. Note that paths to executables might differ on your machine.

### Cmder on Windows

```json
{
    "terminal": "C:\\Program Files\\cmder_mini\\cmder.exe",
    "parameters": ["/START", "%CWD%"]
}
```

### xterm on GNU/Linux

```json
{
    "terminal": "xterm"
}
```

### gnome-terminal for CJK users on GNU/Linux

We unset LD_PRELOAD, as it may cause problems for Sublime Text with imfix.

```json
{
    "terminal": "gnome-terminal",
    "env": {"LD_PRELOAD": null}
}
```
### iTerm on macOS

```json
{
    "terminal": "iTerm.sh"
}
```

### iTerm on macOS (with tabs)

```json
{
    "terminal": "iTerm.sh",
    "parameters": ["--open-in-tab"]
}
```

### iTerm2 v3 on macOS

```json
{
    "terminal": "iTerm2-v3.sh"
}
```

### Hyper on macOS

```json
{
    "terminal": "hyper.sh"
}
```

### Kitty on macOS

```json
{
    "terminal": "/opt/homebrew/bin/kitty",
    "parameters": ["-d", "%CWD%"]
}
```

### [Windows Terminal](https://github.com/microsoft/terminal)

```json
{
    "terminal": "C:/Users/yourusername/AppData/Local/Microsoft/WindowsApps/wt.exe",
    "parameters": ["-d", "."]
}
```