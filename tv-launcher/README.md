# TV Launcher

A tvOS-style home screen for any smart TV browser: a big "top shelf" preview
and a grid of streaming apps (Netflix, YouTube, Tubi, Prime Video, Disney+, Hulu,
Max, and more). Navigate with the remote's arrow keys and press OK to open an app.

## Put it on your TV (192.168.100.15)

1. On a computer on the same Wi-Fi network as the TV, from this folder run:

   ```sh
   python3 -m http.server 8000
   ```

2. Find that computer's local IP (e.g. `192.168.100.20`).
3. On the TV, open its web browser and go to `http://192.168.100.20:8000`.
4. Bookmark it or set it as the browser's home page.

## Android TV / Google TV: install the real apps over the network

If the TV at `192.168.100.15` runs Android TV, turn on **Developer options →
Network debugging**, then from a computer with `adb`:

```sh
adb connect 192.168.100.15:5555
adb shell am start -a android.intent.action.VIEW -d "market://details?id=com.netflix.ninja"
adb shell am start -a android.intent.action.VIEW -d "market://details?id=com.google.android.youtube.tv"
adb shell am start -a android.intent.action.VIEW -d "market://details?id=com.tubitv"
```

Each command opens the Play Store page for that app on the TV; press Install.

## Add or change apps

Edit the `APPS` list in `index.html`: each entry has a name, URL, and tile colors.
