<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let tabNames;
  export let activeItem;
</script>

<div class="wrapper">
  <ul class="tabs d-flex">
    {#each tabNames as tabName}
      <li
        on:click={() => {
          dispatch("tabChange", tabName);
        }}
      >
        <span class:active={tabName === activeItem}> {tabName}</span>
      </li>
    {/each}
  </ul>
</div>

<style>
  .tabs {
    color: #fff;
    justify-content: space-around;
    margin: 0 0 50px;
  }
  .tabs li {
    font-size: 1.5em;
    font-weight: bold;
    margin: 0 50px 0 0;
    cursor: pointer;
    padding: 10px;
  }
  .active {
    border-bottom: 5px solid #fff;
    padding: 0 0 10px;
  }
</style>
