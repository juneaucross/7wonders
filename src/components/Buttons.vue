<template>
  <div class="buttons-wrap">
    <button id="addPlayerBtn"  @click="addPlayer">add</button>
    <button id="getSumBtn" @click="getSum">scores</button>
  </div>
</template>

<script>

export default {
  name: 'Buttons',
  data: function () {
    return {
    //   playersArr: new Array(3).fill('huj').map(() => new PlayerClass()),
    //   sortedArr: null,
    }
  },
  methods: {
    addPlayer: function () {
      $emit('add-player', () => {
        this.playersArr.push(new Player());
      })
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
}
</script>

<style>

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


</style>
