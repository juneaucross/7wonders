<template>

  <tr class="table__player-row">
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

</template>

<script>
export default {
  name: 'Player',
  props: [
    'playersArr',
    'i',
  ],
}
</script>

<style>

.table__player {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 86px;
  height: 100%;
}

.table__player--name {
  width: 160px;
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

</style>
