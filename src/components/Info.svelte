<script>
  import { fade, scale } from "svelte/transition";
  import store from "./store";
  import InfoDetails from "./InfoDetails.svelte";
  let firstName = "";
  let lastName = "";

  const addUser = (e) => {
    let newStore = e.detail;
    store.update((user) => [...user, newStore]);
  };
</script>

<div class="wrapper">
  <div in:fade>
    <h1>Add User</h1>
    <InfoDetails {firstName} {lastName} on:user={addUser}>
      <h1 slot="firstName">User Full name is</h1>
      <h1 slot="lastName">User Full name is</h1>
    </InfoDetails>
  </div>
  <ul>
    {#each $store as user, index}
      <li class="d-flex" in:scale>
        <span class="list_number">{index + 1}</span>{user}
      </li>
    {/each}
  </ul>
</div>

<style>
  h1 {
    color: #fff;
    font-size: 2em;
    text-align: center;
    margin: 20px 0;
  }
  li {
    color: #fff;
    font-size: 1em;
    margin: 10px 0;
    font-weight: bold;
  }
</style>
