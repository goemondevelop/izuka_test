<template>
  <div class="map text-center mx-auto" @keydown.up="doSomething">
    <canvas class="border" ref="map" id="canvas" width="500" height="500" />
  </div>
</template>

<script>

export default {
  name: 'Map',
  data () {
    return {
      bar: 'foo',
      //20px*20pxのマップをひとつの単位として25*25のマップを構成する
      map: [
        //0x
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        //1x
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,1,1,1, 1,1,1,1,1,1,1,1,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,1,1,1, 1,1,1,1,1,1,1,1,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        //2x
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
        [0,0,0,0,0,0,0,0,0,0, 1,1,1,1,1,0,0,0,0,0, 0,0,0,0,0,],//25
      ],
      position: {x:12, y:25 - 1},
    }
  },
  mounted () {
    this.draw()
    document.addEventListener('keydown', (event) => {
      console.log(event)
      var position = this.position
      if(event.code=="ArrowUp"){
        position = {x:this.position.x, y:this.position.y-1}
      }else if(event.code=="ArrowDown"){
        position = {x:this.position.x, y:this.position.y+1}
      }if(event.code=="ArrowLeft"){
        position = {x:this.position.x-1, y:this.position.y}
      }else if(event.code=="ArrowRight"){
        position = {x:this.position.x+1, y:this.position.y}
      }
      if(position.y < 0){
        if (window.confirm("いくぞ、準備はいいか?")) {
          this.$router.push({path:"/battle"})
        }
      }else if(0 <= position.x < 25 && 0 <= position.y < 25){
        if(this.map[position.y][position.x] == 1){
          this.position = position
        }
      }
    })
  },
  computed: {
    foo () {
      return 'bar'
    },
  },
  watch: {
    position: {
      handler(val, old){
        console.log(val)
        console.log(old)
        this.draw()
      }, deep: true
    }
  },
  methods: {
    draw () {
      var canvas = document.getElementById('canvas')
      // //コンテクスト
      var ctx = canvas.getContext('2d')

      /* マップの配置 */
      //通路のつち通れない箇所をdraw
      let invalid = "rgb(100, 100, 100)"
      let valid = "rgb(255, 255, 255)"
      ctx.fillStyle = invalid
      for(var y=0;y<25;y++){
        for(var x=0;x<25;x++){
          if(this.map[y][x] == 0){
            ctx.fillStyle = invalid
            ctx.fillRect (x * 20, y * 20, 20, 20)
          }else{
            ctx.fillStyle = valid
            ctx.fillRect (x * 20, y * 20, 20, 20)
          }
        }
      }

      /* キャラの配置 */
      let character = "rgb(0, 0, 255)"
      ctx.fillStyle = character
      ctx.fillRect (this.position.x * 20, this.position.y * 20, 20, 20)
    },
    doSomething () {
      alert('up')
    }
  },
  components: {
  },
}
</script>

<style scoped>
.map{
}
canvas{
}
</style>
