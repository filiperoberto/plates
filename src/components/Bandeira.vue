<template>
   <!--https://blog.nandomoreira.dev/criando-a-bandeira-do-brasil-apenas-com-css-->
  <div class="brasil-flag">
    <div class="losangue"></div>
    <div class="circle"></div>
  </div>
</template>
<script>
export default {
}
</script>
<style scoped>
.brasil-flag {
    background-color: #16b83e;
    border: 1em solid white;
    width: 50em;
    height: 30em;
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
  left: 4em;
  right: 4em;
}

.brasil-flag .losangue:before {
  border-left: 21em solid transparent;
  border-right: 21em solid transparent;
  border-bottom: 13em solid #ffe11f;
  top: 2em;
}

.brasil-flag .losangue:after {
  border-left: 21em solid transparent;
  border-right: 21em solid transparent;
  border-top: 13em solid #ffe11f;
  bottom: 2em;
}
.brasil-flag .circle {
  overflow: hidden;
  z-index: 2;
  display: block;
  background-color: #1651b8;
  height: 16em;
  width: 16em;
  margin-top: -8em;
  margin-left: -8em;

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
  width: 18em;
  height: 8em;
  -ms-transform: rotate(14deg);
  -webkit-transform: rotate(14deg);
  transform: rotate(14deg);
}

.brasil-flag .circle:before {
  z-index: 3;
  content: '';
  margin-top: -4em;
  margin-left: -9em;
  background: #fff;
}

.brasil-flag .circle:after {
  z-index: 4;
  content: '';
  margin-top: -2em;
  margin-left: -10em;
  background-color: #1651b8;
}
</style>