<template>
  <div id="app">
    <div class="container">

      <Header/>
      <Table/>
      <Buttons/>

      <div class="result__wrap" v-if="sortedArr">
        <ul class="result__list">
          <li class="result__list-item" v-for="player in sortedArr">
            {{ player.name | capitalize }} - {{ player.sum }} !
          </li>
        </ul>
      </div>


    </div>


  </div>
</template>

<script>



import Header from './components/Header.vue';
import Table from './components/Table.vue';
import Buttons from './components/Buttons.vue';

export default {
  name: 'App',
  components: {
    Header,
    Table,
    Buttons,
  },
  data: function () {
    return {
      // playersArr: new Array(3).fill('huj').map(() => new Player()),
      sortedArr: null,
    }
  },
  // methods: {
  //   addPlayer: function () {
  //     this.playersArr.push(new Player());
  //   },
  //   submitForm: function () {
  //       for (var i = 0; i < this.playersArr.length; i++) {
  //         this.playersArr[i].id = i+1;
  //       }
  //     console.log(this.playersArr);
  //     return this.playersArr;
  //   },
  //   getSum: function () {
  //     for (var i = 0; i < this.playersArr.length; i++) {
  //       this.playersArr[i].sum =
  //       +this.playersArr[i].red + +this.playersArr[i].gold + +this.playersArr[i].wonder + +this.playersArr[i].blue + +this.playersArr[i].orange + +this.playersArr[i].violet + +this.playersArr[i].green + +this.playersArr[i].leader;
  //     }
  //     this.sortedArr = this.playersArr.map(item => ({...item}));
  //     this.sortedArr.sort((a, b) => {
  //       return b.sum - a.sum;
  //     })
  //     console.log(this.sortedArr)
  //   },
  // },
  // watch: {
  //   playersArr: function () {
  //     if (this.playersArr.length >= 8) {
  //       document.getElementById('addPlayerBtn').disabled = true;
  //     };
  //   }
  // },
  filters: {
    capitalize: function (value) {
      if (!value) return '';
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    }
  }
}
</script>

<style>

  #app {
    /* css variables */
    --bgColor: #2E364A;
    --inputFocusColor: #232834;
    --inputPlaceholderColor: #030814;

    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-weight: 300;
    text-align: center;
    color: white;
    width: 100%;
    background: var(--bgColor);
    /* margin-top: 60px; */
  }

  .container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    width: 1280px;
    margin: 0 auto;
  }





  .result__list {
    list-style: none;
  }

  li:first-of-type {
    color: red;
    font-weight: bold;
    font-size: 33px;
  }







</style>
