<script>
  import { onMount } from "svelte";
  let mainData = [];
  let fetchUrl = "https://restcountries.eu/rest/v2/name/united";

  onMount(async () => {
    const response = await fetch(fetchUrl);
    const data = await response.json();
    mainData = data;
  });
</script>

<div class="d-flex data_wrapper">
  <ul>
    <h3>Name</h3>
    {#each mainData as name, index}
      <li class="d-flex">
        <span class="list_number">{index + 1}</span>
        <div>{name.name}</div>
      </li>
    {/each}
  </ul>
  <ul>
    <h3>Time Zone</h3>
    {#each mainData as time, index}
      <li class="d-flex">
        <span class="list_number">{index + 1}</span>
        <div>{time.timezones}</div>
      </li>
    {/each}
  </ul>
</div>

<style>
  .data_wrapper {
    justify-content: space-between;
  }
  li {
    color: #fff;
  }
  ul {
   margin: 0 20px 0 0;
  }
  h3 {
    font-size: 1.3em;
    color: #fff;
    margin: 0 0 15px;
  }
</style>
