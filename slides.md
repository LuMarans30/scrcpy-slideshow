---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://raw.githubusercontent.com/LuMarans30/scrcpy-slideshow/refs/heads/master/assets/cover.webp
# some information about your slides (markdown enabled)
title: scrcpy
info: Slideshow for scrcpy
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# take snapshot for each slide in the overview
overviewSnapshots: true
# What is SCRCPY
# Functionalities (popular parameters for the CLI tool)
# ADB (including ADB protocol and its security aspects)
# Server-Client Architecture
# Connection Modes
# USB Mode
# Wireless Mode
# OTG Mode
# Open-source
---

<link rel="icon" href="https://raw.githubusercontent.com/Genymobile/scrcpy/master/app/data/icon.svg" sizes="any" type="image/svg+xml">

# SCRCPY

<p id="subtitle"><strong>Scr</strong>een <strong>c</strong>o<strong>py</strong></p>

<!-- <div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div> -->

<div class="abs-br m-6 flex">
  <a href="https://github.com/LuMarans30/scrcpy-slideshow" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<style>
  #subtitle {
    font-size: 28px;
    font-weight: lighter;
  }
</style>

---

<Toc minDepth="1" maxDepth="2" />

---
layout: image-right
image: https://raw.githubusercontent.com/LuMarans30/scrcpy-slideshow/refs/heads/master/assets/scrcpy.webp
backgroundSize: contain
---

# Funzionalità

<strong>scrcpy</strong> è un tool CLI che consente di interagire con un dispositivo Android da un computer. <br /> <br />
Consente la condivisione di alcune periferiche del PC con il dispositivo Android e viceversa. <br /> <br />
I principali parametri del comando sono:
- `-K`  (`--keyboard`)
- `-M`  (`--mouse`)
- `-n`  (`--no-control`)
- `--otg`
- `-p`  (`--port`); Default range 27183:27199
- `-r`  (`--record`)
- `-W`  (`--stay-awake`)
- `-S`  (`--turn-screen-off`)

---
src: pages/ADB.md
---

---
src: pages/autoadb.md
---

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
