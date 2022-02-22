# API

### webview::webview
Creates a new webview instance. If debug is non-zero - developer tools will  
be enabled (if the platform supports them). Window parameter can be a  
pointer to the native window handle. If it's non-null - then child WebView  
is embedded into the given parent window. Otherwise a new window is created.  
Depending on the platform, a GtkWindow, NSWindow or HWND pointer can be  
passed here.
```
webview(bool debug = false, void *wnd = nullptr)
```

### webview::set_title
Updates the title of the native window. Must be called from the UI thread.
```
void set_title(const std::string title)
```

### webview::set_size
Accepts a `WEBVIEW_HINT`.  
```
#define WEBVIEW_HINT_NONE 0
#define WEBVIEW_HINT_MIN 1
#define WEBVIEW_HINT_MAX 2
#define WEBVIEW_HINT_FIXED 3
```
```
void set_size(int width, int height, int hints)
```

### webview::navigate
Navigates webview to the given URL. URL may be a data URI, i.e.  
"data:text/text,<html>...</html>". It is often ok not to url-encode it  
properly, webview will re-encode it for you.  
```
void navigate(const std::string url)
```

### webview::run
Runs the main loop until it's terminated. After this function exits - you  
must destroy the webview.  
```
void run()
```

# Compiling

### Linux  
```
c++ main.cc `pkg-config --cflags --libs gtk+-3.0 webkit2gtk-4.0` -o webview-example
```

### MacOS
```
c++ main.cc -std=c++11 -framework WebKit -o webview-example
```

### Windows (x64)
The `webview.exe` file will be in the build directory.  
```
script/build.bat
```

# Examples
Hello World:
```
#include "webview.h"
int main() {
  webview::webview w(true, nullptr);
  w.set_title("Minimal example");
  w.set_size(480, 320, WEBVIEW_HINT_NONE);
  w.navigate("https://en.m.wikipedia.org/wiki/Main_Page");
  w.run();
  return 0;
}
```

Complex Example:
```
#include "webview.h"
#include <iostream>

int main() {
  webview::webview w(true, nullptr);
  w.set_title("Example");
  w.set_size(480, 320, WEBVIEW_HINT_NONE);
  w.set_size(180, 120, WEBVIEW_HINT_MIN);
  w.bind("noop", [](std::string s) -> std::string {
    std::cout << s << std::endl;
    return s;
  });
  w.bind("add", [](std::string s) -> std::string {
    auto a = std::stoi(webview::json_parse(s, "", 0));
    auto b = std::stoi(webview::json_parse(s, "", 1));
    return std::to_string(a + b);
  });
  w.navigate(R"V0G0N(data:text/html,
    <!doctype html>
    <html>
      <body>hello</body>
      <script>
        window.onload = function() {
          document.body.innerText = `hello, ${navigator.userAgent}`;
          noop('hello').then(function(res) {
            console.log('noop res', res);
          });
          add(1, 2).then(function(res) {
            console.log('add res', res);
          });
        };
      </script>
    </html>
  )V0G0N");
  w.run();
  return 0;
}
```
