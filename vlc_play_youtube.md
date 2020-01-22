
referer: https://www.latecnosfera.com/2016/10/vlc-unable-to-open-mrl.html

# Solution

Overwrite `youtube.luac` by [Github version](https://github.com/videolan/vlc/blob/master/share/lua/playlist/youtube.lua), then it works.

Path contain `youtube.luac`:
```
Windows 64-bit: C:\Program Files (x86)\VideoLAN\VLC\lua\playlist\
Windows 32-bit: C:\Program Files\VideoLAN\VLC\lua\playlist\
Mac: /Applications/VLC.app/Contents/MacOS/share/lua/playlist/
64-bit Linux: /usr/lib64/vlc/lua/playlist/
32-bit Linux: /usr/lib/vlc/lua/playlist/
```
