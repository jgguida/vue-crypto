<template>
  <div class="hello">
    <div id="crypto-container" v-for="(value, key) in cryptos">
      <span class="left">{{key}}</span>
      <span class="right">R$ {{value.BRL}}</span>


    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data: () => ({
    cryptos: [],
    errors: []
   
  }),

  created () {
    axios.get('https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH,XRP,LINK,LTC,BCH,TRX&tsyms=BRL')
    .then(response => {
      this.cryptos = response.data
      console.log(response)
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
};


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  body {
    background:linear-gradient(45deg, hsla(232, 91%, 49%, 1) 0%, hsla(232, 91%, 49%, 0) 70%), linear-gradient(135deg, hsla(185, 98%, 42%, 1) 10%, hsla(185, 98%, 42%, 0) 80%), linear-gradient(225deg, hsla(310, 98%, 47%, 1) 10%, hsla(310, 98%, 47%, 0) 80%), linear-gradient(315deg, hsla(67, 94%, 43%, 1) 100%, hsla(67, 94%, 43%, 0) 70%);
}
  div#crypto-container {
    background:white;
    width: 70%;
    margin: 0 auto 4px auto;
    padding: 1em;
    box-shadow: 1px 1px 0 lightgrey;
  }
  span.left {
    font-weight: bold;
  }
  span.right {
    float:right;
  }
</style>