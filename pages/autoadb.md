# Esempio: Video4Linux + AutoAdb

````md magic-move
```bash
sudo modprobe v4l2loopback
```

```bash
v4l2-ctl --list-devices
```

```bash
virtual_cam=$(v4l2-ctl --list-devices | awk '/v4l2loopback/{getline; gsub(/[\t ]/, ""); print}')
```

```bash
autoadb scrcpy --v4l2-sink=$virtual_cam --no-video-playback
```
````

Output:
````md magic-move {at: +1}

```md
​
```

```bash
OBS Virtual Camera (platform:v4l2loopback-000):
        /dev/video0

Integrated Camera: Integrated C (usb-0000:05:00.3-3):
        /dev/video1
        /dev/video2
        /dev/media0
```

```bash
/dev/video0
```

```bash
* daemon not running; starting now at tcp:5037
* daemon started successfully
Detected device 192.168.1.103:39445
scrcpy 3.1 <https://github.com/Genymobile/scrcpy>
INFO: No video mirroring, SDK mouse disabled
INFO: ADB device found:
INFO:     --> (tcpip)  192.168.1.103:39445             device  Pixel_8_Pro
/usr/share/scrcpy/scrcpy-server: 1 file pushed, 0 skipped. 75.5 MB/s (90640 bytes in 0.001s)
[server] INFO: Device: [Google] google Pixel 8 Pro (Android 14)
INFO: Renderer: opengl
INFO: OpenGL version: 4.6 (Compatibility Profile) Mesa 24.3.3
INFO: Trilinear filtering disabled
INFO: v4l2 sink started to device: /dev/video0
```
````