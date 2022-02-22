# Alternatives to WebView

When it comes to creating a desktop app with a web frontend, there are many options  
outside WebView.

See an extensive list of Electron alternatives here: https://github.com/sudhakar3697/electron-alternatives

## Don't Make a Desktop App
A good portion of WebView apps could have been much better as web apps or browser  
extensions. Please consider this as you research what library is best for you.

## Non HTML/CSS/JS Frameworks
Chances are, HTML/CSS/JS is *not* the right choice for your app, especially  
if it's a tool (designed to do one thing). Using HTML/CSS/JS as your frontend  
can be justified when your frontend is bigger than your backend.

- [GTK](https://petabyt.dev/blog/tiny-windows-linux-gtk-apps)
- [LCUI](https://github.com/lc-soft/LCUI)
- Qt
- ncurses

## Chrome/Chromium Rendering Backend
Using Chrome/Chromium as a web backend is very useful, since most people have it  
installed, and know how to install it.

- https://github.com/zserge/lorca
- https://github.com/pojala/electrino

## WebView Compatible Libraries
- https://github.com/jchv/go-webview2

## Android
WebView doesn't officially support android, but it's not too hard to get a  
webview up and running there.  
- https://github.com/petabyt/ndkhellohtml
- https://github.com/petabyt/gowebview

## Watching
- https://github.com/alifcommunity/webui
