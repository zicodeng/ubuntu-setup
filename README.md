# Ubuntu Setup

Setup guide for Ubuntu.

## i3

i3 is a **tiling window manager** that provides functionality to efficiently control the windows on the screen. Windows are laid out on the screen in logical subdivisions which can be quickly navigated through keyboard shortcuts.

### Installation

    sudo apt install i3

### Keyboard Shortcuts

https://i3wm.org/docs/refcard.html

### Customization

-   Create an i3 config file.

    -   Open your terminal and type: `i3-config-wizard`
    -   Note: i3 config file might already exists. Check your `~/.config/i3/` directory.

-   Add lock screen keyboard shortcut and customize lock screen wallpaper.

    -   Open i3 config file and add the following line: `bindsym $mod+shift+x exec i3lock -i /home/zicodeng/Pictures/lock-screen-wallpaper.png`

    -   Note: only images with **png** extension are supported.

-   Customize empty workspace wallpaper.

    -   Install **feh**: `sudo apt install feh`
    -   Open i3 config file and add the following line: `exec_always feh --bg-scale /home/zicodeng/Pictures/workspace-wallpaper.jpg`. This puts feh in always executing mode.

-   Rename workspace.

    -   By default, workspaces are named with natural numbers: 1, 2, 3...
    -   Open i3 config file and find `# switch to workspace` section, from which we can rename workspaces. You might also want to make changes correspondingly in `# move focused container to workspace` section (tip: create some variables).

-   Auto-create a specified workspace for a given application.

    -   Find the application class name:

        -   Open an application and open a terminal next to it. Type `xprop`
        -   Now use the cursor to click the application.
        -   Once you have clicked the application, the terminal will display information about that application. Find the line that starts with **WM_CLASS(STRING)** and copy the second value. This string value is the application's class name.

    -   Open i3 config file and add the following line: `assign [class="<app-class-name>"] <workspace-name>`

-   Customize font.

    -   Install font:

        -   Download your desired font and unzip it.
        -   `cd` to the unzipped directory.
        -   Look for fonts with **.ttf** extension. `mv` them all to `~/.fonts/` directory. The system will pick up all fonts under this directory automatically.

    -   Change font-relevant settings in i3 config: `font pango: <your-awesome-font> <font-size>`

-   After modifying i3 config file, don't forget to apply the changes by restarting i3 (**Mod+Shift+R**).

## Rofi

Rofi is an application launcher and dmenu replacement.

### Installation

    sudo apt install rofi

### Integration with i3

-   Open i3 config file.
-   Comment out `bindsym $mod+d exec dmenu_run`
-   Add `bindsym $mod+d exec rofi -show run`

### Theme

Use **rofi-theme-selector** to apply different themes.

## Tmux

Tmux is a terminal multiplexer that allows you to control multiple terminals from a single terminal.

### Installation

    sudo apt update
    sudo apt install tmux
    tmux -V

### Keyboard Shortcuts

https://tmuxcheatsheet.com/

### Integration with i3

-   Open i3 config file.
-   Comment out `bindsym $mod+Return exec i3-sensible-terminal`
-   Add `bindsym $mod+Return exec tmux new`

## Z Shell

Zsh is a more advanced shell for \*nix. It offers more powerful features than BASH.

### Features

-   Auto-change directory: if you know the directory name, you can just simple type `cd **/name-of-dir`
-   More advanced tab completion: you can use arrow key to navigate between options.
-   Path expansion

### Installation

    sudo apt install zsh

## Oh My Zsh

Oh My Zsh is a community-driven framework for managing zsh configuration.

### Installation

https://github.com/robbyrussell/oh-my-zsh

## Shutter

A screen capture tool for Linux.

### Installation

    sudo apt install shutter

### Commands

`shutter --full`: Capture a selected area.

`shutter --full`: Capture the entire screen.
