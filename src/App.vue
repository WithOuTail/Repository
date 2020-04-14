<template style="background: purple">

  <div id="app" class="fon">
    <a v-if=!vision id="web1">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <ul type="checkbox">
      <li v-for="(her, index) in dich" :key="her.message">
        <input type="button" value="Удалить" v-on:click="kefir(her.index)" class="del">
        <input type="checkbox" v-model="her.done" v-on:change="gazirovka(index)">
        <s v-if="her.done">{{index+1}} : {{her.message}}</s>
        <span v-else> {{her.message}}</span>
      </li>
      <input type="button" value="Удалить все"  v-on:click="moloko">
      <input type="button" value="Выделить все" @click="mineralka">
      <input type="button" value="другой список" @click="voda">
    </ul>
    <label>
    Введите запрос
    <input v-model="shaverma" type="text" placeholder="писать тут" size="100"  v-on:keyup.enter="kotletka" style="border-radius: 5px">
    <input type="button" size="50" value="тык" v-on:click="kotletka">
    </label>
    </a>
    <a v-if="vision" id="web2">
        <input type="date" style="margin-left: 10px" v-model="vremy">
<!--      <img alt="Vue logo" src="./assets/logo.png">-->
      <label>
        <input v-model="shaurma" type="text" placeholder="писать тут" size="100"  v-on:keyup.enter="plov" style="border-radius: 5px">
        <button v-on:click="plov" style="border-radius: 5px; size: 100px"> <i class="fas fa-arrow-alt-circle-right"></i>  </button>
<!--          <input type="button" size="50" value="тык" v-on:click="plov">-->
        <input type="button" value="другой список" @click="voda">
      </label>
      <ul type="radio">
        <li v-for="(her2, index) in dich2" :key="her2.message">
          <input type="checkbox" v-model="her2.done" v-on:change="gazirovka(index)" class="fas fa-check-circle" style="color: black">
          <s v-if="her2.done">{{index+1}} : {{her2.message}}</s>
          <span v-else> {{her2.message}}  </span>
            <button v-on:click="kefir2(her2.index)" class="del"> <i class="fas fa-trash-alt" style="color: white"></i> </button>
<!--            <input type="button" value="×" v-on:click="kefir2(her2.index)" class="del">-->
        </li>
        <input type="button" value="Удалить все"  v-on:click="moloko2" class="button">
        <input type="button" value="Выделить все" @click="mineralka2" class="button">
      </ul>
    </a>
  </div>
</template>



<script>
    var moment = require('moment');
    console.log(moment().format());
//
export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data(){
    return {
      isChanged:false,
        today: new Date(),
      shaverma:"",
      shaurma: "",
      name1: "рис",
      name2: "гречка",
      name3: "макарошки",
      vision: true,
      dich2: [

      ],
      dich: [
        // {name:"гыг1", id:1, message: "Фо"},
        // {name:"гыг2", id:2, message: "Бо"},
        // {done: false}
        ]
    }
  },
  methods: {
    vremy() {
        Date.prototype.getDate()
    },
    kotletka() {
      this.dich.push({id: Date.now(), message: this.shaverma, done: false}),
              this.shaverma = ""
    },
    plov() {
      this.dich2.push({id: Date.now(), message: this.shaurma, done: false}),
              this.shaurma = ""
    },
    moloko() {
      this.dich.splice({id: Date.now(), message: this.shaverma})
    },
    moloko2() {
      this.dich2.splice({id: Date.now(), message: this.shaurma})
    },
    kefir(index) {
      this.dich.splice(index, 1)
    },
    kefir2(index) {
      this.dich2.splice(index, 1)
    },
    mineralka() {
      for (var i = 0; i < this.dich.length; i++) {
        this.dich[i].done = !this.isChanged;
      }
      this.isChanged = !this.isChanged
    },
    mineralka2() {
      for (var i = 0; i < this.dich2.length; i++) {
        this.dich2[i].done = !this.isChanged;
      }
      this.isChanged = !this.isChanged
    },
    gazirovka(index) {
      if (!this.dich[index].done && this.isChanged) this.isChanged = !this.isChanged
    },
    voda() {
      this.vision = !this.vision
              },
    }
  }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Oswald:wght@300&display=swap');

    ul#app > li {
        color: #42b983;
    }
    .del {
        border-radius: 5px;
        background: #7e5b7e;
        outline: none;
        size: 0 ;
        color: white;
        text-align: right;
        float: right;
        border-bottom:  1px dotted black;
        border: 0;
    }
    .del:hover {
        opacity: .3; cursor: pointer;
    }
    .button {
        border-radius: 5px;
        background-color: #7e5b7e;
        size: 10px;
        color: rgb(180, 180, 180);
        text-align: right;
        float: right;
        border-bottom:  1px dotted black;
        float: left;
        outline: none;
        border: 0;
        font-family: 'Oswald', sans-serif;
        font-size: 110%;
    }

    .button:hover {
        cursor: pointer
    }

  .fon {
    border-radius: 10px;
      background-color: purple;
    box-shadow: 5px 5px 5px 3px rgba(67, 67, 67, 0.84);
    background: #7e5b7e;
    width: 700px; /* Ширина слоя */
    margin-left: auto;
    margin-right: auto;
    border: 1px solid black; /* Параметры границы */
    padding: 10px; /* Поля вокруг текста */
  }
  li{
    color: rgb(180, 180, 180);
    text-align: left;
    /*display: inline;*/
    margin-right: 10px;
      list-style-type: decimal;
      border-bottom:  2px solid black;
      margin-top: 7px;
      font-family: 'Oswald', sans-serif;
      font-size: 120%;
  }
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: black;
    margin-top: 60px;
    }

    body {
    background-color: blue;
        font-family: 'Oswald', sans-serif;
    }




</style>
