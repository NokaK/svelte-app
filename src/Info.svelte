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

<div>
  <slot name="name" />
  <input type="text" bind:value={firstName} />
  <slot name="lastanme" />
  <input type="text" bind:value={lastName} />
  <button on:click={handleClick}>add user</button>
</div>

<style>
  button {
    background-color: #ff3e00;
    border-radius: 15px;
    border: none;
    padding: 10px 15px;
    color: #fff;
    box-sizing: border-box;
    transition: all 0.3s linear 0.3s;
    cursor: pointer;
  }
  button:hover {
    background-color: #531500;
  }
  input {
    border-radius: 15px;
    padding: 10px 15px;
  }
  input:focus {
    outline: none;
  }
</style>
