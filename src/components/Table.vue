<template>
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
        <Player :playersArr="playersArr" v-for="(player, i) in playersArr" :i="i" :key="i"/>
      </transition-group>

    </table>
    <!-- <button @click.prevent="submitForm">Submit scores</button> -->
  </form>
</template>

<script>

import { PlayerClass } from '../PlayerClass';

import Player from './Player.vue'

export default {
  name: 'Table',
  components: {
    Player,
  },
  data: function () {
    return {
      playersArr: new Array(3).fill('huj').map(() => new PlayerClass()),
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
}
</script>

<style>

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

.table__head--name {
  width: 160px;
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
