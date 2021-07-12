# Swayfade

Fades windows when focused/unfocused, mimicking behaviour from X compositors
such as [picom](https://github.com/yshui/picom).

### Usage

Requires Python 3.8+ and libraries in `requirements.txt` (namely `i3ipc`
and `toml`). Run `swayfade.py` or add it to your sway config:

```
exec <path>/swayfade.py
```

### Configuration

The script checks `$XDG_CONFIG_HOME/swayfade.toml` or, if `XDG_CONFIG_HOME`
is unset, then `~/.config/swayfade.toml`. The following options are available:

* **focused**: default focused window opacity. Default: `1`
* **unfocused**: default unfocused window opacity. Default: 0.7
* **rate**: Delay between each step in fade. Default: 0.016
* **steps**: Number of steps between opacity changes. Default: 14
* **rules**: List of rules for specific windows. Default is none.

#### Rules

Each rule is an object with the following values:
* **app_id**: window app_id to match. Optional.
* **floating**: whether to include or exclude floating windows. Optional.
* **focused**: Opacity when focused.
* **unfocused**: Opacity when unfocused.

Here is an example:

```toml
rules = [
  { app_id = "mpv", focused = 1, unfocused = 1 },
  { floating = true, focused = 0.8, unfocused = 1 }
]
```
