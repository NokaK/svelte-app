<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let firstName;
  export let lastName;

  
  $: fullName = firstName + " " + lastName;
  const handleClick = () => {
    dispatch("user", fullName);
    firstName = "";
    lastName = "";
  };
</script>

<div class="d-flex flex-column">
  <slot name="name" />
  <input type="text" bind:value={firstName} />
  <slot name="lastanme" />
  <input type="text" bind:value={lastName} />
  <button on:click={handleClick}>Add</button>
</div>

<style>
  input {
    border-radius: 15px;
    padding: 10px 15px;
    margin: 15px 0 0;
  }
  input:focus {
    outline: none;
  }
  button {
    background-color: #496768;
    border-radius: 15px;
    border: none;
    padding: 10px 15px;
    color: #fff;
    box-sizing: border-box;
    transition: all 0.3s linear 0.3s;
    cursor: pointer;
    margin: 15px 0;
    font-weight: bold;
  }
  button:hover {
    background-color: #273c3d;
  }
</style>
