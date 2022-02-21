### webview::webview
```
webview(bool debug = false, void *wnd = nullptr)
```
Example:
```
// Create new webview instance "w"
webview::webview w(true, nullptr);
```

### webview::set_title
```
void set_title(const std::string title)
```
Example:
```
w.set_title("Minimal example");
```

## webview::set_size
```
void set_size(int width, int height, int hints)
```
Example:
```
w.set_size(480, 320, WEBVIEW_HINT_NONE);
```

### webview::navigate
```
void navigate(const std::string url)
```
Example:
```
w.navigate("https://en.m.wikipedia.org/wiki/Main_Page");
```

### webview::run
```
void run()
```
Example:
```
w.run();
```

...

```
webview_t w = webview_create(0, NULL);
webview_set_title(w, "Webview Example");
webview_set_size(w, 480, 320, WEBVIEW_HINT_NONE);
webview_navigate(w, "https://en.m.wikipedia.org/wiki/Main_Page");
webview_run(w);
webview_destroy(w);
```
