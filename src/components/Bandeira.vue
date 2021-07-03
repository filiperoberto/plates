<template>
   <!--https://blog.nandomoreira.dev/criando-a-bandeira-do-brasil-apenas-com-css-->
  <div class="brasil-flag" :style="{width: `${width}px`, height: `${height}px`, top:`${top}px`, right: `${top}px`}">
    <div class="losangue"></div>
    <div class="circle"></div>
  </div>
</template>
<script>
export default {
  props: {
    width: {
      type: Number,
      default: 50
    }
  },
  computed: {
    height() {
      return this.width * 3/5
    },
    top() {
      return this.width / 10
    }
  }
}
</script>
<style scoped>
.brasil-flag {
    position: absolute;
    background-color: #16b83e;
    border: 1px solid white;
  }

  .brasil-flag .losangue:before,
  .brasil-flag .losangue:after {
    position: absolute;
  }

  .brasil-flag .losangue {
    width: 100%;
    height: 100%;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
  }

.brasil-flag .losangue:before,
.brasil-flag .losangue:after {
  content: '';
  width: 0;
  height: 0;
  left: 4px;
  right: 4px;
}

.brasil-flag .losangue:before {
  border-left: 21px solid transparent;
  border-right: 21px solid transparent;
  border-bottom: 13px solid #ffe11f;
  top: 2px;
}

.brasil-flag .losangue:after {
  border-left: 21px solid transparent;
  border-right: 21px solid transparent;
  border-top: 13px solid #ffe11f;
  bottom: 2px;
}
.brasil-flag .circle {
  overflow: hidden;
  z-index: 2;
  display: block;
  background-color: #1651b8;
  height: 16px;
  width: 16px;
  margin-top: -8px;
  margin-left: -8px;

  top: 50%;
  left: 50%;
  position: absolute;
  border-radius: 50%;
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
}
.brasil-flag .circle,
.brasil-flag .circle:before,
.brasil-flag .circle:after {
  top: 50%;
  left: 50%;
  position: absolute;
  border-radius: 50%;
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
}
.brasil-flag .circle:before,
.brasil-flag .circle:after {
  width: 18px;
  height: 8px;
  -ms-transform: rotate(14deg);
  -webkit-transform: rotate(14deg);
  transform: rotate(14deg);
}

.brasil-flag .circle:before {
  z-index: 3;
  content: '';
  margin-top: -4px;
  margin-left: -9px;
  background: #fff;
}

.brasil-flag .circle:after {
  z-index: 4;
  content: '';
  margin-top: -2px;
  margin-left: -10px;
  background-color: #1651b8;
}
</style>