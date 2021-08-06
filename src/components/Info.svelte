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
  const removeItem = (user) => {
    store.update((storeItem) => {
      return storeItem.filter((item) => item !== user);
    });
  };
</script>

<div class="wrapper">
  <div in:fade>
    <h1>Add User</h1>
    <InfoDetails {firstName} {lastName} on:user={addUser}>
      <span class="label" slot="firstName">First Name</span>
      <span class="label"slot="lastName">Last Name</span>
    </InfoDetails>
  </div>
  <ul>
    <h2>User List</h2>
    {#each $store as user, index}
      <li class="d-flex">
        <span class="list_number">{index + 1}</span>{user}
        <button class="delete" on:click={() => removeItem(user)}>X</button>
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
  .delete {
    color: red;
    margin: 0 0 0 15px;
    font-size: 1em;
    cursor: pointer;
    background: none;
    border: 2px solid #fff;
    border-radius: 5px;
    padding: 0 5px;
  }
  .label {
    color: #fff;
    margin: 15px 0 0;
    font-size: 1em;
  }
  h2{
    color: #fff;
  }
</style>
