---
layout: two-cols
---

<ScrcpyWebcam width="540px" height="1170px"/>

::right::

```html
<template>
    <video id="scrcpy-webcam" autoplay muted></video>
    <button id="start-button">Avvia stream V4L</button>
</template>
```

```ts twoslash
  let button = document.getElementById('start-button');
  let video = document.getElementById('scrcpy-webcam') as HTMLVideoElement;
  button?.addEventListener('click', function() {
      const facingMode = "environment"; // Webcam frontale: "user", Altra webcam: "environment"
      const constraints = {
          audio: false,
          video: {
              facingMode: facingMode,
              width: { ideal: 2336 },
              height: { ideal: 1080 },
          }
      };
      navigator.mediaDevices.getUserMedia(constraints)
          .then(stream => {
              video.srcObject = stream;
          })
          .catch(error => {
              console.error("Error accessing the camera", error);
          });
  })
```