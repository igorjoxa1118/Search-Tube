# Search-Tube

PKGBUILD must be built. If not, then the paths to the scripts may not be correct

```python
sudo pacman -S mpv yad socat jq yt-dlp
yay -S zscroll-git
yay -S ytdlp-gui
git clone https://github.com/igorjoxa1118/Search-Tube.git
cd Search-Tube
makepkg -s
sudo pacman -U [pakage.zst]
```

Polybar module for i3

```python
[module/mpv-youtube-icon]
type = custom/text
content = " "
content-font = 0
content-background = #16161E
content-foreground = #2ac3de
content-padding = 0
click-left = "$HOME/.local/bin/Search-Tube/mpv-youtube-playlist.sh" &
click-middle = "$HOME/.local/bin/Search-Tube/mpv-youtube-kill.sh" &
```

```python
[module/mpv]
type = custom/script
exec-if = pidof mpv 
exec = "$HOME/.local/bin/Search-Tube/mpv-zscroll.sh"
tail = true
click-left = echo 'cycle pause' | socat - /tmp/mpv_socket
click-middle = "$HOME/.local/bin/Search-Tube/mpv-youtube-kill.sh"
scroll-up = "$HOME/.local/bin/Search-Tube/polybar-mpv/mpv.sh" --volume-up
scroll-down = "$HOME/.local/bin/Search-Tube/polybar-mpv/mpv.sh" --volume-down
format-foreground = #2ac3de
format-background = #16161E
format-underline = #2ac3de
```

```python
[module/mpv-prev]
type = custom/script
exec-if = pidof mpv
exec = echo " "
click-left = echo 'playlist-prev' | socat - /tmp/mpv_socket
format-foreground = #2ac3de
format-background = #16161E
```

```python
[module/mpv-next]
type = custom/script
exec-if = pidof mpv
exec = echo " "
click-left = echo 'playlist-next' | socat - /tmp/mpv_socket
format-foreground = #2ac3de
format-background = #16161E
```
Polybar config.ini

```python
modules-left = mpv mpv-prev mpv-next
modules-center = mpv-youtube-icon
modules-right = 
```