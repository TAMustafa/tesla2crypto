<script>
  export let coin;
  export let tesla;

  $: calculate = tesla.price / coin.price
</script>


  <h4>Tesla <span>{tesla.group} - {tesla.label}</span> costs: </h4>
  <img src="{coin.image}" alt="{coin.value}" id="coin_img">
  <h2> <strong id="coin_price">{calculate.toFixed(2)} {coin.symbol.toUpperCase()}</strong></h2>

<style>
  h4 {
    color: rgb(89, 94, 89);
  }

  #coin_img {
    max-width: 100px;
  }

  #coin_price {
    color: rgb(235, 166, 145);
  }

  span {
    color: rgb(235, 166, 145);
    font-weight: 700;
  }
</style>