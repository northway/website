---
icon: lucide/screen-share

tags:
  - linux
  - terminal
  - screen
  - window
---

# Screen

[Screen](https://linux.die.net/man/1/screen) is a full-screen window manager that multiplexes a physical terminal between several processes (typically interactive shells). Each virtual terminal provides the functions of a DEC VT100 terminal and, in addition, several control functions from the ISO 6429 (ECMA 48, ANSI X3.64) and ISO 2022 standards (e.g. insert/delete line and support for multiple character sets).  There is a scrollback history buffer for each virtual terminal and a copy-and-paste mechanism that allows moving text regions between windows.

## Install Linux GNU Screen

```bash
sudo apt install screen
```

## Basic Linux Screen Usage

### Create a session

```bash
screen -S session_name
```

Now you are in the new screen session, you can run your desired program or command.

If you want to keep this session alive, use the key sequence ++ctrl+a++ then ++ctrl+d++ to detach from the screen session without closing it.

### List screen session

```bash
screen -ls
```

### Reattach to the screen session

```bash
screen -r
```

In case you have multiple sessions already, you need to specify which session you would to reattach to:

```bash
screen -ls

There are screens on:
        18181.htop      (03/10/2026 02:21:51 PM)        (Detached)
        18093.wget      (03/10/2026 02:21:42 PM)        (Detached)
        17178.zen       (03/10/2026 12:19:02 PM)        (Detached)
3 Sockets in /run/screen/S-northway.
```

If you want to restore `screen 10835.pts-0`, then use the following command:

```bash
screen -r htop
```

These are also working options:

```bash
screen -r 18181

screen -r 18181.htop
```

## Windows

In GNU screen, a session and a window are two different levels of organization — think of it like a browser: a session is the browser process, and windows are the tabs inside it.

Here are some key sequences to work with windows:

| Command | Description |
| ------- | ----------- |
| `Ctrl + a c` | Create a new window (with shell) | 
| `Ctrl + a "` | List all window |
| `Ctrl + a 0` | Switch to window 0 (by number ) |
| `Ctrl + a A` | Rename the current window |
| `Ctrl + a S` | Split current window horizontally into two windows |
| `Ctrl + a |` | Split current window vertically into two windows |
| `Ctrl + a tab` | Switch the input focus to the next window |
| `Ctrl + a Ctrl + a` | Toggle between the current and previous window |
| `Ctrl + a Q` | Close all windows but the current one |
| `Ctrl + a X` | Close the current window |
