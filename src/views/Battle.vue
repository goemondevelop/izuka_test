<template>
  <div class="battle">
    <div>
      <CharacterView></CharacterView>
      <StatusBar></StatusBar>
      <ActionAlert></ActionAlert>
      <BattleCommand></BattleCommand>
    </div>
    <div>

    </div>
  </div>
</template>

<script>
import CharacterView from '@/components/CharacterView.vue'
import BattleCommand from '@/components/BattleCommand.vue'
import StatusBar from '@/components/StatusBar.vue'
import ActionAlert from '@/components/ActionAlert.vue'


export default {
  name: 'Battle',
  components: {
    CharacterView,
    BattleCommand,
    StatusBar,
    ActionAlert,
  },
  data () {
    return {
      bar: 'foo',
    }
  },
  computed: {
    foo () {
      return 'bar'
    },
  },
  watch: {
    bar: {
      handler(val, old){
        console.log(val)
        console.log(old)
      }, deep: true
    }
  },
  methods: {
    doSomething () {
      console.log('do something')
    }
  },
  mounted () {

  }
}
</script>

<style scoped>
.battle{
  width: 100vw;
  height: 100vh;
  background-color: #aa9966;
}
</style>
