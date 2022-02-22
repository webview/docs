# WebView

A tiny cross-platform webview library to create a common HTML5 UI abstraction layer frontend with your favorite programming language as the backend!

This library is written in C/C++ and has bindings for many others. See the sidebar for an API reference in each specific language.

It supports two-way JavaScript bindings (to call JavaScript from the backend-language and to call the backend-language from JavaScript).

It uses Cocoa/WebKit on macOS, gtk-webkit2 on Linux and Edge on Windows 10.

## Dependancies

*Windows*
- Windows 10 SDK via Visual Studio Installer
- C++ support via Visual Studio Installer
- See [Microsoft Docs](https://docs.microsoft.com/en-us/microsoft-edge/webview2/get-started/win32)
for more info

*Ubuntu*
- `sudo apt install webkit2gtk-4.0`
- Try webkit2gtk-4.0-dev if webkit2gtk-4.0 is not found

*OpenBSD*
- requires `wxallowed` [mount(8)](https://man.openbsd.org/mount.8) option

*FreeBSD*
- `pkg install webkit2-gtk3`

*MacOs*
- Just build it!
