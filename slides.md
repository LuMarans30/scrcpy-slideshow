---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://raw.githubusercontent.com/LuMarans30/scrcpy-slideshow/refs/heads/master/assets/cover.webp
# some information about your slides (markdown enabled)
title: SCRCPY
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
# hide in the table of contents
hideInToc: true
---

<link rel="icon" href="https://raw.githubusercontent.com/Genymobile/scrcpy/master/app/data/icon.svg" sizes="any" type="image/svg+xml">

# SCRCPY

<p id="subtitle"><strong>Scr</strong>een <strong>c</strong>o<strong>py</strong></p>

<div class="abs-br m-6 flex">
  <a href="https://github.com/LuMarans30/scrcpy-slideshow" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<style>
  #subtitle {
    font-size: 28px;
    font-weight: light;
  }
</style>

---
hideInToc: true
---

# Indice

<Toc minDepth="1" maxDepth="2" />

---
src: pages/funzionalita.md
---

---
src: pages/ADB.md
---

---
src: pages/autoadb.md
---

---
src: pages/demo.md
---