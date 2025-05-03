```HTML
<div class="particle-background" data-color-1="#00d76c" data-color-2="#a8e2ff" data-color-3="#0f1627"
      data-count="60" data-speed="1">
</div>
``` 


```CSS
.particle-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  pointer-events: none;
  overflow: hidden;
}

.particle-background canvas {
  display: block;
  width: 100%;
  height: 100%;
}


/*  */
.other-website-section-which-will-contain-the-particles {
  z-index: 1;
}
```
