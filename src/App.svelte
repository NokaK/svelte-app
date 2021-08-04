<script>
  import store from "./store";
  import Info from "./Info.svelte";
  let firstName = "";
  let lastName = "";

  const addUser = (e) => {
    let newStore = e.detail;
    store.update((user) => [...user, newStore]);
  };
</script>

<Info {firstName} {lastName} on:user={addUser}>
  <h1 slot="firstName">User Full name is</h1>
  <h1 slot="lastName">User Full name is</h1>
</Info>
<ul>
  {#each $store as user}
    <li>{user}</li>
  {/each}
</ul>

<style>
  ul {
   padding: 0 0 0 10px;
   list-style: none;
  }
  li {
    color: #ff3e00;
    font-size: 1em;
	margin: 10xp 0;
  }
</style>
