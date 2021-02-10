<script>
  import Child from "./Child.svelte";
</script>

<div class="wrapper">
  <div class="text">this is parent component</div>
  <Child>John</Child>
</div>

<style lang="scss">
  .wrapper {
    border: 1px solid black;
  }
</style>
