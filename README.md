# steamdeck_maxwin
A simple bash script to force maximize non-steam apps in Steam Deck's Gamescope. This is intended to work on other resolutions when using an external display.

I made this due to those pesky apps that don't offer an easy way to maximize on init and/or have problems in fullscreen (I am looking at you Discord and Firefox).

## Warning
I am still messing around with this and it probably doesn't work with all applications (specially the apps that limit window dimensions).

# Guide
1) Go into desktop mode.
2) Install the `wmctrl` binary. You can also use the one in this repository and put it on a directory of your choice (I recommend in $PATH). In my case, I have installed it via `pacman` and so it's in `/usr/bin/wmctrl`. The script will try to locate it in any $PATH directory or if set with the `--wmctrl_path` optional argument.
3) Download the `maxwin` file and put it in a directory of your choice, I recommend `~/.local/bin/maxwin`.
4) Add an application to steam. (E.g. right click executable > Add to Steam).
5) Go into gamemode and then to the newly added application properties.
6) Change 'Game Resolution' to 'Native'.
8) Copy the command in 'Target' and append it to the beginning of the 'Launch Options', and change 'Target' to the `maxwin` binary path (e.g. Target was ```/usr/bin/flatpak``` and Launch Options: ```run com.discordapp.Discord``` and it becomes, in my case, Target=```/home/deck/.local/bin/maxwin```  and Launch Options=```/usr/bin/flatpak -- run com.discordapp.Discord```).
9) Modify 'Launch Options' according to the `maxwin` guide (use `maxwin --help` to check help and examples).

# Some examples

## Discord
Target: ```/home/deck/.local/bin/maxwin```

Start in: ```/home/deck/.local/bin/```

Launch Options: ```name "Friends - Discord"```

## Firefox
Target: ```/home/deck/.local/bin/maxwin```

Start in: ```/home/deck/.local/bin/```

Launch Options: ```name "Mozilla Firefox" -- flatpak "run" "--branch=stable" "--arch=x86_64" "--command=firefox" "--file-forwarding" "org.mozilla.firefox" "@@u" "@@"```

## Steamos-nested-desktop
Target: ```/home/deck/.local/bin/maxwin```

Start in: ```/home/deck/.local/bin/```

Launch Options: ```viewable -- "/usr/bin/steamos-nested-desktop"```

