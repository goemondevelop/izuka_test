<template>
  <div class="statusbar">
    <h3>ステータス</h3>
    <ul>
      <li>{{heroNAME}}</li>
      <li>HP：{{heroHP}}</li>
      <li>MP：{{heroMP}}</li>
      <li>状態：{{heroCondition}}</li>
    </ul>
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
      heroCondition: "ふつう",
    }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.statusbar {
  width: 50vw;
  height: 20vh;
  position: absolute;
  top: 0;
  background-color: #000;
  color: #fff;
  margin: 2%;
  border: solid 2px #fff;
  border-radius: 5px;
  z-index: 99;
}
h3 {

}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 10 10%;
  width: 90%;
  font-size: 22px;
  text-align: left; 
}
</style>
