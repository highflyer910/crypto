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
       <div><img class="img" src="../assets/crypto.svg"></div>

        <p>&copy; Made with ❤ by <a href="https://github.com/highflyer910/crypto">Thea</a></p> 
  </div>
</div>
</template>

<script>
import axios from 'axios';  
export default {
    name: 'app',
    data:() => ({
     results: []
        }),

     mounted() {
      this.upDate();
      this.timer = setInterval(this.upDate, 1000)
      }, 
      methods:{
      upDate: function() {
            axios.get("https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH,LTC&tsyms=USD,EUR,GBP").then(response => {
              this.results = response.data
            })
       }, 
      cancelAutoUpdate: function(){
            clearInterval(this.timer)
       },

       beforeDestroy() {
         clearInterval(this.timer)
       }
    }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Quicksand:300,400,500,700");
  :root {
  --blue: #2E2A42;
  --green: #234B59;
  --yellow: #FEEE86;

}

html {
  box-sizing: border-box;
  font-family: 'Quicksand', sans-serif;
}

*,
*:before,
*:after {
  box-sizing: inherit;
}

body {
  background-color: var(--blue);
}


.item {
  display: grid;
  justify-content: center;
  align-items: center;
  border-top: 1px dotted var(--blue);
  border-radius: 5px;
  font-size: 22px;
  height: 60px;
  background-color: var(--green);
  color: var(--yellow);
  box-shadow: 0 1.5px 1.5px 0 var(--yellow);
}

.container{
  display: grid;
  grid-gap: 20px;
  grid-template-columns: repeat(3, 200px);
  justify-content: center;
  align-items: center;
  padding: 40px;
}

.crypto{
  font-weight: bold;
  font-size: 25px;
}

.result p{
  opacity: .9;
}

h3{
  text-align: center;
  padding-top: 50px;
  color: var(--yellow);
  font-size: 42px;
}

h5{
  text-align: center;
  padding-top: 20px;
  color: var(--yellow);
  opacity: .8;
}

img{
  width: 150px;
  align-self: center;
}

.split-credit {
    display: grid;
    padding: 20px;
    justify-content: center;
  }

  .split-credit p {
    font-size: 12px;
    line-height:15px; 
    color: var(--yellow);
  }

  .split-credit p a {
      font-weight: bold;
      color: var(--yellow); 
 }

@media screen and (max-width: 600px) {
  .container{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
  }

  .item{
    padding: 0 60px;
    width: 100%;
  }
}

</style>
