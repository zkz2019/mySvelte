<script>
  import { onMount } from "svelte";
  import { writable, get } from "svelte/store";
  import Left from "../components/Left";
  import Right from "../components/Right";
  let value;
  let dom;
  let copyData = [];
  let leftData = [1, 2, 3];
  let rightData = [];
  onMount(() => {
    dom = document.getElementsByTagName("input")[0];
  });
  function onAdd() {
    leftData.push(value);
    console.log("leftData", leftData, value);
    leftData = leftData;
  }
  function onInput(e) {
    console.log("onInput", e, e.target, e.value);
    value = dom.value;
  }
  function onClear() {
    rightData = [];
  }
</script>

<style>
  .topBox {
    width: 300px;
    height: 100px;
    border: 1px solid red;
  }
  .bottomBox {
    width: 300px;
    display: flex;
  }
  .leftBox {
    width: 150px;
    min-height: 300px;
    border: 1px solid yellow;
  }
  .rightBox {
    width: 150px;
    min-height: 300px;
    border: 1px solid green;
  }
</style>

<div class="topBox">
  <input type="text" on:input={onInput} />
  <button type="submit" on:click|preventDefault={onAdd}>添加</button>
  <button type="submit" on:click={onClear}>清空</button>
</div>
<div class="bottomBox">
  <Left />
  <Right />
</div>
