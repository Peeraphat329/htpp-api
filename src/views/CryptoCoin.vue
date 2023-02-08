<template>
  <div>
    <h1>Crypto</h1>
    <button @click="lordCrypto()">LoadData</button>
    
    <table>
      <thead>
        <th>ลำดับที่</th>
        <th>symbol</th>
        <th>priceChange</th>
        <th>weightedAvgPrice</th>
        <th>prevClosePrice</th>
        <th>lastPrice</th>
      </thead>
      <tbody>
        <tr v-for="(value, index) in data" :key="index">
          <td>{{ index+1 }}</td>
          <td>{{ value.symbol }}</td>
          <td>{{ value.priceChange }}</td>
          <td>{{ value.weightedAvgPrice }}</td>
          <td>{{ value.prevClosePrice }}</td>
          <td>{{ value.lastPrice }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script setup>
import axios from "axios";
import { ref } from "vue";

const data = ref([]);
const url = ref("https://data.binance.com/api/v3/ticker/24hr");

function lordCrypto() {
  axios
    .get(url.value)
    .then((response) => {
      data.value = response.data;
    })
    .catch((err) => {
      console.log(err);
    });
}
</script>

<style scope>
  table,th,td,tr,thead{
    text-align: center;
    border: 1px solid rgb(235, 10, 36);
    text-decoration: none;
      color: white;
  }

h1{
  text-decoration: none;
    color: hsla(160, 100%, 37%, 1);
    transition: 0.4s;
}
</style>