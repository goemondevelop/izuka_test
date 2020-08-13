<template>
  <div class="characterview">
    <img alt="Vue logo" src="../assets/maou.png">
  </div>
</template>

<script>
export default {
  name: 'CharacterView',
  data () {
    return {
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.characterview img {
  width:50vw;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-right: -50%;
  transform: translate(-50%, -50%);
  margin: 0 auto;
  z-index: 98;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
</style>
