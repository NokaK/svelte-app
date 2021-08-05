<script>
  import Info from "./components/Info.svelte";
  import Data from "./components/Data.svelte";
  import Tabs from "./Tabs.svelte";

  let tabNames = ["Add user", "View data"];
  let activeItem = "Add user";

  const tabChange = (e) => {
    activeItem = e.detail;
  };
</script>

<div class="container">
  <Tabs {tabNames} {activeItem} on:tabChange={tabChange} />
  {#if activeItem === "Add user"}
    <Info />
  {:else if activeItem === "View data"}
    <Data />
  {/if}
</div>

<style>
  .container {
    min-height: 500px;
    max-width: 940px;
    padding: 50px;
    margin: 0 auto;
    background-color: #8ebec0;
    border-radius: 5px;
  }
</style>
