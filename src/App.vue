<script setup>
import CryptoPrices from './components/CryptoPrices.vue'
</script>

<template>
  <CryptoPrices/>
  
</template>

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
  display: flex;
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

  .crypto{
    padding: 0 120px;
    max-width: 120px;
    font-size: 18px;
  }
}

html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}


</style>