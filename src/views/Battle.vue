<template>
  <div class="map">
    battle
  </div>
</template>

<script>

export default {
  name: 'Battle',
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
  components: {
  },
}
</script>

<style scoped>
</style>
