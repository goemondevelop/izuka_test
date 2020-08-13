<template>
  <div class="battlecommand">
    <ul class="b_c_1st">
      <li><button type="button" value="Attack" @click="onClickHeroAction('Attack')">▶たたかう</button></li>
      <li><button type="button" value="Magic" @click="onClickHeroAction('Magic')">▶まほう</button></li>
      <li><button type="button" value="Item" @click="onClickHeroAction('Item')">▶アイテム</button></li>
      <li><button type="button" value="XX" @click="onClickHeroAction('XX')">▶わるぐち</button></li>
    </ul>
    <ul class="b_c_2nd attack" v-show="ClickedAttack">
      <li><button type="button" @click="heroAttack" value="punch">▶なぐる</button></li>
      <li><button type="button" @click="heroAttack">▶ける</button></li>
      <li><button type="button" @click="heroAttack">▶ずつき</button></li>
      <li><button type="button" @click="heroAttack">▶かみつく</button></li>
    </ul>
    <ul class="b_c_2nd magic" v-show="ClickedMagic">
      <li><button type="button" @click="heroMagicAtk">▶ザラキ</button></li>
      <li><button type="button" @click="heroMagicAtk">▶イオナズン</button></li>
      <li><button type="button" @click="heroMagicStn">▶ラリホー</button></li>
      <li><button type="button" @click="heroMagicHeal">▶ベホイミ</button></li>
    </ul>
    <ul class="b_c_2nd item" v-show="ClickedItem">
      <li><button type="button" @click="ItemYakusou">▶やくそう</button></li>
      <li><button type="button" @click="ItemDokukeshi">▶どくけしそう</button></li>
      <li><button type="button" @click="ItemSekaiju">▶せかいじゅのは</button></li>
      <li><button type="button" @click="ItemYubiwa">▶いのりのゆびわ</button></li>
    </ul>
    <div class="xx" v-show="ClickedXX">
      <input type="text" maxlength="1000" placeholder="入力してください" v-model="Abuse">
      <button type="button" @click="SayYes">あびせる</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'battlecommand',
  data () {
    return {
      ClickedAttack: false,
      ClickedItem: false,
      ClickedMagic: false,
      ClickedXX: false,
      heroAction: "",
      Abuse: "",
    }
  },
  methods: {
    onClickHeroAction(arg){
      this.heroAction = arg
    },
    heroAttack () {
      console.log("こうげき")
    },
    heroMagicAtk () {
      console.log("まほうのこうげき")
    },
    heroMagicStn () {
      console.log("スタンまほう")
    },
    heroMagicHeal () {
      console.log("かいふくまほう")
    },
    ItemYakusou () {
      console.log("かいふくアイテム")
    },
    ItemDokukeshi () {
      console.log("どくけしアイテム")
    },
    ItemSekaiju () {
      console.log("ぶっ生き返す")
    },
    ItemYubiwa () {
      console.log("MPかいふくアイテム")
    },
    SayYes () {
      console.log(this.Abuse.length)
    },
  },
  watch: {
    heroAction () {
      if ( this.heroAction == "Attack" ) {
        this.ClickedAttack = true
      }
      else if ( this.heroAction == "Magic" ) {
        this.ClickedMagic = true
      }
      else if ( this.heroAction == "Item" ) {
        this.ClickedItem = true
      }
      else {
        this.ClickedXX = true
      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.battlecommand ul {
  width: 30vw;
  height: 20vh;
  background-color: #000;
  color: #fff;
  margin: 2%;
  border: solid 2px #fff;
  border-radius: 5px;
}
.b_c_1st {
  position: absolute;
  bottom: 0;
  z-index: 99;
}
.b_c_2nd {
  position: absolute;
  bottom: 0;
  left: 28vw;
  z-index: 100;
}
button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  outline: none;
  padding: 0;
  appearance: none;
  color: #fff;
  width: 28vw;
  text-align: left;
  font-size: 20px;
}
h3 {
  color: #fff;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  line-height: 5vh;
  margin: auto;
}
.xx {
  position: absolute;
  top: 40%;
  left: 50%;
  margin-right: -50%;
  transform: translate(-50%, -50%);
  z-index: 100;
  height: 12vh;
  width: 50vw;
  background-color: #000;
  color: #fff;
  margin: 2%;
  border: solid 2px #fff;
  border-radius: 5px;
}
.xx input {
  height: 5vh;
  width: 40vw;
  margin: 1vh auto;
}
.xx button {
  width: 30vw;
  height: 3vh;
  background-color: #aaa;
  text-align: center;
  color: #000;
}
</style>
