---
title: vue-Stretch-div
tags:
---

```vue
<template>
  <div class="stretch-box">
    <div class="table-box" :style="{height: `${tableHeight}px`}">

    </div>
    <div class="move-button" @mousedown="moveFooter" :style="moveButtonStyle">
      <span></span>
      <span></span>
    </div>
    <div class="footer-box" :style="{height: `${footerHeight}px`}">

    </div>
  </div>
</template>

<script>
export default {
  name: "stretch",
  data() {
    return {
      tableHeight: 150,
      footerHeight: 150,
      moveButtonStyle: '',
    }
  },
  methods: {
    moveFooter(e) {
      e.stopPropagation()
      // let startX = e.clientX;
      let startY = e.clientY;
      let self = this;
      let distY;
      document.onmousemove = function (e) {
        e.preventDefault();
        // let distX = Math.abs(e.clientX - startX);
        distY = startY - e.clientY;
        let moveBtnY = e.clientY;
        console.log(e.clientY)
        self.moveButtonStyle = {
          position: 'absolute',
          top: `${moveBtnY}px`
        }
      }

      document.onmouseup = function (e) {
        e.stopPropagation()
        self.footerHeight = self.footerHeight + distY;
        self.tableHeight  = self.tableHeight - distY;
        self.moveButtonStyle = ''
        document.onmousemove = null;
        document.onmouseup = null;
      }
    }
  },
}
</script>

<style  scoped>
.table-box {
  border: 1px solid darkgray;
  margin-bottom: 20px;
  background: darkgray;
}
.move-button{
  border: 2px solid red;
  height: 10px;
  cursor:ns-resize;
  width: 100%;
  margin-bottom: 20px;
  border-radius: 2px;
}
.footer-box {
  border: 1px solid gray;
  background: gray;
}
</style>
```