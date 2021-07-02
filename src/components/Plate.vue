<template>
  <div class='plate'>
    <span>{{letters}}</span>
    <span>{{numbers}}</span>
  </div>
</template>

<script>
export default {
  props: {
    plate: String
  },
  computed: {
    letters() {
      return this.plate.slice(0,3)
    },
    numbers() {
      return this.plate.slice(3,8)
    }
  }
}
</script>
<style scoped>
  .plate {
    box-sizing: border-box;
    width: 100%;
    border: 0.2em solid #101c36;
    border-radius: 0.2em;
    text-align:center;
    font-size: 4em;
    padding:0.4em;
    letter-spacing: 0.1em;
  }

  .plate > span {
    display: inline-block;
  }
</style>
