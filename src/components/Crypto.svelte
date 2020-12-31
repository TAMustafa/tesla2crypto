<script>
  import { onMount, createEventDispatcher } from "svelte";
  import Select from "svelte-select";

  const dispatch = createEventDispatcher();

  let data = [];
  let output = [];
  let coin;

  onMount(async () => {
    const res = await fetch(
      `https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1`
    );
    data = await res.json();

    // Map data
    output = data.map((x) => ({
      label: x.name,
      value: x.id,
      price: x.current_price,
      image: x.image,
      symbol: x.symbol,
    }));
  });

  const handleSelect = (e) => {
    coin = e.detail;
    dispatch("coinData", coin);
  };
</script>

<div id="crypto">
<Select items={output} on:select={handleSelect} placeholder="Select Cryptocurrency" />
</div>


<style>
  #crypto {
    margin-top: 40px;
    --borderRadius: 10px;
    --borderFocusColor: rgb(235, 166, 145);
    --itemColor: rgb(89, 94, 89);
    --itemIsActiveBG:  rgb(235, 166, 145);
    --itemHoverBG:  rgb(248, 229, 222);
  }
  
</style>