# 1 Prerequisites
```Homebrew
RubyGems
npm
MacOS
git
```

# 2 [iTerm2](https://www.iterm2.com/) and [zsh](https://ohmyz.sh/)
iTerm2 allows versatile customization of the standard OS X terminal. Install it before doing anything else.
`brew cask install iterm2`
Next install zsh, a replacement terminal shell that allows further customization.
`sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`
The zsh config file is located at ~/.zshrc and effectively replaces your bashprofile. update your PATH variable. If you have modified your .bash_profile, you can simply add 
`source ~/.bash_profile`
to the bottom of your zshrc file. Themes may also be set and configured in this file.
Note: zsh comes with a number of preconfigured [aliases.](https://github.com/robbyrussell/oh-my-zsh/wiki/Cheatsheet)

# 3 [tmux](https://github.com/tmux/tmux/wiki)
TLDR: tmux is a simple terminal multiplexer that allows you to tile and manage multiple terminal windows at the same time. Essential for l33t h4x0rs.
`brew install tmux`
The tmux config file is located at ~/.tmux.conf. If this doesnt exist, make one yourself. I customized tmux to be a bit more usable since the predefined shortcuts are hard to remember:
- Rebound default prefix from the awkward 'ctrl b' to a more comfortable 'ctrl a'
- Remapped window splitting to 'ctrl |' and 'ctrl -' for vertical and horizontal window splitting, respectively. 
- Mapped pane switching to work with 'alt arrowkey'
- Enabled mouse control

Some useful commands I have found when using tmux (prefixed with 'ctrl a'):
o  swap panes
q  show pane numbers
x  kill pane
|  split horizontally
-  split vertically```
tmux also allows plugins that can further customize it's look and feel with 
[tmux plugin manager](https://github.com/tmux-plugins/tpm)

# 4  [Neovim and vim-plug](https://github.com/neovim/neovim)
Install neovim, a vim fork focused on customizability. Neovim is run directly as 'nvim' and the config file can be found at ~/.config/nvim/init.vim. 
vim-plug is  one of many plugin managers for vim and allows us to install cool plugins like [Nerdtree](https://github.com/scrooloose/nerdtree) and [YouCompleteMe](https://github.com/Valloric/YouCompleteMe). See my init.vim for more details. 

# 5  Making it all pretty

### 5.1  [neofetch] (https://github.com/dylanaraps/neofetch)
A simple command line system information tool mostly used to show off your terminal. Can display custom images. 
`brew install neofetch`

### 5.2  [colorls] (https://github.com/athityakumar/colorls)
An 'ls' replacement that adds icons to the 'colorls' command and allows you to color different filetypes. Note that for icons to display properly, the Knack font must be installed and set under your iterm settings in Profiles > Text > non-ASCII Font. Icon colors can be customized according to this [list of supported colors](https://github.com/sickill/rainbow#color-list)
`gem install colorls`

### 5.2  ncmpcpp + [Mopidy](https://www.mopidy.com/) (mpd) 
Allows usage of spotify through a command line interface. I highly recommend reading [this tutorial](https://www.brettgardiner.net/play-and-visual-spotify-music-in-terminal) for mopidy before attempting to install. 
`brew install ncmpcpp`
[ncmpcpp cheat sheet](https://pkgbuild.com/~jelle/ncmpcpp/)

If you are not Spotify user, simply install mpd and set your audio source folder (where you keep your audio files). 
`brew install mpd`

Otherwise, follow the (somewhat complex) instructions given on the website. 
Note: Spotify playlists do NOT work with mopidy-spotify-web since a recent change to the Spotify API. 
From Spotify you will have to obtain a device ID that authorizes mopidy to connect to Spotify with your account. in your mopidy.conf file, you must set the `client_id` and `client_secret` fields to [generated here](ttps://www.mopidy.com/authenticate/#spotify). 

### 5.3 [cli-visualizer](https://github.com/dpayne/cli-visualizer)
Before installing, make sure your audio output is set properly in your mopidy.conf: 
```[audio]
output = tee name=t t. ! queue ! autoaudiosink t. ! queue ! audioresample ! audioconvert ! audio/x-raw,rate=44100,channels=2,format=S16LE ! wavenc ! filesink location=/tmp/mpd.fifo```
This allows external programs to read your audio data. Purely for visual purposes, there exist multiple music 'visualizers' that run your audio output through a Fourier Transform in order to visually represent frequencies. The resulting graph is then output to our terminal in aesthetically pleasing colors. 
```brew install fftw
brew tap homebrew/dupes
brew install ncurses```
RTDC for customization of colors and styles.

# 6  Miscellaneous
This section is for miscellaneous customisation of OS X and doesn't directly pertain to a terminal workflow. 

### 6.1 Window managers
Window managers such as i3 are very popular in linux. Fortunately, Macs have an alternative that works just as well. kwm and chunkwm are both solid window managers created by the same developer with the former being the 'proof of concept' version. Note that while kwm is deprecated, chunkwm is still a bit unstable as not all of the bugs have been worked out yet. Nevertheless, both function fine. 
- [kwm](https://github.com/koekeishiya/kwm)
- [chunkwm](https://github.com/koekeishiya/chunkwm)

### 6.2 [Ubersicht](http://tracesof.net/uebersicht/)
Widgets, who doesn't like widgets? This allows you to display HTML5 widgets on your desktop and customize them from a neat manager. You can find more widgets [here](http://tracesof.net/uebersicht-widgets/). Note that if you want to edit/move them you will have to edit HTML. Fun way to learn basic HTML syntax.

### 6.3 Sublime Fun
Useful hotkeys:

|Description|Command|
|---|---|
|Box selection| Option + Left Click Drag|
|File switch| Command + T|
|Multiple selection| Command + D|
|Add all lines to selection| Command + Shift + L|
|Add single line to selection| Ctrl + Shift + Up/Down|
|Search/Replace within file| Command + Alt + F|
|S/R across all files| Command + Shift + F|

Color Scheme: Gruvbox
Themes: Afterglow

### 6.4 Chrome Extensions
- BehindTheOverlay (gets rid of annoying adblock notifications on news websites)
- PrivacyBadger (blocks trackers and other bad stuff)
- Vimium (use chrome with vim shortcuts, my favorite addon!)
- Tamper Chrome (intercept HTTP requests easily)
- Stylus (customize websites by editing css elements)
- Wikiwand (prettier looking wikipedia) 
