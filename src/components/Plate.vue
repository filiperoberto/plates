<template>
  <div class='plate'>
    {{plate}}
  </div>
</template>

<script>
export default {
  props: {
    plate: String
  }
}
</script>
<style scoped>
  .plate {
    width: 100%;
  }
</style>
