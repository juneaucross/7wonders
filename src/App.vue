<template>
  <div id="app">
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
        <tr class="table__player-row" v-for="(player, i) in playersArr">
          <td class="table__player table__player--name">
            <input type="text" :name="'playerName-' + (i+1)" v-model="player.name" value="" tabindex="1">
          </td>
          <td class="table__player table__player--red">
            <input type="number" :name="'red-' + (i+1)" value="" v-model="player.red" tabindex="2">
          </td>
          <td class="table__player table__player--gold">
            <input type="number" :name="'gold-' + (i+1)" value="" v-model="player.gold" tabindex="3">
          </td>
          <td class="table__player table__player--wonder">
            <input type="number" :name="'wonder-' + (i+1)" value="" v-model="player.wonder" tabindex="4">
          </td>
          <td class="table__player table__player--blue">
            <input type="number" :name="'blue-' + (i+1)" value="" v-model="player.blue" tabindex="5">
          </td>
          <td class="table__player table__player--orange">
            <input type="number" :name="'orange-' + (i+1)" value="" v-model="player.orange" tabindex="6">
          </td>
          <td class="table__player table__player--violet">
            <input type="number" :name="'violet-' + (i+1)" value="" v-model="player.violet" tabindex="7">
          </td>
          <td class="table__player table__player--green">
            <input type="number" :name="'green-' + (i+1)" value="" v-model="player.green" tabindex="8">
          </td>
          <td class="table__player table__player--leader">
            <input type="number" :name="'leader-' + (i+1)" value="" v-model="player.leader" tabindex="9">
          </td>
        </tr>
      </table>
      <button @click.prevent="submitForm">Submit scores</button>
    </form>
    <button id="addPlayerBtn"  @click="addPlayer">add player</button>
    <button @click="getSum">calculate scores</button>

    <div class="result__wrap" v-if="playersArr[0].sum">
      <ul class="result__list">
        <li clas="result__list-item" v-for="player in playersArr">
          {{ player.name | capitalize }} - {{ player.sum }} !
        </li>
      </ul>
    </div>


  </div>
</template>

<script>

export default {
  name: 'App',
  data: function () {
    return {
      playersArr: [
        {
          name: '',
          red: null,
          gold: null,
          wonder: null,
          blue: null,
          orange: null,
          violet: null,
          green: null,
          leader: null,
          sum: null
        },
        {
          name: '',
          red: null,
          gold: null,
          wonder: null,
          blue: null,
          orange: null,
          violet: null,
          green: null,
          leader: null,
          sum: null
        },
        {
          name: '',
          red: null,
          gold: null,
          wonder: null,
          blue: null,
          orange: null,
          violet: null,
          green: null,
          leader: null,
          sum: null
        }
      ]
    }
  },
  methods: {
    addPlayer: function () {
      this.playersArr.push(
        {
          name: '',
          red: null,
          gold: null,
          wonder: null,
          blue: null,
          orange: null,
          violet: null,
          green: null,
          leader: null,
          sum: null
        }
      );
    },
    submitForm: function () {
      console.log(this.playersArr);
    },
    getSum: function () {
      for (var i = 0; i < this.playersArr.length; i++) {
        this.playersArr[i].sum =
        +this.playersArr[i].red + +this.playersArr[i].gold + +this.playersArr[i].wonder + +this.playersArr[i].blue + +this.playersArr[i].orange + +this.playersArr[i].violet + +this.playersArr[i].green + +this.playersArr[i].leader;
      }
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
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: white;
    width: 100%;
    background: black;
    margin-top: 60px;
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
    justify-content: space-between;
    text-align: center;
  }

  .table__head {
    width: 80px;
  }

  .table__player {
    width: 80px;
  }

  .table__player--name,
  .table__head--name {
    width: 160px;
  }

  .result__list {
    list-style: none;
  }

  input {
    width: 50%;
  }

  input::-webkit-inner-spin-button {
  display: none;
}

</style>
