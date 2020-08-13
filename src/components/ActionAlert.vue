<template>
  <div class="actionalert">
    <!-- <message> -->
      <p>～～～～～～～～！！</p>
    <!-- </message> -->
  </div>
</template>

<script>
export default {
  name: 'StatusBar',
  data () {
    return {
      heroNAME: "ゴエモン",
      heroHP: 100,
      heroMP: 100,
      heroCondition: "",
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.actionalert {
  width: 80vw;
  height: 10vh;
  position: absolute;
  top: 70%;
  left: 50%;
  margin-right: -50%;
  transform: translate(-50%, -50%);
  background-color: #000;
  border: solid 2px #fff;
  border-radius: 5px;
  color:#fff;
  z-index: 99;
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
