<template>
  <div class='plate'>
    <span class='header'>BRASIL</span>
    <div class='plate-container'>
      <span>{{letters}}</span>
      <span>{{numbers}}</span>
    </div>
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
  .plate, .plate * {
    box-sizing: border-box;
  }

  .plate {
    width: 100%;
    border: 9px solid #101c36;
    border-radius: 5px;
    text-align:center;
  }

  .plate-container {
    padding:0.4em;
    letter-spacing: 10px;
    font-size: 50px;
  }

  .plate-container > span {
    display: inline-block;
  }

  .header {
    display: block;
    background: #1e4ab3;
    height: 30px;
    margin: 0;
    width:100%;
    display: flex;
    align-items: center;
    color: white;
    justify-content:center;
  }
</style>
