<script>
  import { createEventDispatcher } from "svelte";
  import Select from "svelte-select";
  import TeslaStore from "../stores/TeslaStore.js";

  const dispatch = createEventDispatcher();

  let tesla;

  const groupBy = (item) => item.group;

  const handleSelect = (e) => {
    tesla = e.detail;
    dispatch("teslaData", tesla);
  };
</script>

<div id="tesla">
<Select
  items={$TeslaStore}
  {groupBy}
  on:select={handleSelect}
  placeholder="Select Tesla" />
</div>

<style>
  #tesla {
    margin-bottom: 40px;
    --groupTitleColor: rgb(235, 166, 145);
    --groupTitleFontSize: 14px;
    --borderRadius: 10px;
    --borderFocusColor: rgb(235, 166, 145);
    --itemColor: rgb(89, 94, 89);
    --itemIsActiveBG:  rgb(235, 166, 145);
    --itemHoverBG:  rgb(248, 229, 222);
  }
  
</style>
