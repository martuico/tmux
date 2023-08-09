.tmux
=====

Self-contained, pretty and versatile `.tmux.conf` configuration file.

![Screenshot](https://cloud.githubusercontent.com/assets/553208/19740585/85596a5a-9bbf-11e6-8aa1-7c8d9829c008.gif)

Installation
------------

Requirements:

  - tmux **`>= 2.4`** running inside Linux, Mac, OpenBSD, Cygwin or WSL
  - awk, perl and sed
  - outside of tmux, `$TERM` must be set to `xterm-256color`

⚠️ Before installing, you may want to backup your existing configuration.

You can install Oh my tmux! at any of the following locations:
- `~`
- `$XDG_CONFIG_HOME/tmux`
- `~/.config/tmux`

Installing in `~`:
```
$ cd ~/.config
$ git clone https://github.com/martuico/tmux.git tmux
```
Bindings
--------

  - `<prefix>` means you have to either hit <kbd>Ctrl</kbd> + <kbd>a</kbd> or <kbd>Ctrl</kbd> + <kbd>b</kbd>
  - `<prefix> c` means you have to hit <kbd>Ctrl</kbd> + <kbd>a</kbd> or <kbd>Ctrl</kbd> + <kbd>b</kbd> followed by <kbd>c</kbd>
  - `<prefix> C-c` means you have to hit <kbd>Ctrl</kbd> + <kbd>a</kbd> or <kbd>Ctrl</kbd> + <kbd>b</kbd> followed by <kbd>Ctrl</kbd> + <kbd>c</kbd>

This configuration uses the following bindings:

 - `<C-e>` opens the `.local` customization file copy with the editor
   defined by the `$EDITOR` environment variable (defaults to `vim` when empty)
 - `<prefix> r` reloads the configuration

 - `<prefix> C-c` creates a new session
 - `<prefix> C-f` lets you switch to another session by name

 - `<prefix> C-h` and `<prefix> C-l` let you navigate windows (default
   `<prefix> n` and `<prefix> p` are unbound)

 - `<prefix> |` splits the current pane vertically
 - `<prefix> _` splits the current pane horizontally
 - `<S-[>`, `<S-]>` let you move to next/last window
 - `<S-Up>`, `<S-Down>`, `<S-Left>`, `<S-Right>` let you navigate panes
 - `<prefix> C-o` let you swap panes
 - `<prefix> +` maximizes the current pane to a new window

 - `<prefix> y` Use tmux-yank


### Using TPM plugins

This configuration now comes with built-in [TPM] support:
- use the `set -g @plugin ...` syntax to enable a plugin
- whenever a plugin introduces a variable to be used in `status-left` or
  `status-right`, you can use it in `tmux_conf_theme_status_left` and
  `tmux_conf_theme_status_right` variables, see instructions above 👆
- ⚠️ do not add `set -g @plugin 'tmux-plugins/tpm'` to any configuration file
- ⛔️ do not add `run '~/.tmux/plugins/tpm/tpm'` to any configuration file

⚠️ The TPM bindings differ slightly from upstream:
  - installing plugins: `<prefix> + I`
  - uninstalling plugins: `<prefix> + Alt + u`
  - updating plugins: `<prefix> + u`

See the sample `.local` customization file for instructions.

[TPM]: https://github.com/tmux-plugins/tpm

### Accessing the macOS clipboard from within tmux sessions (tmux `< 2.6`)

[Chris Johnsen created the `reattach-to-user-namespace`
utility][reattach-to-user-namespace] that makes `pbcopy` and `pbpaste` work
again within tmux.

To install `reattach-to-user-namespace`, use either [MacPorts][] or
[Homebrew][]:

    $ port install tmux-pasteboard

or

    $ brew install reattach-to-user-namespace

Once installed, `reattach-to-usernamespace` will be automatically detected.

[MacPorts]: http://www.macports.org/
[Homebrew]: http://brew.sh/
