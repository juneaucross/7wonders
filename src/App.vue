<template>
  <div id="app">
    <div class="container">

      <div class="logo">
        <h1 class="logo-heading"><span class="logo-number">7</span>wonders</h1>
      </div>
      <form class="main" action="" method="post">
        <table class="table">
          <th class="table__head-row">
            <td class="table__head table__head--name">player name</td>
            <td class="table__head table__head--red">war</td>
            <td class="table__head table__head--gold">gold</td>
            <td class="table__head table__head--wonder">wonder</td>
            <td class="table__head table__head--blue">culture</td>
            <td class="table__head table__head--orange">market</td>
            <td class="table__head table__head--violet">guild</td>
            <td class="table__head table__head--green">science</td>
            <td class="table__head table__head--leader">leader</td>
          </th>
          <transition-group name="list" appear>
            <tr class="table__player-row" v-for="(player, i) in playersArr" :key="i">
              <td class="table__player table__player--name">
                <input type="text" :name="'playerName-' + (i+1)" v-model="player.name" value="" tabindex="1" placeholder=" ">
              </td>
              <td class="table__player table__player--red">
                <input type="number" :name="'red-' + (i+1)" value="" v-model="player.red" tabindex="2" placeholder=" ">
              </td>
              <td class="table__player table__player--gold">
                <input type="number" :name="'gold-' + (i+1)" value="" v-model="player.gold" tabindex="3" placeholder=" ">
              </td>
              <td class="table__player table__player--wonder">
                <input type="number" :name="'wonder-' + (i+1)" value="" v-model="player.wonder" tabindex="4" placeholder=" ">
              </td>
              <td class="table__player table__player--blue">
                <input type="number" :name="'blue-' + (i+1)" value="" v-model="player.blue" tabindex="5" placeholder=" ">
              </td>
              <td class="table__player table__player--orange">
                <input type="number" :name="'orange-' + (i+1)" value="" v-model="player.orange" tabindex="6" placeholder=" ">
              </td>
              <td class="table__player table__player--violet">
                <input type="number" :name="'violet-' + (i+1)" value="" v-model="player.violet" tabindex="7" placeholder=" ">
              </td>
              <td class="table__player table__player--green">
                <input type="number" :name="'green-' + (i+1)" value="" v-model="player.green" tabindex="8" placeholder=" ">
              </td>
              <td class="table__player table__player--leader">
                <input type="number" :name="'leader-' + (i+1)" value="" v-model="player.leader" tabindex="9" placeholder=" ">
              </td>
            </tr>
          </transition-group>

        </table>
        <!-- <button @click.prevent="submitForm">Submit scores</button> -->
      </form>
      <div class="buttons-wrap">
        <button id="addPlayerBtn"  @click="addPlayer">add</button>
        <button id="getSumBtn" @click="getSum">scores</button>
      </div>

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

class Player{
  constructor() {
    this.id = null,
    this.name = '',
    this.red = null,
    this.gold = null,
    this.wonder = null,
    this.blue = null,
    this.orange = null,
    this.violet = null,
    this.green = null,
    this.leader = null,
    this.sum = null
  }
}

export default {
  name: 'App',
  data: function () {
    return {
      playersArr: new Array(3).fill('huj').map(() => new Player()),
      sortedArr: null,
    }
  },
  methods: {
    addPlayer: function () {
      this.playersArr.push(new Player());
    },
    submitForm: function () {
        for (var i = 0; i < this.playersArr.length; i++) {
          this.playersArr[i].id = i+1;
        }
      console.log(this.playersArr);
      return this.playersArr;
    },
    getSum: function () {
      for (var i = 0; i < this.playersArr.length; i++) {
        this.playersArr[i].sum =
        +this.playersArr[i].red + +this.playersArr[i].gold + +this.playersArr[i].wonder + +this.playersArr[i].blue + +this.playersArr[i].orange + +this.playersArr[i].violet + +this.playersArr[i].green + +this.playersArr[i].leader;
      }
      this.sortedArr = this.playersArr.map(item => ({...item}));
      this.sortedArr.sort((a, b) => {
        return b.sum - a.sum;
      })
      console.log(this.sortedArr)
    },
  },
  watch: {
    playersArr: function () {
      if (this.playersArr.length >= 8) {
        document.getElementById('addPlayerBtn').disabled = true;
      };
    }
  },
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

  .logo-heading {
    width: 100%;
    position: relative;
    text-transform: uppercase;
    font-size: 25px;
    line-height: 1.4;
  }

  .logo-number {
    display: block;
    position: absolute;
    top: -10px;
    left: -20px;
    font-size: 38px;
    line-height: 1.4;
    font-weight: 500;
  }

  .table {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  .table__head-row,
  .table__player-row {
    display: flex;
    flex-direction: row;
    width: 1190px;
    height: 64px;
    justify-content: space-around;
    -ms-align-items: center;
    align-items: center;
    text-align: center;
  }

  .table__player-row {
    border-bottom: 1px solid rgba(255, 255, 255, 0.3);
  }

  .table__player-row:nth-child(odd) {
    background-color: rgba(255, 255, 255, 0.1);
  }

  .table__head {
    width: 86px;
    font-size: 20px;
    line-height: 1.2;
  }

  .table__player {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 86px;
    height: 100%;
  }

  .table__player--name,
  .table__head--name {
    width: 160px;
  }

  .result__list {
    list-style: none;
  }

  li:first-of-type {
    color: red;
    font-weight: bold;
    font-size: 33px;
  }

  input {
    width: 80%;
    height: 24px;
    color: #fff;
    font-size: 20px;
    line-height: 1.2;
    background-color: var(--bgColor);
    border: none;
  }

  input:placeholder-shown {
    background-color: var(--inputPlaceholderColor);
  }

  input:focus {
    width: 100%;
    height: 100%;
    font-size: 35px;
    line-height: 1.2;
    background-color: var(--inputFocusColor);
    outline: none;
  }

  input::-webkit-inner-spin-button {
    display: none;
  }

  .table__player-row:nth-child(odd) > input {
    background-color: rgba(255, 255, 255, 0.1);
  }

  .buttons-wrap {
    display: flex;
    justify-content: flex-end;
    margin: 45px 0;
    width: 100%;
  }

  button {
    width: 140px;
    height: 43px;
    margin: 0 20px;
    border-radius: 50px;
    font-size: 20px;
    line-height: 1.2;
    color: #fff;
    background-color: transparent;
    border: 2px solid #fff;
    transition: all 0.2s linear;
    outline: none;
  }

  button:hover {
    color: var(--bgColor);
    background-color: #fff;
    /* border: 2px solid #fff; */
  }

  button:disabled {
    color: rgba(255, 255, 255, 0.3);
    border: 2px solid rgba(255, 255, 255, 0.3);
  }




  .slide-fade-enter-active {
    transition: all .3s ease;
  }
  .slide-fade-leave-active {
    transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .slide-fade-enter, .slide-fade-leave-to
  /* .slide-fade-leave-active до версии 2.1.8 */ {
    transform: translateX(10px);
    opacity: 0;
  }



  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to /* .list-leave-active до версии 2.1.8 */ {
    opacity: 0;
    transform: translateY(30px);
  }

</style>
