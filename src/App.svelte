<script lang="typescript">
  import Parent from "./Parent.svelte";
  import IntersectionObserver from "./Shared/IntersectionObserver.svelte";
  import { fade } from "svelte/transition";
  let visible = false;
</script>

<main>
  <!--  -->
  <div>Render Parent</div>
  <Parent />
  <hr />
  <!--  -->

  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>

  <!--  -->
  <div>Intersection Observer</div>
  <IntersectionObserver let:intersecting top={-400}>
    {#if intersecting}
      {console.log("visible", visible)}
      <div transition:fade>
        <div>start</div>
        <div class="box red">box</div>
        <div class="box red">box</div>
        <div class="box red">box</div>
        <div>end</div>
      </div>
    {/if}
  </IntersectionObserver>
  <!--  -->

  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>

  <!--  -->
  <div>Toggle</div>
  <button on:click={() => (visible = !visible)}>toggle</button>
  {#if visible}
    <div transition:fade>
      <div class="box red">box</div>
      <div class="box red">box</div>
      <div class="box red">box</div>
    </div>
  {/if}
  <!--  -->

  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
  <div class="box">box</div>
</main>

<style lang="scss">
  .hidden {
    visibility: hidden;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  .box {
    width: 300px;
    height: 300px;
    background: lightblue;
    opacity: 0.6;
    border: 1px solid blue;
  }

  .red {
    background: red;
    opacity: 0.2;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
