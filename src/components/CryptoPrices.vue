<template>
  <div>
    <h3>Cryptocurrency Prices</h3>
    <h5>(Real-time Updating)</h5>
   
    <div class="container" id="app">

       <div v-for="(result, index) in results">

          <div class="item crypto">
            <p> {{ index }} </p>
          </div>

          <div class="item result">
            <p>$ {{ result.USD }}</p>
          </div>
          <div class="item result">
            <p> &#8364 {{ result.EUR }}</p>
          </div>
          <div class="item result">
            <p>  £ {{ result.GBP }}</p>
          </div>
      </div> 
    </div>
    <div class="split-credit">
       <div><img class="img" src="../assets/crypto.svg" alt="art"></div>
        <p>&copy; Made with ❤ by <a href="https://github.com/highflyer910/crypto">Thea</a></p> 
    </div>
</div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import axios from 'axios';

const results = ref([]);

const upDate = () => {
  axios.get("https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH,PI,USDT,&tsyms=USD,EUR,GBP")
    .then(response => {
      results.value = response.data;
    });
};

let timer;

onMounted(() => {
  upDate();
  timer = setInterval(upDate, 1000);
});

onUnmounted(() => {
  clearInterval(timer);
});
</script>

